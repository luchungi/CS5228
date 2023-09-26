# Data Fields
* **rent_approval_date** - year and month when the rent was approved as string, e.g., "2021-01" representing January 2021
* **town** - the town of the sold HDB flat (e.g., "Bishan", "Queenstown", "Clementi")
* **block** - block number of the flat (e.g., "300", "306A", "254")
* **street_name** - street name of block containing the flat (e.g., "ubi avenue 1", "woodlands drive 14")
* **flat_type** - type of flat (e.g., "2 room", "3 room", "4-room")
* **flat_model** - model of the flat (e.g., "model a", "dbss", ''executive")
* **floor_area_sqm** - floor area in square meter (e.g., 104.0, 74.0, 136.0)
* **furnished** - indicator if flat is furnished ("yes" or "no")
* **lease_commence_date** - year the lease for flat commenced (e.g., 1984, 1985, 1986)
* **latitude** - latitude of block containing the flat (e.g., 1.328805)
* **longitude** - longitude of block containing the flat (e.g., 103.74502)
* **elevation** - elevation of block containing the flat in meter (e.g., 30)
* **subszone** - subzone of block containing the flat in meter (e.g., "blangah rise", "marymount")
* **planning_area** - planning area of block containing the flat (e.g., "woodlands", "bukit merah")
* **region** - region of block containing the flat in meter (e.g., "west region", "north region")
* **monthly_rent** - rental rate SGD (e.g., 2350, 4000, 3200)

# How to handle each attributes?

numeric variables = ['block', 'floor_area_sqm', 'lease_commence_date', 'latitude', 'longitude']

categorical variables = ['rent_approval_date', 'town', 'street_name', 'flat_type', 'flat_model', 'furnished', 'subzone', 'planning_area', 'region']

* **rent_approval_date** - ordinal encoding
* **town** - one hot encoding
* **block** - remove the suffix to make it completely numeric? (does this attribute really matter?) (could be useful for decision tree)
* **street_name** - target encoding because there are too many unique values for this attribute (or we simply drop it)

* **flat_type** - ordinal encoding
* **flat_model** - ordinal encoding? (not sure if there is ordinal relationship for this one)

* **floor_area_sqm** - normalization
* **furnished** - removed (all the value is "yes")
* **lease_commence_date** - ordinal encoding (has been converted to new feature 'age' in another jupyter notebook)
* **latitude** - normalization
* **longitude** - normalization
* **elevation** - removed (all the value is "0")
* **subszone** - not sure what kind of encoding to apply, I think it also depends on the model we are going to use. (hard to decide personally as this one is hierarchical)
* **planning_area** - this attribute is almost the same as town, in my opinion we should keep this one and drop the "town" as the value in "town" can be the concatenation of two towns (e.g. kallang/whampoa) which doesn't exist in "planning are". (open to discussion)
* **region** - one hot encoding
* **monthly_rent** - our target attribute

## It seems like theres no missing value in the main dataset and all the numeric values are on the same scale.
