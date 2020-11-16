# Capstone project: Finding a Good Location to Open Thailand Restaurant in Jakarta, Indonesia.

- A final report for the course ["Applied Data Science Capstone"](https://www.coursera.org/learn/applied-data-science-capstone) given by IBM on Coursera
- [Full report](https://github.com/imamjabar/Thai-Restaurants-in-Jakarta/blob/master/report.pdf)
- [Presentation](https://github.com/imamjabar/Thai-Restaurants-in-Jakarta/blob/master/presentation.pdf)

## A. Problem's description

The city of Jakarta is well known to be a cosmopolitan city where you can find people from all around the world with over 11 million people live and it has a population density of over 16 thousand people per square kilometer. The city is divided into 44 districts in total (including Thousand Island districts). 

An investor is looking to open a new ***Thailand Restaurant*** in Jakarta, but he is not sure about the best location for his new venue and needs input for making the decision. Although there are a lot of districts in Jakarta, their density between them is not uniform. Some districts are containing too many restaurants while there are less in some others.

If we have some knowledge about the population density, the housing price in each district coupling with an overview of the number of restaurants, we can have a better idea to set up a new business there. We expect to choose a place where the population density is high but fewer competitors. If the housing price in that place is low, it’s more attractive to us.

The project aims to find a good location for a Thailand Restaurant in Jakarta. This will be determined by analyzing the number of restaurants, the population density, and the average housing price in each district.

## B. Data Description

- List of Jakarta City administrative units from **official Jakarta annual publication** [1] and **OpenStreetMap mapping project** [2]. It gives us a list of all urban districts of Jakarta with their area (in km²), population (in 2020), and the density of each district (people/km²).
- List of the coordinates (latitude, longitude) of 42 urban districts in Jakarta (without Thousand Island). This list can be generated based on the name of each district using **Nominatim** package. *geopy.geocoders.Nominatim*
- List of average housing prices per m² from **real estate marketplace web page** [3].
- A modified `.json` file that contains all coordinates where we use it to create a choropleth map of the Housing Sales Price Index of Jakarta. From **Jakarta Geospatial Information site** [4].
- **Foursquare API** [5] to select the number of restaurants and their location in some neighborhoods of Jakarta.

## C. Methodology

1. First, we need to collect all urban districts of Jakarta data from Jakarta annual publication to get **District Name**, **Area**, and **Population**. Also, collect **Average Housing Price** from the real estate marketplace. Then save it to `.csv` file.
2. The column **Density** is calculated later based on columns **Population** and **Area** of each district.
3. Throughout the project, we use **numpy** and **pandas** packages to manipulate data frames
4. We use **geopy.geocoders.Nominatim** package to get the coordinates of districts and add them to the main data frame.
5. We use **Foursquare API** to explore Thailand Restaurant venues in each district.
6. For clustering the "Thailand Restaurant" venues between districts, we use **K-Means Clustering** method and the package **scikit-learn** to implement the algorithm on our data. In order to indicate how many K for the method, we try with 10 different values of K from 1 to 10 and use the **elbow method** to choose the most appropriate one.
7. In order to visualize the charts, we use package **matplotlib** and **seaborn**.
8. We use the package **folium** to visualize the Jakarta map with its districts.

## D. References:

* [1] [DKI Jakarta Province in Figures](https://jakarta.bps.go.id/publication/2020/04/27/20f5a58abcb80a0ad2a88725/provinsi-dki-jakarta-dalam-angka-2020.html)
* [2] [HOT PDC InAWARE Mapping Project 2017](https://issuu.com/harryhotosm)
* [3] [Lamudi](https://www.lamudi.co.id/trends/)
* [4] [Jakarta Geospatial Site](http://gis.bpbd.jakarta.go.id/layers/geonode%3Adki_kecamatan)
* [5] [Foursquare API](https://developer.foursquare.com/)
