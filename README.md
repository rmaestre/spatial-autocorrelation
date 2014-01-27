Abstract
========

This article will focus on the spatial autocorrelation, using the space in a plane to better understand the signals among close locations in the space and we apply this method in a public data related to the home intrusions among Spain provinces retrieved from the website of the company.


Spatial correlation
===================
A common metric to measure and show the distributions and patterns of the spatial correlation is the MORAN I test. Moran's I is defined as:

![](http://upload.wikimedia.org/math/2/c/9/2c9a9580448f41debc44790e9b5e2031.png)


In order to show a brief introduction, we propose the next grid points distributed in a plane

![Simple grid](../master/img/grid_clusteredMapNewFrame.png?raw=true "Simple grid")

Then, we apply two distributions of weights in each point, the left one is a clustered one and the right one is a random distribution.

![Simple grid](../master/img/grid_clusteredMapNewFrame.png?raw=true "Simple grid")


Clustered | Random |
----------|----------|
![Simple grid](../master/img/grid_clusteredCartogramNewFrame.png?raw=true "Simple grid") | ![Simple grid](../master/img/grid_randomCartogramNewFrame.png?raw=true "Simple grid")  |


By means of Geoda [cite] software, we can obtain the MORAN’S I score.


Clustered MORAN’S I score | Random MORAN’S I score |
----------|----------|
![Simple grid](../master/img/grid_randomLisaScatterPlotFrame.png?raw=true "Simple grid") | ![Simple grid](../master/img/grid_clusteredLisaScatterPlotFrame.png?raw=true "Simple grid")  |


A deep introduction to MORAN I test and spatial autocorrelation can be founded at [citas: libro del csic, mit, etc. …], 
Two main results should be pointed out: In one hand,  a measurement of the MORAN’S I test is 0.6744 in the clustered case and -0.00339 in the random case. These results show that near to 1 this metric show a high positive spatial autocorrelation in the data, near to -1 a high negative spatial autocorrelation and near to 0 a null spatial autocorrelation. In the other hand, each quadrant of the MORAN`s I test shows the four different spatial autocorrelation between points in the space, e.g. high-high, low-low, high-low, low-high.
In the example, we can see the next distributions:


Select quadrant | Cartogram selection | Grid selection |
----------|----------|----------|
![Grid qudrant](../master/img/grid/quadrant1/grid_clusteredLisaScatterPlotFrame.png?raw=true "Grid qudrant") | ![Simple grid](../master/grid/quadrant1/img/grid_clusteredCartogramNewFrame.svg?raw=true "Grid qudrant") | ![Grid qudrant](../master/grid/quadrant1/img/grid_clusteredMapNewFrame.png?raw=true "Grid qudrant") |
![Grid qudrant](../master/img/grid/quadrant2/grid_clusteredLisaScatterPlotFrame.png?raw=true "Grid qudrant") | ![Simple grid](../master/grid/quadrant2/img/grid_clusteredCartogramNewFrame.svg?raw=true "Grid qudrant") | ![Grid qudrant](../master/grid/quadrant2/img/grid_clusteredMapNewFrame.png?raw=true "Grid qudrant") |
![Grid qudrant](../master/img/grid/quadrant3/grid_clusteredLisaScatterPlotFrame.png?raw=true "Grid qudrant") | ![Simple grid](../master/grid/quadrant3/img/grid_clusteredCartogramNewFrame.svg?raw=true "Grid qudrant") | ![Grid qudrant](../master/grid/quadrant3/img/grid_clusteredMapNewFrame.png?raw=true "Grid qudrant") |
![Grid qudrant](../master/img/grid/quadrant4/grid_clusteredLisaScatterPlotFrame.png?raw=true "Grid qudrant") | ![Simple grid](../master/grid/quadrant4/img/grid_clusteredCartogramNewFrame.svg?raw=true "Grid qudrant") | ![Grid qudrant](../master/grid/quadrant4/img/grid_clusteredMapNewFrame.png?raw=true "Grid qudrant") |
![Grid qudrant](../master/img/grid/quadrant5/grid_clusteredLisaScatterPlotFrame.png?raw=true "Grid qudrant") | ![Simple grid](../master/grid/quadrant5/img/grid_clusteredCartogramNewFrame.svg?raw=true "Grid qudrant") | ![Grid qudrant](../master/grid/quadrant5/img/grid_clusteredMapNewFrame.png?raw=true "Grid qudrant") |



USE CASE: SPATIAL AUTO CORRELATION OF HOME INTRUSIONS IN SPAIN
==============================================================
Nowadays business is starting to provide their data through online applications [citas de aplicaciones de datos]. Sometimes this data is wasted because companies do not exploit deeply the analysis or the visualizations. 
In this article we explore how can convert this public data into a valuable asset for a company from a business intelligence point of view. 

We should bear in mind that this data are provided by a private company and we can not be sure if this data has been manipulated or mistakes has been made in the grouped process, however we conduct this analysis with these assumptions.

S.D. is one of the main security company across Spain , mainly especially in home alarm systems. A huge network of alarms belongs to this company, show they are able to explore the data related to intrusions  in homes. The figure below shows the distribution of intrusion incidents among Spain grouped by Zip code provided by S.D and provide the first approach to better understand the data.




