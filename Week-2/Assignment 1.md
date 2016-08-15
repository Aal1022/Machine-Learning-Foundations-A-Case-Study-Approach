+ 1. Selection and summary statistics: We found the zip code with the highest average house price. What is the average house price of that zip code?

sales = graphlab.SFrame('home_data.gl/')

high = sales[sales['zipcode'=='98039']]

high['price'].mean()

2160606.5999999996

+ 2. Filtering data: What fraction of the houses have living space between 2000 sq.ft. and 4000 sq.ft

inRange = sales[(sales['sqft_living']>=2000) & (sales['sqft_living']<=4000)]

inRange.num_rows()
9221

sales.num_rows()
21613

42.66%


+ 3. Building a regression model with several more features: What is the difference in RMSE between the model trained with my_features and the one trained with advanced_features?

my_features = ['bedrooms', 'bathrooms', 'sqft_living', 'sqft_lot', 'floors', 'zipcode']
my_features_model = graphlab.linear_regression.create(train_data,target='price',features=my_features,validation_set=None)
print my_features_model.evaluate(test_data)
{'max_error': 3486584.5093818405, 'rmse': 179542.4333126907}

advanced_features = ['bedrooms', 'bathrooms', 'sqft_living', 'sqft_lot', 'floors', 'zipcode','condition', 'grade','waterfront','view','sqft_above','sqft_basement','yr_built','yr_renovated','lat','long','sqft_living15','sqft_lot15']
adv_features_model = graphlab.linear_regression.create(train_data,target='price',features=advanced_features,validation_set=None)
print adv_features_model.evaluate(test_data)
{'max_error': 3556849.413849746, 'rmse': 156831.1168020198}

difference:22711







