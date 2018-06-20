# Welcome to Xiaoqing DAI's blog

Xiaoqing's research interests include: travel demand prediction, intelligent transportation systems, big data, behavior modeling and transportation planning.

This blog presents some of my research. 

You can find the pdf version of my resume here. [XiaoqingDAI's resume](XiaoqingDAI_resume_201806acdemic_final.pdf)

### Travel demand prediction under non-recurrent situations 


The goal is to predict travel demand under non-recurrent situations based on normal historical data. The model has been developed for metro systems. 


![](heatmap130913.gif)
Figure. A heatmap of out-station volume of Shanghai metro on a heavy rainy day with disruption in the afternoon.

---

### Intelligent Transportation System Planning


Intelligent transportation system planning based on consideration of smart connected vehicles. The V2I roadside environment design and the coordinated traffic signal control/traffic guidance system design are included.

![](anting_roadmap.png)
Figure. A roadmap of the planning area.

---

### OD is intereseting, right?

<style  type="text/css">
#tooltip { color: white; opacity: .9; background: #333; padding: 5px; border: 1px solid lightgrey; border-radius: 5px; position: absolute; z-index: 10; visibility: hidden; white-space: nowrap; pointer-events: none; } #circle circle { fill: none; pointer-events: all; } path.group { fill-opacity: .8; } path.chord { fill-opacity: .8; stroke: #000; stroke-width: .25px; } #circle:hover path.fade { display: none; } 
</style>
<div id="tooltip"></div><script src="d3.js"></script><script src="underscore.js"></script><script src="mapper.js"></script>
<script type="text/javascript">
d3.csv('trade11.csv', function (error, data) { var mpr = chordMpr(data); mpr .addValuesToMap('importer1') .addValuesToMap('importer2') .setFilter(function (row, a, b) { return (row.importer1 === a.name && row.importer2 === b.name) || (row.importer1 === b.name && row.importer2 === a.name) }) .setAccessor(function (recs, a, b) { if (!recs\[0\]) return 0; return recs\[0\].importer1 === a.name ? +recs\[0\].flow1 : +recs\[0\].flow2; }); drawChords(mpr.getMatrix(), mpr.getMap()); }); function drawChords (matrix, mmap) { var w = 980, h = 800, r1 = h / 2, r0 = r1 - 110; var fill = d3.scale.ordinal() .range(\['#c7b570','#c6cdc7','#335c64','#768935','#507282','#5c4a56','#aa7455','#574109','#837722','#73342d','#0a5564','#9c8f57','#7895a4','#4a5456','#b0a690','#0a3542',\]); var chord = d3.layout.chord() .padding(.02) .sortSubgroups(d3.descending) .sortChords(d3.descending); var arc = d3.svg.arc() .innerRadius(r0) .outerRadius(r0 + 20); var svg = d3.select("body").append("svg:svg") .attr("width", w) .attr("height", h) .append("svg:g") .attr("id", "circle") .attr("transform", "translate(" + w / 2 + "," + h / 2 + ")"); svg.append("circle") .attr("r", r0 + 20); var rdr = chordRdr(matrix, mmap); chord.matrix(matrix); var g = svg.selectAll("g.group") .data(chord.groups()) .enter().append("svg:g") .attr("class", "group") .on("mouseover", mouseover) .on("mouseout", function (d) { d3.select("#tooltip").style("visibility", "hidden") }); g.append("svg:path") .style("stroke", "black") .style("fill", function(d) { return fill(rdr(d).gname); }) .attr("d", arc); g.append("svg:text") .each(function(d) { d.angle = (d.startAngle + d.endAngle) / 2; }) .attr("dy", ".35em") .style("font-family", "helvetica, arial, sans-serif") .style("font-size", "9px") .attr("text-anchor", function(d) { return d.angle > Math.PI ? "end" : null; }) .attr("transform", function(d) { return "rotate(" + (d.angle * 180 / Math.PI - 90) + ")" + "translate(" + (r0 + 26) + ")" + (d.angle > Math.PI ? "rotate(180)" : ""); }) .text(function(d) { return rdr(d).gname; }); var chordPaths = svg.selectAll("path.chord") .data(chord.chords()) .enter().append("svg:path") .attr("class", "chord") .style("stroke", function(d) { return d3.rgb(fill(rdr(d).sname)).darker(); }) .style("fill", function(d) { return fill(rdr(d).sname); }) .attr("d", d3.svg.chord().radius(r0)) .on("mouseover", function (d) { d3.select("#tooltip") .style("visibility", "visible") .html(chordTip(rdr(d))) .style("top", function () { return (d3.event.pageY - 170)+"px"}) .style("left", function () { return (d3.event.pageX - 100)+"px";}) }) .on("mouseout", function (d) { d3.select("#tooltip").style("visibility", "hidden") }); function chordTip (d) { var p = d3.format(".1%"), q = d3.format(",.0f") return "Chord Info:<br/>" + d.sname + " go to " + d.tname + ": " + q(d.svalue) + " pax<br/>" + p(d.svalue/d.stotal) + " of " + d.sname + "'s Total (" + q(d.stotal) + " pax)<br/>" + p(d.svalue/d.mtotal) + " of Matrix Total (" + q(d.mtotal) + " pax)<br/>" + "<br/>" + d.tname + " go to " + d.sname + ": " + q(d.tvalue) + " pax<br/>" + p(d.tvalue/d.ttotal) + " of " + d.tname + "'s Total (" + q(d.ttotal) + " persions)<br/>" + p(d.tvalue/d.mtotal) + " of Matrix Total (" + q(d.mtotal) + " pax)"; } function groupTip (d) { var p = d3.format(".1%"), q = d3.format(",.0f") return "Group Info:<br/>" + d.gname + " : " + q(d.gvalue) + "M<br/>" + p(d.gvalue/d.mtotal) + " of Matrix Total (" + q(d.mtotal) + "M)" } function mouseover(d, i) { d3.select("#tooltip") .style("visibility", "visible") .html(groupTip(rdr(d))) .style("top", function () { return (d3.event.pageY - 80)+"px"}) .style("left", function () { return (d3.event.pageX - 130)+"px";}) chordPaths.classed("fade", function(p) { return p.source.index != i && p.target.index != i; }); } }</script>


Figure. A chord map of ODs in a metro network.

