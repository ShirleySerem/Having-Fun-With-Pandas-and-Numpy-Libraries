# Having-Fun-With-Pandas-and-Numpy-Libraries

## Description
A repository with simple dataset to have fun :feelsgood: and practice Pandas and Numpy Libraries.

## Project Context
This is a project that was done to just give a feel of how Pandas and Numpy libraries funtion within Python. 


## Analysis Tasks
Step 1: Create a DataFrame from the list of dictionaries below:
[{'product_id':23, 'name':'computer', 'wholesale_price': 500, 'retail_price':1000,
'sales':100}, 
{'product_id':96, 'name':'Python Workout', 'wholesale_price': 35,'retail_price':75,
'sales':1000},
{'product_id':97, 'name':'Pandas Workout', 'wholesale_price': 35, 'retail_price':75,
'sales':500},
{'product_id':15, 'name':'banana', 'wholesale_price': 0.5,'retail_price':1,
'sales':200},
{'product_id':87, 'name':'sandwich', 'wholesale_price': 3,'retail_price':5, 'sales':300}]


Step 2: Calculate the Total Profit for each product using the formula

**net_revenue_per_product = (retail_price - wholesale price) * sales**

Step 3: Determine the following
- How much total net revenue was received from all of these sales?
- What product is product retail price more than twice the wholesale price?
- How much did the store make from food vs. computers vs. books?
- Because your store is doing so well, you’re able to negotiate a 30% discount on
the wholesale price of goods. Calculate the new net revenue

## Code Explanation
We first import the libraries needed for this analysis
>#importing pandas and numpy
>
>`import pandas as pd`
>
>`import numpy as np`

**STEP 1: We create a dictionary, then a dataframe.**

>#creating a sales report dictionary
>
>`sales_report ={`
>
>>`'products_id'  :[23,96,97,15,87],`
>
>>`'name'  :['computer','python workout','pandas workout','banana','sandwich'],`
>
>>`'wholesale_price':[500,35,35,0.5,3],`
>
>>`'retail_price':[1000,75,75,1,5],`
>
>>`'sales': [100,1000,500,200,300]`
>
>`}`
>
>#creating a dataframe from out of the dictionary
>
>`df =pd.DataFrame(sales_report)`
>
>`df`

>#setting the name column  as the  index of our dataframe
>
>#setting inplace as true in order to set the changes permanent in the dataframe
>
>`df.set_index('name',inplace=True)`
>
>`df`


**STEP 2: Calculating Total Profit**
>#calculating the total revenue for all products
>
>`df['net_revenue_per_product'].sum()`

**STEP 3**
>**a. What product is product retail price more than twice the wholesale price?**
>
>#getting the products with retail_price twice greater than wholesale_price using boolean filtering
>
>`filt=(df['retail_price'] >2*df['wholesale_price'])`
>
>#filtering the variable filt to get results from our dataframe
>
>#brings out the exact product affected with boolean filter
>
>`df[filt]`

>**b. How much did the store make from food vs. computers vs. books?**
>
>#how much the store makes from food(banana and sandwhich), computers and books(python workout and pandas workout)
>
>`food =df.loc['banana','net_revenue_per_product'] + df.loc['sandwich','net_revenue_per_product']`
>
>`computer=df.loc['computer','net_revenue_per_product']`
>
>`books=df.loc['python workout','net_revenue_per_product'] + df.loc['pandas workout','net_revenue_per_product']`
>
>`print(f' The store made {food} from food, {computer} from computer and {books} from books')`

>**c. Because your store is doing so well, you’re able to negotiate a 30% discount on
the wholesale price of goods. Calculate the new net revenue.**
>
>#calculating new_wholesale_price after getting a discount
>
>`discount_on_wholesale_price= 30/100 * df['wholesale_price']`
>
>`new_wholesale_price = df['wholesale_price'] - discount_on_wholesale_price`
>
>#calculating the new revenue after getting the wholesale discount
>
>`df['new_net_revenue']=(df['retail_price']-new_wholesale_price)*df['sales']`
>
>`df`
## Author
Shirley Serem
