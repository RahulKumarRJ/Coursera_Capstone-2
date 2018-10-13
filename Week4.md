# Relocating to Another City: Where Could Be My Next Hometown?
Thinh Nguyen-Vo
School of Interactive Arts + Technology, Simon Fraser University, BC, Canada
tnguyenv@sfu.ca


# Abstract

For several reasons, especially business, many people have to relocate. Most of the time, people know their target city (or area of cities), but have to spend lots of time on researching where exactly they should live. In other words, they need to survey which neighbourhood in the large city might fit themselves and their habits. Here, I propose a recommendation model that analyzes and clusters neighbourhoods of a target city into multiple groups with different characters; and compare them with one’s current neighbourhood, in order to recommend those in the target city that are most similar to one’s hometown. In in this project, we would apply the DBSCAN algorithm in neighbourhoods clustering.


# I. Introduction

Relocation has never been an easy decision for anyone. It usually takes time for researching with unstructured information on the Internet. Thanks to advancements in data science, many models and libraries are now available for building such systems that can help people shorten and prioritize the list of neighbourhoods of interest, hence reduce the task load and increase the efficiency. 

In order to illustrate the problem, we will take a specific case as an example: Andy has lived in Vancouver for 25 years of his life, currently, he graduated from his grad school and looked for a data scientist position. He finally got an offer, however, the company bases in Toronto. He decided to relocate to Toronto for something new. The question here is that where exactly he could live in that big city.

![](https://d2mxuefqeaa7sj.cloudfront.net/s_1454ED3EC8D03710AF713D45EEDCB5FE310EE2ED7C7A5681FCBCA5FCEAF5E005_1539418630903_Fig1.png)


One of the concern of Andy is that he also loves his hometown so much and really wants something similar that could help him to be less homesick. In order to determine the similarity, we will need to somehow describe each neighbourhood as a numerical vector then apply some machine learning technique, e.g., DBSCAN, to cluster them into different groups.

![](https://d2mxuefqeaa7sj.cloudfront.net/s_1454ED3EC8D03710AF713D45EEDCB5FE310EE2ED7C7A5681FCBCA5FCEAF5E005_1539418255332_Fig2.png)


This problem is not restricted to this example but has wider applications in different situations. For example, if a restaurant decides to open another branch somewhere on the other side of the city, they might also need to find a similar neighbourhood, because there are always interactive effects between stores. For instance, Starbucks usually opens their stores nearby shopping areas or even inside shopping malls, because customers tend to drink something after hours of shopping; or 7Eleven tends to open their stores close to public areas such as train station, universities, or offices. Finding similar neighbourhood has a wide application to several situations in the real world.


## 1. Dataset and Feature Vector

Fortunately, FourSquare offers free APIs for developers to access their database of venues. Each venue in their dataset is usually categorized into a venue category, which is described in their [Developers Docs](https://developer.foursquare.com/docs/resources/categories). There are 10 main categories, each includes 5-91 subcategories which explicitly describe the venue, e.g., Sushi Restaurant or Fishing Store:


1. Arts & Entertainment (36)
2. College & University (23)
3. Event (12)
4. Food (91)
5. Nightlife Spot (7)
6. Outdoors & Recreation (62)
7. Professional & Other Places (41)
8. Residence (5)
9. Shop & Service (145)
10. Travel & Transport (34)

In order to predict the cluster for a neighbourhood in Vancouver while the model has been trained using data of Toronto’s neighbourhoods, we have to be careful with the feature vector:

- They must have the same length (train set vs. test set).
- All component must be consistently in the same order.

Here, we use a vector of 456 components, respectively to 456 subcategories, each illustrates the number of venues in that category. Hence, we have a histogram of venue categories for every neighbourhood.


![](https://d2mxuefqeaa7sj.cloudfront.net/s_1454ED3EC8D03710AF713D45EEDCB5FE310EE2ED7C7A5681FCBCA5FCEAF5E005_1539426418823_Unknown-3.png)



## 2. Density-Based Spatial Clustering of Applications with Noise (DBSCAN)

KMeans and DBSCAN are two of the most popular unsupervised algorithms that we can apply to solve the current problem. Though each has its own pros and cons, I decided to use DBSCAN here as we have very little knowledge about the number of clusters for a big city like Toronto, hence coming up with a certain number could be very difficult.

DBSCAN does not require specifying the number of clusters, however, it might be much slower than KMeans and also requires a careful selection of parameters. Density clustering algorithms including DBSCAN use the concept of reachability, that is how many neighbors has a point within a radius. Hence, they seem to be more corresponding to human intuition of clustering. 

In below sections, the detailed methods, results and discussion will be presented. Note that these parts will only be updated in the next week (week 5 of the Capstone project).



