# Project-3-Airbnb-Pricing
Machine Learning final project by Daniel Parmet 5/7/2019 Version 1.0.

Airbnb discussing their algo: https://www.vrmintel.com/inside-airbnbs-algorithm/
Airbnb discussing the data science in general: https://www.datacamp.com/community/podcast/data-science-airbnb


AirBnB reservation price is based on following costs (according to AirBnB official website information: https://www.airbnb.com/help/article/125/how-is-the-price-determined-for-my-reservation?locale=en):

    Costs determined by the host:
        Nightly price: Nightly rate decided by the host;
        Cleaning fee: One-time fee charged by some hosts to cover the cost of cleaning their space;
        Extra guest fees: One-time fee charged by some hosts to cover other costs related to using their space;
    Costs determined by Airbnb: Airbnb service fee;
    Other costs that may be included: currency exchange fees, VAT, other local taxes etc.



Outline:
Primary goal is to learn machine learning algos.
Project: 
My plan is to use the Kaggle dataset found here: data.insideairbnb.com/united-states/dc/washington-dc/2015-10-03/data/listings.csv.gz that is a web scraped dataset from 10/3/2015.
My goal is to test various machine learning models to see if I can A) correctly predict price B) Find reasonable price segmentation among the offerings C) Identify areas where more revenue could be generated by hosts and Airbnb and optionally if there is time to do D) Web scrape a 2019 data set (or use someone else’s code) to compare the models built to use 2015 data vs. 2019 data.
My steps are going to be:

•	Data Preprocessing & cleaning

•	Initial exploration with linear regression to test feature selection and correlation among variables

•	Then move to more formal models along
The three-four regressions:

•	Logistic

•	Lasso

•	Ridge

•	I want to run a decision tree on a slice of zipcode data to see if that can take the bias of location out of the picture.

•	Random Forest

•	KNN (attempt to identify price segmentation)

•	Clustering (attempt to identify price segmentation)

My hypothesis is that Airbnb’s own price recommendation algorithm in use in 2015 was weak. Therefore, due to the Sherman Anti-Trust act, the newness of Airbnb and lack of both government regulation and Airbnb’s ability to predict and suggest prices, I expect to see more over and underpriced options done by hosts. I expect to find numerous opportunities to present price segmentation and revenue enhancement. Although, those opportunities likely exist because of the hosts setting their own price without data. Therefore, I expect to achieve fairly poor predictions from any ML. If I get the chance to create or obtain a 2019 dataset for time series comparison, I am almost the complete opposite results due to government regulation, growth and awareness of Airbnb and its’ ability to recommend more regularized price recommendations to their hosts.
Since none of the data accounts for photos placed on the offerings, I expect to see poor prediction results of price.

Results:
I achieved .55298 from a random forest model which is a bit short of the .60 I was hoping to achieve. The results are lackluster.
However, the project was a success in the sense that it shows there is a clear option to improve revenue along the lines of Entire Home vs Room rentals.
It's very clear that the airbnb algo at the time was near useless for room results and thus the hosts were all over the place.
It became clear with early tests that clustering and KNN were not useful with this particular dataset so focus became around variations of Regression and Random Forest.

Conclusions:
This dataset was the DC area. 
1) Minimum nights apparently has nothing to do with price.
2) Accommodates is correlated with beds and bedrooms but it drives the price less.
3) Superhost seems to matter and is worth testing more.


Log of steps taken:
First examined what I had in data
Second I went through to think about what factors might effect price and price segmentation drew some hypothesises
Third Look at NAN
Fourth went through doing data cleaning
Fifth went ahead and created a golden database dropping the few NANs
Sixth did some variant tests on both LR, RF and KNN
7th Returned to examine intercept / correlation closely
8th Ran correlation variations on accommodates, beds, bedrooms. Bedrooms won 15% most valuable variable
9th created comfort variation out of that and tested it. Useless.
10th Revisited idea around room_type as its own data set without dummy variable. Major success Entire home runs!
11th Tested availability a30 vs a60 vs a90 vs a365
12th a30 won so added it to the best case Entire Room, Accommodates: SUCCESS .411 from initial 32.64
13th Created function and refactored code
14th new drawing board on ideas and a view simple visuals to help me understand what was going
15th fixed beds bug
16th Dropped High prices that were throwing it off to run Random Forest
17th ran city vs zipcode. City determined nothing so dropped.
18th Travis on price per person
19th dummy variable beds+ba
20th for loop Visualizations on each component...
21st Reporting Log Results and print (.append?)
22nd drop max minimum nights to 31 because one result had a 180 night minimum.
23rd created heatmap for correlations
24th created more visualizations
25th dropped minimum_nights due to heatmap correlations

What I would do next time:
1. Test PCA (Principal Component Analysis)
2. Use a more modern dataset from http://insideairbnb.com/
3. If I had used insiderairbnb data (found it sooner rather than the kaggle dataset...) I would have had more robust data like: reviews, calendars which allows me to set for cleanliness data and other factors hosts get rated on as well as test for seasonality time series data. Undoubtedly a more complex problem but I would have expected better results.
4. I would refactor my cleanup and EDA code to work better.
5. I think there is a definite opportunity to do NLP on reviews to see how better or worse reviews drive more price.
6. I would add more visualizations (time restrictions, short project)
7. Certainly Airbnb's own conclusiosn 10 years ago were not suprising: PHOTOS PHOTOS PHOTOS. I would attempt to build an image classifier to see what results might be based on listings' photos.
8. Further diving into room rental 
