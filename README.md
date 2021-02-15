
# US Sheriff Political Clustering

[**Dataset 1**](https://wholeads.us/%C2%A0) | [**Dataset 2**](https://console.cloud.google.com/marketplace/product/united-states-census-bureau/us-census-data?filter=solution-type:dataset&q=census&id=2c089839-2b4a-477a-962b-4a8b730d0a12) 

The sheriff dataset (**Dataset 1**) comes from the Reflective Democracy Campaign, a nonprofit that "investigates and the demographics of power in the United States. The data helps to prove that white male 'electability' is a myth, and that voters want women of all races and men of color to represent them. Their research shines a light on both the recent waves of victories by candidates who reflect the American people, and the structural barriers that still prevent a fair distribution of political power."

The Reflective Democracy Campaign and the Center for Technology and Civic Life have partnered to produce datasets examining the demographics of 3,000+ elected sheriffs; 2,800+ elected prosecutors; and candidates for federal, state, and local offices in 2012, 2014, 2016, and 2018.

This particular dataset examines sheriffs in 2,300 counties and other jurisdictions in the US in 2018. Findings show that there are very few jurisdictions with Hispanic, Asian, or black sheriffs. There are also very few women who hold the title. The data is merged with US Census Bureau estimates for 2018 (**Dataset 2**) for a more complete demographic picture.

[![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://drive.google.com/file/d/1mBKHQMyzfCV8HyWhkhqWvo17tjd97nks/view?usp=sharing)


----

## Key Features

![image](https://storage.googleapis.com/sheriff_data/sheriff_race.png)
![image](https://storage.googleapis.com/sheriff_data/sheriff_gender.png)
![image](https://storage.googleapis.com/sheriff_data/class_dist.png)
![image](https://storage.googleapis.com/sheriff_data/corr_chart.png)


- Notes
	* EDA/Analysis shows a vast discrepancy at the county level in terms of education, housing occupancy, employment, and family makeup.
	* There are three basic categories of sheriff leadership: independent, Democrat and Republican.
	* The majority of sheriffs (47%) are Republican, 90% are white and 97% are male.
	* PCA did not work well to separate political categories. With t-SNE and UMAP there are three distinct categories with some small outlying clusters.

>Low-income, college-educated 20-somethings, many of whom live in urban areas, are voting more like rich, college-educated people who tend to live in the inner suburbs that are moving left.
> 
>Derek Thompson, [*The Atlantic*](https://www.theatlantic.com/ideas/archive/2020/11/2020-election-results-prove-density-destiny/617027/)

----

## Integrations

* [KMeans](https://scikit-learn.org/stable/modules/generated/sklearn.cluster.KMeans.html)
* [DBSCAN](https://scikit-learn.org/stable/modules/generated/sklearn.cluster.DBSCAN.html)
* [PCA](https://scikit-learn.org/stable/modules/generated/sklearn.decomposition.PCA.html)
* [UMAP](https://umap-learn.readthedocs.io/en/latest/how_umap_works.html)
* [t-SNE](https://scikit-learn.org/stable/modules/generated/sklearn.manifold.TSNE.html)

----

## Conclusions

![image](https://storage.googleapis.com/sheriff_data/clustering_results_t-SNE.png)

A y-crosstab in unsupervised learning runs what is similar to a confusion matrix with supervised learning. This contingency table tells us how many fall into the outlier category (-1), the Democratic Party (1), Independent (2), and Republican (0).

|	|-1|	0|	1|	2|
|-------|---|----|-------|-------|			
|Democratic Party|306|	0|	289|	0|
|Independent|	290|	0|	0|	375|
|Republican|	241|	867|	0|	0|

### Analyzing Clusters

The means of the DBScan clusters are shown for each feature. The difference between the means, if significant, can tell us if the y was a good choice, or if we should choose again.

* __[white_pct]__ - for counties with the ~87% white populations, the sheriff will tend to be Republican. For those that are ~82% white, the sheriff tends to be Democrat. For counties that are ~85% white, they will tend to be Independent.

* __[black_pct]__ - counties that have high black populations (~10%) will have a Democrat sheriff. A black population of ~6% are likely to have an Independent sheriff, and a black population of ~4% will have a Republican sheriff.   

* __[hispanic_pct]__ - the counties with higher Hispanic populations tend to have a Republican sheriff, followed by Independent and Democrat.

* __[amerindian_pct]__ - the counties with the highest Amerindian population tend to have Independent sheriffs.

* __[asian_pct]__ - the counties with higher Asian populations tend to vote for more Independent sheriffs. 

* __[mean_inc_pct]__ - Mean income is highest in counties with Independent sheriffs with ~3% over average, second in counties with Republican sheriffs with ~2% over average, and third in Democratic counties with ~8% under the average.

* __[mean_age_pct]__ - There is a similar pattern across income and age. The highest age seem to be Independent counties, followed by Republican and then Democratic counties. It is interesting to note that all of these counties have ages higher than the mean, while the outliers are younger counties.

* __[vacancy_pct]__ - When homes have a high share of being empty (vacant), the sheriff tends to be Independent. 

* __[nonfamily_pct]__ - People who are not part of a family unit (ie, unmarried couples, single people) tend to have Democrat sheriffs. 

* __[mobile_homes_pct]__ - Counties with a high number of households being mobile homes or trailerhave a higher likelihood of Democrat sheriffs. 

* __[unemployed]__ - Unemployment is highest in counties with Democrat sheriffs.

* __[no_degree]__ - There are 3% more people without degrees in counties with Democrat sheriffs than Republican or Independent counties.

* __[owner_pct]__ - The counties with Republican sheriffs have the most home ownership, followed by Independent, then Democrat.

* __[armed_forces_pct]__ - The highest percentage of people in the armed forces are in Republican-sheriff counties, followed by Independent, then Democrat counties.

### Metrics

For scoring, I compared K-Means and DBScan on non-winsorized and winsorized data: 

* Adjusted rand-index score of the K-Means solution: 0.0632480796488733
* The silhouette score of the K-Means solution: 0.14460997927860114
* Adjusted Rand Index of the DBSCAN solution: 0.4867411296451129
* The silhouette score of the DBSCAN solution: 0.01937317159934826
* Adjusted Rand Index of the winsorized DBSCAN solution: 0.07348290490619522
* The silhouette score of the winsorized DBSCAN solution: 0.25825599856499887


----

## Questions/Comments

Any contributions are more than welcome!

Feel free to leave me a message on Git or email me at mcclure.dean@gmail.com


