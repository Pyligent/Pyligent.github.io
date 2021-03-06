---
layout: post
title: Kijiji Web Scraping Project
subtitle: Scrapping Car information from kijiji website
bigimg: /img/car_project.jpg
image: /img/kijiji.png
tags: [Data Analytics, Web Scraping,ELT,Python]
---

##### [Project Website]<https://pyligent.github.io/Car_ETL_PROJECT/>



#### Table of Contents
+ [Data Source](#Data-Source)
+ [1. Extraction](#1-Extraction)
+ [2. Transformation](#2-Transformation)
+ [3. Data Analysis](#3-Data-Analysis)
+ [4. Load](#4-Load)

---
#### Data Source
- Scraped:   [Kijiji Car Website (GTA Data)](https://www.kijiji.ca/b-cars-vehicles/city-of-toronto/c27l1700273)
- Scraped:   <https://www.autolist.com> (U.S. Data)
- API:       [Car Query API](http://www.carqueryapi.com/) (use the [json files](data/carquery.json))
- CSV:       [Fuel Economy Web Service](https://www.fueleconomy.gov/feg/ws/index.shtml#fuelType1) offers the fuel economy database 
- CSV:        <https://www.kaggle.com/toramky/automobile-dataset/kernels?sortBy=hotness&group=everyone&pageSize=20&datasetId=1291&language=Python>


#### 1. Extraction

##### 1.1. Extract all listing car information in GTA area from [kijiji website](www.kijiji.ca)

[A. Kijiji Scaper (raw data)  - Jupyter Notebook](https://nbviewer.jupyter.org/github/Pyligent/Car_ETL_PROJECT/blob/master/kijii_car_scaper.ipynb)

[B. Kijiji Scaper (clean data with vin number and image link)  - Jupyter Notebook](https://nbviewer.jupyter.org/github/Pyligent/Car_ETL_PROJECT/blob/master/kijiji_car_scaper_fullset.ipynb)
##### Key Car information is as below(Clean Data Scraper):

- 'brand'
- 'model'
- 'model_year' : Type: int
- 'list_price' : Type: int
- 'color'
- 'configration'
- 'condition'
- 'body_type'
- 'wheel_config'
- 'transmission'
- 'fuel_type'
- 'mileage'  : Type: int
- 'carfax_link'
- 'vin_number'
- 'image_link'
- 'dealer_address'

##### Examples:

##### Car Information link: https://www.kijiji.ca/v-cars-trucks/city-of-toronto/2009-ford-f-150-xlt-super-crew-4x4/1385290163

- brand: 'Ford'
- model: 'F-150'
- model_year:'2009'
- list_price:'11999'
- color: 'Blue'
- configration: 'XLT'
- condition: 'Used'
- body_type: 'Pickup Truck'
- wheel_config: '4 x 4'
- transmission: 'Automatic'
- fuel_type:  'Gasoline'
- mileage: '204000'
- carfax_link: 'https://www.carproof.com/order?ref=kijiji&vin=1FTRW14819FB42024'
- vin_number: '1FTRW14819FB42024'
- image_link: 'https://i.ebayimg.com/00/s/NDgwWDY0MA==/z/c9AAAOSwDkBbpAaq/$_59.JPG'
- dealer_address: '2 Castleton Ave unit 3, York, ON, M6N 3Z5'

##### 1.2. Extract all listing car information from [autolist website](https://www.autolist.com)
- [Autolist.com scaper - Jupyter Notebook](https://nbviewer.jupyter.org/github/Pyligent/Car_ETL_PROJECT/blob/master/mlouisju/ETL%20Project%20-%20Autolist.ipynb)

#### 2. Transformation

##### 2.1 Data Tansform - Scraped Data
- Clean the dirty data
- Merge the csv/api data to get the MPG and displacement information

- [Kijiji Data Transformation and Plot - Jupyter Notebook](https://nbviewer.jupyter.org/github/Pyligent/Car_ETL_PROJECT/blob/master/Kijiji_Data_Trans_Plot_v2.ipynb)
- [Kijiji Data merge with MPG/Displacement- Jupyter Notebook](https://nbviewer.jupyter.org/github/Pyligent/Car_ETL_PROJECT/blob/master/Kijiji_mpgdata_merge.ipynb)
- [Kijiji Data merge with MPG/Displacement- Jupyter Notebook](https://github.com/Pyligent/Car_ETL_PROJECT/blob/master/Kijiji_merging.ipynb)
- [Autolist Data merge with Fuel Economy Database - Jupyter Notebook](https://nbviewer.jupyter.org/github/Pyligent/Car_ETL_PROJECT/blob/master/Auto_trader_merge.ipynb)

##### 2.2 Data Tansform  - API Data
##### Key Car information extracted is as below:
 - Year
 - Make
 - Model
 - Transmission type
 - MPG
 - Displacement
- [CarQuery API Data Transformation - Json file was downloaded from CarQuery Website - Jupyter Notebook](https://nbviewer.jupyter.org/github/Pyligent/Car_ETL_PROJECT/blob/master/CarQuery.ipynb)


#### 3. Data Analysis

##### 3.1 Car Information Analysis
- [Car Data Analytics - Jupyter Notebook](https://nbviewer.jupyter.org/github/Pyligent/Car_ETL_PROJECT/blob/master/car_query_charts_Tim.ipynb)


##### **Question: Can a relationship be made between car prices and fuel econnomy?**
- By using Generate Kernel Density Estimate plot using Gaussian kernels

The following chart showing the displacement of individual results underlaid by a distribution
graph showing the highest density of results. This database was almost entirely made up of used
cars, therefore the results we see are a representation of the fuel economy in relation to the
list price of available used cars. The final conclusion here is that in small numbers, used cars
of all fuel economies are available across all price points. However there is a trend with the
majority of 5k−10k cars having 20mpg or less. The trend gradually increases to demonstrate that
a high number of used cars are available at the 15k−20k price point that are far more fuel
efficient, between 23 and 30 mpg.These results are driven by two main factors, 1/ New cars tend
to have better fuel economy, and newer used cars are more expensive. Secondly, Cars with higher
fuel economy and the technologies associated with them also tend to be more expensive.


 ![Distribution of MPG vs List Price Chart](/img/plot_image/MPG_PRICE.PNG)



##### **Question: Can a relationship be made between displacement (motor size) and fuel econnomy?**

This chart displays the relationship between displacement and fuel economy. In modern cars,
lower displacement turbo charged motors are producing the same or even more horsepower than
the larger displacement naturally aspirated motors. The graph here seems to indicate that fuel
economy improves with smaller displacement regardless of turbo charging and horsepower gains.
There are a couple “outliers” with “super fuel efficiency”. These are the result of small
displacement “Hybrids” which supplement combustion power with electrical power, and represent
another level of fuel economy.


![Mpg vs Displacement Chart](/img/plot_image/Scatter_Plot_Mph_by_Displacement.png)


##### **Question: Can a relationship be made between car brand (make) and fuel econnomy?**

This bar graph displays the relationship between car manufacturer and fuel economy. As expected,
there is a clear correlation between the entry level or “economy brands having better fuel
economy. Luxury and sports cars tend to put a premium on power and weigh more, while economy
cars put more emphasis on operating costs. This trend can be clearly seen with one exception:
Lexus, while being a “luxury” brand, in this particular data set is number 1 for fuel economy.
This can be explained by the fact that Toyota was one of the first to the mass-market with hybrid
technology (Prius). They were also one of the first to introduce this hybrid technology to their
luxury division (Lexus). As this database is based on used cars, it stands to reason that both
Toyota and lexus would be found in the top 4 for fuel economy. The other two in the top 4 are
Fiat and Kia who are both known for primarily making sub-compact cars which by nature are very
fuel efficient.



![mpg brand](/img/plot_image/mpg_brand.png)


#### 3.2 Kijiji Data Analysis

- **Total car sales on kijiji website in GTA area based on Model Year**<br/>

  From the chart, we know the most listing used cars' model year is around 2015.
  Partly because after four years driving, the car is off lease and warranty is gone.
  So people is seeking to sell it.

 ![Total car sales on kijiji website in GTA area based on Model Year](/img/plot_image/kijiji_car_count.png)

- **Brand Numbers on kijiji website in GTA area**

    Top three used car listing all are Germany brand: Mercedes-Benz, Volkswagen
    and BMW

 ![Brand Numbers on kijiji website in GTA area](/img/plot_image/kijiji_brand_count.png)

- **Average Mileages based on Brands on Kijiji website**

   Amerian used cars always have the higher mileages while the luxury used cars may
   have lower mileages.

 ![Average Mileages based on Brands on Kijiji website](/img/plot_image/kijiji_brand_mean_mileage.png)

- **Average Price based on Brands on Kijiji website**

   Luxury brand used cars still have high re-sell values
 
 ![Average Price based on Brands on Kijiji website](/img/plot_image/kijiji_brand_mean_price.png)

- **Average List Price vs Average Mileage  Kernel Density Estimate**

   Most used cars' mileages will be around the 100,000km and the average price will
   be likely below $20,000.
   
 ![Average List Price vs Average Mileage  Kernel Density Estimate plot](/img/plot_image/Dist_mean_pricemile.png)

- **Average price of vehicles by vehicle type and brand**
 ![Average price of vehicles by vehicle type and brand](/img/plot_image/kijiji_type_price.png)

- **Average mileage of vehicles by vehicle type and brand**
 ![Average mileage of vehicles by vehicle type and brand](/img/plot_image/kijiji_type_mileage.png)

- **Mercedes-Benz Used Cars Data Analysis**

  Model Year: major between 2007 to 2016
  Price: mainly below $40,000
  Mileage: mainly around 100K km

 ![Mercedes-Benz Used Cars Data Analysis](/img/plot_image/kijiji_benz1.png)


 - **Lising used car Color Analysis on kijiji websit**
 
   Black and White is the most populor used car color. The  second tier
   is the Grey color and Silver

 ![Color Analysis](/img/plot_image/kijiji_color.png)



#### 3.3 Autolist Data Analysis

- **Price vs. Miles per Galon - cars made in 2015 (USA)**

![Price vs. Miles per Galon - cars made in 2015 (USA)](/img/plot_image/auto_trader_price2015_MPG.png)

- **Displacement vs. Miles per Galon (USA data)**

![Displacement vs. Miles per Galon (USA data)](/img/plot_image/auto_trader_displacement_MPG.png)

- **Price vs. Displacement - cars made in 2015 (USA)**

![Price vs. Displacement - cars made in 2015 (USA)](/img/plot_image/auto_trader_price2015_displacement.png)

- **[MPG by make (USA data)]**

![MPG by make (USA data)](/img/plot_image/auto_trader_make_MPG.png)




#### 4. Load

- put all data into MySql server via pymysql

- [Data Load to MySql Server - Jupyter Notebook](https://nbviewer.jupyter.org/github/Pyligent/Car_ETL_PROJECT/blob/master/data_load_mysql.ipynb)

   
  ![MySql Query](/img/plot_image/Data%20Load.png)
