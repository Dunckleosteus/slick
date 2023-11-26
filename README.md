# Slick 
This is a project aiming to detect oil leaks in the ocean using Landsat 5 data
# The oil leak
Deepwater Horizon oil spill, largest marine oil spill in history, caused by an April 20, 2010, explosion on the Deepwater Horizon oil rig—located in the Gulf of Mexico, approximately 41 miles (66 km) off the coast of Louisiana—and its subsequent sinking on April 22. ([Britannica](https://www.britannica.com/event/Deepwater-Horizon-oil-spill))
- 28°44'17''N, 88°21'58'W
# Landsat data
I tried to use Landsat 8 data but there was missing data. For this project we have 3 images. The first image was taken 13 days before the accident, the second one was taken 19 days after the accident and the last one 30 days after the accident. 
# Goals
As an academic project this project has 2 main objectives: 
1. See which combinations work best for detecting the oil leak
2. Compare the evolution of oil spread over the time
# Data analysis
We tried various indices to see if any of them showed any promise in detecting the oil spill.
## RGB Images
Here are the RGB composition for the satellite pictures, the oil stain is visible in the right of the pictures taken after the accident. We can see that the stain seems to grow over time in visible light. 
![SAVI](/images/rgb_images.png).
## Ferrous Minerals
![SAVI](/images/ferrous_mineral_images.png).
Does not seem to show much promise when it comes to detecting hydrocarbons. 
## VARI
![SAVI](/images/vari_images.png).
## NDVI 
![NDVI](/images/ndvi_images.png "NDVI").
## SAVI
![SAVI](/images/savi.png).
## MNDWI 
![SAVI](/images/mndwi_images.png).
This composition seems to show promise when it comes to detecting the oil. That is why we did some stats on it: 
#### Stats
##### Scatter
![SAVI](/images/mndwi_scatter.png).
##### Correlation
![SAVI](/images/mndwi_correlation_heatmap.png).
##### Manual classification
I started by dividing the image into 2 classes: 
- Values over 0.75 that are either a landmass or oil infused water
- Values under 0.75 that are probably clean sea water
![SAVI](/images/mndwi_manual_classification.png).
We can also count the number of each class for each image:
![SAVI](/images/mndwi_barplot.png).
Because we know that image 1 has no leak (normally), we can substract it's number of pixels over the threashold to have a better estimate of oil quantity. This is more or less the same as removing the number of pixels that represent a landmass as they also have a value over 0.75. 
We can see that the value seems to increase, wich seems normal.
# Unsupervised classification 
Tried a unsupervised classification
![SAVI](/images/unsupervised_classification.png).
