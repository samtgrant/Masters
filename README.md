# Masters
How do wildfires affect the vegetation structure in the savannahs of the Central African Republic? An analysis using MODIS and ICESat-2 data products.
Sam Grant - Progress Report

1. Project Outline
This project aims to combine a time-series analysis of NASA’s MODIS satellite data with more detailed spatial data from the novel ICESat-2 satellite to better constrain the effect of wildfires on the vegetation structure within the savannah regions of the Central African Republic. The primary hypothesis to be tested is that there is a positive relationship between fire frequency and mean tree height, but tree density is unaffected. The increase in mean tree height will also be observed as an increase in tree height heterogeneity, as only tall trees remain.

This project also aims to test a secondary hypothesis that there is a negative relationship between fire frequency and greenness indicators, such as NDVI. This project aims to provide valuable insights into the large-scale effects of wildfires on vegetation structure. In particular, it aims to reduce uncertainty on the relationship between fire frequency and tree density in African savannahs (Higgins et al., 2007). The submitted timeline for this project is shown in figure 1.

2. Project Progress
2.1 Data Preparation
This project requires significant amounts of data to download (currently 660 GB) which requires its own script and software to download. The data is saved onto an external hard drive. 

2.2 Data Analysis
The data analysis of this section is currently ahead of the estimated schedule. All the completed data analysis has been carried out in python using Jupyter Notebook as the Integrated Development Environment (IDE). Jupyter Notebook was chosen because it can run software code, computational output and explanatory text in individual cells, making it easier to explain the purpose of each part of the python script.

The MODIS data products are downloaded as HDF4 files, which store the relevant pixel data in 2400 by 2400 two-dimensional arrays (tiles), with each cell representing a 500m grid. My study area (Central African Republic) overlaps four MODIS tiles, so each analysis step must be repeated for the different tiles. The following analysis is for the h20v08 tile.

The downloaded MODIS data spans 18 years, from 2002 to 2019. The first step was to split the files, dividing the first and second 9 years. Then, I was able to count the number of times each pixel burnt across the 9-year sections, and store this data in two arrays, named “first_BA” and “second_BA”. Using the number of fires across the 9-year sections, I could assign each pixel a value. Each pixel was assigned “low” if there were no fires over the 9-year period, “med” if there were between 1 and 6 fires and “high” if there were more than 6 fires. Then, a new array could be assigned the category value of one of the 9 categories devised from the fire frequency over the two arrays, as shown by the table below. 

I repeated this process but used the MCD12Q1 (Land Cover Type) product to assign a Category Value of 0 if the pixels land cover was not classified as “savannah” or “woody savannah”. The number of pixels in each category was counted using NumPy’s count_nonzero() function; the results of which are shown in figure 2a. This data could then be visualised by 9 separate colourmaps using matplotlib, a python visualisation library (figure 2b). 

The results show a slight decreasing trend in fire frequency between the two 9-year periods, which is consistent with the larger regional trend (Andela et al., 2017).  I chose this method of categorising my data because the category value for each pixel could then be used to compare fire frequency and the mean tree height from the ICESat-2 data products.

This data is stored as transects, not in MODIS tiles, which means I had to convert the data in order to compare it. I converted the mean canopy height from the ATL08 data set and stored it in a 2400 by2400 array to allow me to compare mean canopy height to fire frequency.

In this early stage of analysis, there is no clear trend between an increase in fire frequency and an increase in mean tree canopy height. This could be due to many of the other factors which affect tree canopy height and have not yet been accounted for, such as rainfall.

I have used python to visualise the ATL08 mean canopy height data. This shows the clear trend of increasing mean canopy height toward the south, as savannah areas transition to forests (Eva and Grégoire, 2001; Freeborn et al., 2014.). I also plotted the data in QGIS , where I used the TIN interpolation tool to fit the data to the Central African Republic. 

I am currently ahead of schedule for my data analysis, which I started in December, two months before planned. This is likely to be beneficial as early data analysis suggests that testing the hypothesis may be more complicated than expected and I am likely to require more data to find reliable trends.

2.3 Project Write Up
Unfortunately, the progress made in analysing my data has largely come at the expense of writing up my dissertation. I have decided to focus on my data analysis because the outcome of this analysis will alter my projects methods section, which risks making my previous write-up outdated. However, it would have been beneficial to have allocated more time to write up the introduction and hypothesis section, as this is unlikely to change significantly and may also help to cement my understanding of the literature. 

With three months left of the project, it isn’t a cause for significant concern, but starting to progressively allocate more time to writing up my dissertation would be sensible. This would also allow me to spend longer on my data analysis instead of curtailing it early to complete my project write up.

3. Changes to Project 
Since starting my project in earnest, I have made some small changes to the original project plan. Firstly, cutting the MODIS data from the tiles to only fit the Central African Republic is not a priority at this stage and is likely to be time consuming, so I will complete this job with the final data set.  

Also, in my project plan, I did not clearly think through what contributed “a change” in fire frequency and I have experimented with calculating this in different ways for my data analysis. I am currently using the “low”, “medium” and “high” categories previously outlined, although the definitions of this may change to best fit the spread of data. In my project plan, I had created four categories for both nine year periods, although I found this meant too few pixels were assigned to each of the 16 total categories. 

As previously mentioned, I aim to use the extra time I have for data analysis to further explore how changes in rainfall affects the trends I am currently observing, something I did not expect to have time for in my original project plan.
