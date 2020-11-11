# sheriff_data
Sheriff and demographic data on 2,000+ US counties

## __Data Source__

This dataset comes from the Reflective Democracy Campaign, a nonprofit that "investigates and the demographics of power in the United States. The data helps to prove that white male 'electability' is a myth, and that voters want women of all races and men of color to represent them. Their research shines a light on both the recent waves of victories by candidates who reflect the American people, and the structural barriers that still prevent a fair distribution of political power."

The Reflective Democracy Campaign and the Center for Technology and Civic Life have partnered to produce datasets examining the demographics of 3,000+ elected sheriffs; 2,800+ elected prosecutors; and candidates for federal, state, and local offices in 2012, 2014, 2016, and 2018.

This particular dataset examines sheriffs in 2,300 counties and other jurisdictions in the US in 2018. Findings show that there are very few jurisdictions with Hispanic, Asian, or black sheriffs. There are also very few women who hold the title. The data is merged with US Census Bureau estimates for 2018 for a more complete demographic picture.
This data comes from https://wholeads.us/ 
and https://console.cloud.google.com/marketplace/product/united-states-census-bureau/us-census-data?filter=solution-type:dataset&q=census&id=2c089839-2b4a-477a-962b-4a8b730d0a12

## __Usefulness__

The project was explored organically and used dimension reduction techniques to separate the data into three groups. The end result corresponded well to the political affiliation of the sheriff elected in each particular county. A density-based algorithm was able to distinguish these three clusters (Democrat, Republican, and Independent), as well as the borders and outliers of each cluster. 

There were a number of features that fed into the model and helped separate data points. The features were dummy variables from the sheriff individuals, as well as demographic information from the county electorate population. 

When analyzing the clusters by feature, we get a clearer picture of the factors that lead a general population to vote for sheriffs based on demographic characteristics. This information could be used for exploring electability of certain candidates and marketing purposes.

## __Get Help With This Project__

The main contributor for the project is Dean McClure, mcclure.dean@gmail.com. The contact for the source material (sheriff data) is Asha Muralidharan, asha@wholeads.us

