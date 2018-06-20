# Welcome to Xiaoqing DAI's blog

<font face="Century Schoolbook"> Xiaoqing's research interests include: travel demand prediction, intelligent transportation systems, big data, behavior modeling and transportation planning.</font>

This blog presents some of my research. 

You can find the pdf version of my resume here. [XiaoqingDAI's resume](XiaoqingDAI_resume_201806acdemic_final.pdf)

### Travel demand prediction under non-recurrent situations 


<font face="Century Schoolbook"> The goal is to predict travel demand under non-recurrent situations based on normal historical data. The model has been developed for metro systems. </font>

  
[//]: # ![](heatmap130906.gif)
[//]: # Figure. A heatmap of out-station volume of Shanghai metro on a normal day.

![](heatmap130913.gif)
Figure. A heatmap of out-station volume of Shanghai metro on a heavy rainy day with disruption in the afternoon.

---

### Intelligent Transportation System Planning


Intelligent transportation system planning based on consideration of smart connected vehicles. The V2I roadside environment design and the coordinated traffic signal control/traffic guidance system design are included.

![](anting_roadmap.png)
Figure. A roadmap of the planning area.

---

### OD is intereseting, right?

//\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*
// CREATE MATRIX AND MAP
//\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*
d3.csv('trade11.csv', function (error, data) { var mpr = chordMpr(data);
mpr .addValuesToMap('importer1') .addValuesToMap('importer2')
.setFilter(function (row, a, b) { return (row.importer1 === a.name &&
row.importer2 === b.name) || (row.importer1 === b.name && row.importer2
=== a.name) }) .setAccessor(function (recs, a, b) { if (!recs\[0\])
return 0; return recs\[0\].importer1 === a.name ? +recs\[0\].flow1 :
+recs\[0\].flow2; }); drawChords(mpr.getMatrix(), mpr.getMap()); });
//\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*
// DRAW THE CHORD DIAGRAM
//\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*
function drawChords (matrix, mmap) { var w = 980, h = 800, r1 = h / 2,
r0 = r1 - 110; var fill = d3.scale.ordinal()
.range(\['\#c7b570','\#c6cdc7','\#335c64','\#768935','\#507282','\#5c4a56','\#aa7455','\#574109','\#837722','\#73342d','\#0a5564','\#9c8f57','\#7895a4','\#4a5456','\#b0a690','\#0a3542',\]);
var chord = d3.layout.chord() .padding(.02)
.sortSubgroups(d3.descending) .sortChords(d3.descending); var arc =
d3.svg.arc() .innerRadius(r0) .outerRadius(r0 + 20); var svg =
d3.select("body").append("svg:svg") .attr("width", w) .attr("height", h)
.append("svg:g") .attr("id", "circle") .attr("transform", "translate(" +
w / 2 + "," + h / 2 + ")"); svg.append("circle") .attr("r", r0 + 20);
var rdr = chordRdr(matrix, mmap); chord.matrix(matrix); var g =
svg.selectAll("g.group") .data(chord.groups())



Figure. A chord map of ODs in a metro network.

[//]: # (You can use the [editor on GitHub](https://github.com/XiaoqingDai/XiaoqingDai.github.io/edit/master/index.md) to maintain and preview the content for your website in Markdown files.)

[//]: # (Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.)

[//]: # For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

[//]: # Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/XiaoqingDai/XiaoqingDai.github.io/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

[//]: # Having trouble with Pages? Check out our [documentation](https://help.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.
