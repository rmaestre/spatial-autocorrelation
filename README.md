Abstract
========

This article will focus on the spatial autocorrelation, using the space in a plane to better understand the signals among close locations in the space. We apply this method in a public dataset related to home intrusions among Spain provinces retrieved from the website of a security [company](http://www.conseguridad.org/cp/).




Spatial correlation
===================
A common metric to measure and show the distributions and patterns of the spatial correlation is the MORAN I test. Moran's I is defined as:

![](http://upload.wikimedia.org/math/2/c/9/2c9a9580448f41debc44790e9b5e2031.png)

A deep introduction to MORAN's I test and spatial autocorrelation can be founded at [Spatial Statistics: Spatial Autocorrelation][], [Geoda][], [R Ape library][],  [Moran's I in R][] or [Global Spatial Autocorrelation Indices][].

In order to show a brief introduction, we propose the next grid points distributed in a plane (15x15)

![Simple grid](../master/img/grid_clusteredMapNewFrame.png?raw=true "Simple grid")

Then, we apply two distributions of weights in each point, the left one is a clustered distribution and the right one is a random distribution.

Clustered | Random |
----------|----------|
![Simple grid](../master/img/grid_clusteredCartogramNewFrame.png?raw=true "Simple grid") | ![Simple grid](../master/img/grid_randomCartogramNewFrame.png?raw=true "Simple grid")  |

By means of [Geoda][] software, we obtain the MORAN’s I score from the two previous distributions of weights.


Clustered dist. MORAN’s I score | Random dist. MORAN’s I score |
----------|----------|
![Simple grid](../master/img/grid_clusteredLisaScatterPlotFrame.png?raw=true "Simple grid") | ![Simple grid](../master/img/grid_randomLisaScatterPlotFrame.png?raw=true "Simple grid")  |


Two main results should be pointed out: In one hand,  a measurement of the MORAN’s I test is 0.6744 in the clustered case and -0.00339 in the random case. These results show that near to 1 this metric show a high positive spatial autocorrelation in the data, near to -1 a high negative spatial autocorrelation and near to 0 a null spatial autocorrelation. In the other hand, each quadrant of the MORAN`s I test shows the four different spatial autocorrelation between points in the space, e.g. high-high, low-low, high-low, low-high.
In the example, we can see the next distributions:


Selected quadrant | Cartogram selection | Grid selection |
----------|----------|----------|
![Grid qudrant](../master/img/grid/quadrant1/grid_clusteredLisaScatterPlotFrame.png?raw=true "Grid qudrant") | ![Simple grid](../master/img/grid/quadrant1/grid_clusteredCartogramNewFrame.png?raw=true "Grid qudrant") | ![Grid qudrant](../master/img/grid/quadrant1/grid_clusteredMapNewFrame.png?raw=true "Grid qudrant") |
![Grid qudrant](../master/img/grid/quadrant2/grid_clusteredLisaScatterPlotFrame.png?raw=true "Grid qudrant") | ![Simple grid](../master/img/grid/quadrant2/grid_clusteredCartogramNewFrame.png?raw=true "Grid qudrant") | ![Grid qudrant](../master/img/grid/quadrant2/grid_clusteredMapNewFrame.png?raw=true "Grid qudrant") |
![Grid qudrant](../master/img/grid/quadrant3/grid_clusteredLisaScatterPlotFrame.png?raw=true "Grid qudrant") | ![Simple grid](../master/img/grid/quadrant3/grid_clusteredCartogramNewFrame.png?raw=true "Grid qudrant") | ![Grid qudrant](../master/img/grid/quadrant3/grid_clusteredMapNewFrame.png?raw=true "Grid qudrant") |
![Grid qudrant](../master/img/grid/quadrant4/grid_clusteredLisaScatterPlotFrame.png?raw=true "Grid qudrant") | ![Simple grid](../master/img/grid/quadrant4/grid_clusteredCartogramNewFrame.png?raw=true "Grid qudrant") | ![Grid qudrant](../master/img/grid/quadrant4/grid_clusteredMapNewFrame.png?raw=true "Grid qudrant") |
![Grid qudrant](../master/img/grid/quadrant5/grid_clusteredLisaScatterPlotFrame.png?raw=true "Grid qudrant") | ![Simple grid](../master/img/grid/quadrant5/grid_clusteredCartogramNewFrame.png?raw=true "Grid qudrant") | ![Grid qudrant](../master/img/grid/quadrant5/grid_clusteredMapNewFrame.png?raw=true "Grid qudrant") |



USE CASE: SPATIAL AUTO CORRELATION OF HOME INTRUSIONS IN SPAIN
==============================================================
Nowadays business is starting to provide their data through online applications. Sometimes this data is wasted because companies do not exploit deeply the analysis or the visualizations. 
In this use case study we explore how can convert this public data into a valuable asset for a company from a business intelligence point of view. 

We should bear in mind that this data are provided by a private company and we can not be sure if this data has been manipulated or mistakes has been made in the grouped process, however we conduct this analysis with these assumptions.

S.D. is one of the main security company across Spain , mainly especially in home alarm systems. A huge network of alarms across Spain belongs to this company, show they are able to explore the data related to intrusions in homes. 
We point out the first summary:

    > data <- read.csv("/Users/rmaestre/Projects/spatial-autocorrelation/data/data_normalized_SPAIN.csv", sep = "\t")
    > summary(data)
          cod             lat              lng              intrusion      
    Min.   : 1120   Min.   :-23.56   Min.   :-103.7412   Min.   :  0.000  
    1st Qu.:13260   1st Qu.: 38.41   1st Qu.:  -5.6300   1st Qu.:  2.000  
    Median :28049   Median : 40.62   Median :  -3.4902   Median :  4.000  
    Mean   :26367   Mean   : 39.98   Mean   :  -3.3452   Mean   :  9.513  
    3rd Qu.:39005   3rd Qu.: 42.19   3rd Qu.:  -0.5542   3rd Qu.:  9.000  
    Max.   :52006   Max.   : 61.95   Max.   : 100.8113   Max.   :400.000  
    variation       flag_variation
    Min.   :   0.00   neg : 974     
    1st Qu.:   0.00   null:1728     
    Median :  13.60   pos :1807     
    Mean   :  44.12                 
    3rd Qu.:  88.20                 
    Max.   :2292.60 

The figure below shows the distribution of intrusion incidents among Spain grouped by Zip code provided by S.D and provide the first approach to better understand the data.

![Spain](../master/img/qgis/spain.png?raw=true "Spain")

 More detailed, we can show below the Madrid province divided by ZIP code, and with color graduated points by the number of intrusions, big circle means big intrusion area.
 
![Madrid](../master/img/qgis/madrid.png?raw=true "Madrid")
 
Using Geoda, we can represent the same information by means of a cartogram visualization
 
![Madrid](../master/img/madridCartogramNewFrame.png?raw=true "Madrid")

Finally the MORAN`s I test shows a certain correlation between values of the points and its spatial autocorrelation
 
![Madrid](../master/img/madridLisaScatterPlotFrame.png?raw=true "Madrid")



Selected quadrant | Cartogram selection
----------|----------|
![Grid qudrant](../master/img/madrid/quadrant1/madridLisaScatterPlotFrame.png?raw=true "Grid qudrant") | ![Simple grid](../master/img/madrid/quadrant1/madridCartogramNewFrame.png?raw=true "Grid qudrant") |
![Grid qudrant](../master/img/madrid/quadrant2/madridLisaScatterPlotFrame.png?raw=true "Grid qudrant") | ![Simple grid](../master/img/madrid/quadrant2/madridCartogramNewFrame.png?raw=true "Grid qudrant") |
![Grid qudrant](../master/img/madrid/quadrant3/madridLisaScatterPlotFrame.png?raw=true "Grid qudrant") | ![Simple grid](../master/img/madrid/quadrant3/madridCartogramNewFrame.png?raw=true "Grid qudrant") |



The pictures below show one zone with high-high spatial autocorrelation in the south and north of Madrid with high ratio of intrusions, and another one  with low-low spatial auto correlation located in the north-center of the city with low intrusions ratio. **The last quadrant is related to high values representing isolated locations with high intrusion ratios useful for point out emergent intrusions areas.**
 

Inference of Moran's I
===================
The permutation method ([Análisis de datos espacio-temporales para la economía y el geomarketing][]) allow us to estimate the values of mean and standard deviation from Moran's I statistic through a random rearrangement of the spatial variable values, i.e. the n! Moran`s I statistic are calculated and the mean and standard deviation are calculated from the n! samples.

The below picture shows a vertical line  with a high value with respect to the values calculated with the permutation method. Therefore the value of variable INTRUSION in its original spatial configuration is clearly above to I values from the 999 permutations performed.

![Permutations method](../master/img/permutations_method.png?raw=true "Permutations method")

Also a p-value is provided (p-value = 0.001), thus we can affirm that the variable Intrusion has a spatial dependence structure with a 99.999%.

Conclusions
===================
First of all, we should be aware of the sources of the public data, in this study, we used data from a private company; this company perhaps distributed this data with a marketing purpose therefore we should be cautious with the results.

We performed a simple analysis based on Moran's test with the main goal to understand the spatial autocorrelation of the data. We can use several opensource to analyze the Moran`s I test and study the distributions per quadrants.

Also, more qualitative and quantitative variables from open datasets could be crossed with further analysis to test more hypothesis, e.g.: [Anuario Estadístico del Ministerio del Interior](http://www.interior.gob.es/file/63/63661/63661.pdf) about criminal rates in Spain.


Other analysis
===================

León
![Leon](../master/img/leon/leon.png?raw=true "Leon") 


Selected quadrant | Cartogram selection
----------|----------|
![Leon qudrant](../master/img/leon/quadrant1/leonLisaScatterPlotFrame.png?raw=true "Leon qudrant") | ![Leon grid](../master/img/leon/quadrant1/leonCartogramNewFrame.png?raw=true "Leon qudrant") |
![Leon qudrant](../master/img/leon/quadrant2/leonLisaScatterPlotFrame.png?raw=true "Leon qudrant") | ![Leon grid](../master/img/leon/quadrant2/leonCartogramNewFrame.png?raw=true "Leon qudrant") |
![Leon qudrant](../master/img/leon/quadrant3/leonLisaScatterPlotFrame.png?raw=true "Leon qudrant") | ![Leon grid](../master/img/leon/quadrant3/leonCartogramNewFrame.png?raw=true "Leon qudrant") |

p-value from permutations method

![Leon](../master/img/leon/permutation_method.png?raw=true "Leon") 



  [Moran's_I]: http://en.wikipedia.org/wiki/Moran's_I        "Moran's_I"
  [Moran's I in R]:  http://www.ats.ucla.edu/stat/r/faq/morans_i.htm  "Yahoo Search"
  [Spatial Statistics: Spatial Autocorrelation]:    http://libraries.mit.edu/news/category/subject-areas/gis/    "Spatial correlation"
  [Geoda]: http://geodacenter.asu.edu/ "Geoda"
  [R Ape library]: http://cran.r-project.org/web/packages/ape/ "APE R"
  [Global Spatial Autocorrelation Indices]: http://www.lpc.uottawa.ca/publications/moransi/moran.htm "GSAI"
  [Análisis de datos espacio-temporales para la economía y el geomarketing]: http://www.researchgate.net/publication/256116713_Anlisis_de_datos_espacio-temporales_para_la_economa_y_el_geomarketing "Analisis de datos espacio temporales"
