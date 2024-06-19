## Multiscale Geographical Weighted Regression Plugin for QGIS
**THIS PLUGIN VERSION IS BASED ON MGWR: LATEST RELEASED VERSION >= 2.2.1**  [other versions here](https://github.com/pysal/mgwr/)
### Introduction
Multiscale Geographically Weighted Regression (MGWR) is a spatial regression technique used in various fields like geography, urban planning, and ecology. It's an extension of a method called Geographically Weighted Regression (GWR). It processes by fitting a regression equation to every feature in the dataset. Generally, MGWR is a powerful tool for analysing spatially varying relationships while accounting for processes happening at different geographical scales.
### Installation
1. Install dependencies:
Open `OSGeo4W` Shell installed with QGIS as `Administrator` and type:
```sh
$ python -m pip install --upgrade pip
$ python -m pip install mgwr -U
```
2. Install plugin in QGIS:
Save the mgwr.zip in local folder. Open `QGIS 3` and go to `Plugins` -> `Manage and Install plugins` -> `Install from ZIP`. Select the mgwr.zip file and press `install plugins`. The icon for the MGWR plugin will appear in the list of the installed plugins. Tick the checkbox to activate it. The plugin will appear in the ‘plugin’ menu list, toolbar and ‘Processing Toolbox’ panel.


![mgwrqgis3.png](:/a8c2594fcfc845e4b7f1b356a6a78517)


***
_Note: In case of errors rising from the `Pandas`, `Scipy`, `Spglm`, `Shapely` package, open `OSGeo4W` Shell installed with QGIS3 as `Administrator` and type:_
```sh
$ python -m pip install pandas -U
$ python -m pip install scipy -U
$ python -m pip install spglm -U
$ python -m pip install shapely -U
```
_If there is an error of `pip`, open `OSGeo4W` Shell installed with QGIS3 as `Administrator` and type:_
```sh
$ python -m ensurepip
$ python -m pip install --upgrade pip
```
_Then check your python environment. Maybe the environment in which your QGIS is running is not a standard python environment, some caused by the following:
•	May be caused by your Python version and LIBPYSAL version conflict click here_
***
### Application
Input Layer:
-	Select the input layer containing all the fields used to build local regression model.

Input Parameters:
-	Select only one dependent variable and one or multiple explanatory variables (a.k.a. independent variables).

Dependent Variable: 
-	The field containing values dependent on explanatory variable(s) in regression model

Explanatory Variable: 
-	The field(s) representing independent explanatory variable(s) in regression model.

Neighbourhood Type:
-	Select the kernel neighbourhood type, either adaptive or fixed, usually depending on how observations distribute in the region of interest.
-	Adaptive (default): The spatial context is a specified number of nearest neighbors. Where feature distribution is dense, the spatial context is smaller, while where feature distribution is sparse, the spatial context is larger.
-	Fixed: The spatial context used to solve each local regression analysis is a fixed distance. Fixed kernel type is suggested when observations distribute evenly in the research region.

Spatial Kernel Function:
-	Select one kernel function to calculate weight matrix for each observation.
_ Bisquare (default)
_ Gaussian
_ Exponential
-	Note: A potential issue with the Gaussian and Exponential kernel functions is that all observations retain non-zero weight, regardless of their distance from the calibration location. This means that even faraway observations can remain influential for moderate-to-large bandwidth parameters.
-	To avoid the issue above, the default kernel function is set to bi-square kernel. Moreover, bi-square kernel has a much more intuitive interpretation, where the bandwidth parameter is the distance or number of nearest neighbours away in space so that the remaining observations will not affect in searching optimal bandwidth parameters.

Bandwidth Searching Criterion:
-	Specify how the extent of the kernel should be determined.
-	AICc (default): Corrected Akaike information criterion is an improved version of AIC, as well as the mostly suggested one, since it penalizes smaller bandwidths that result in more complex models that consume more degrees of freedom.
-	AIC: Akaike information criterion estimates the quality of each model, relative to each of the other models.
-	BIC: Bayesian information criterion shares the same methodology with AIC, but performs better at model selection.
-	CV: Cross validation criterion compares the model residuals based on different bandwidths and chooses the optimal solution.
Minimum and Maximum Bandwidth (optional):
-	Specify the minimum and maximum bandwidth searching range for MGWR calibration.
-	Minimum or maximum bandwidth can be set as one uniform value for all variables.
-	Minimum or maximum bandwidth can be set to different value for each variable specifically. The format is a list of space-separated values, where the number of values must match the total number of explanatory variables plus one (for the intercept).

### Reference
-	[Fotheringham, A.S., Yang, W. and Kang, W., 2017. Multiscale geographically weighted regression (MGWR). Annals of the American Association of Geographers, 107(6), pp.1247-1265.](https://www.tandfonline.com/doi/abs/10.1080/24694452.2017.1352480?casa_token=LL9HQLVnJUkAAAAA:bBSsBZ_fl5gHpqcvya1LEBtCBU0XMzOcRd79RxueihDoucCDOZ5l-cAOQblyn1ujVpG-w3bOFZ36)
-	[Oshan, T.M., Li, Z., Kang, W., Wolf, L.J. and Fotheringham, A.S., 2019. mgwr: A Python implementation of multiscale geographically weighted regression for investigating process spatial heterogeneity and scale. ISPRS International Journal of Geo-Information, 8(6), p.269.](https://www.mdpi.com/2220-9964/8/6/269)
-	Xiangyang Song & Jiawei Gao [Geographically Weighted Regression (GWR) Plugin for QGIS](https://github.com/XiangyangSong/GWR_Plugin)

### License
_The Multiscale Geographically Weighted Regression (MGWR) Plugin is free software; you can redistribute it and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation._
Copyright ©  2024 Huaying Gu - [University of Pennsylvania](https://www.upenn.edu/) | Yi Wu – [University of Otago](https://www.otago.ac.nz)


© 2011-2018 GeoApt LLC - geoapt.com
