# Profitable App Profiles Project
This project contains data of all non-free apps available that generates revenue by in-app ads. Our goal is to sort these free aps and find the sources of revenue.

Let us first open both the files needed. The required files are `AppleStore.csv` and `googleplaystore.csv`.


```python
from csv import reader
#opening AppleStore.csv
open_file = open('AppleStore.csv')
read_file = reader(open_file)
apple = list(read_file)
apple_header = apple[0]
apple = apple[1:]


#opening googleplaystore.csv
open_file = open('googleplaystore.csv')          
read_file = reader(open_file)
google = list(read_file)
google_header = google[0]
google = google[1:]
```

Now that we've opened both the files, let us define a function `explore_data`. This function comprises of **4 parameters**, *dataset*, *start*, *end* and, *rows_and_columns*. 


```python
def explore_data(dataset, start, end, rows_and_columns=False):
    dataset_slice = dataset[start:end]    
    for row in dataset_slice:
        print(row)
        print('\n') # adds a new (empty) line after each row

    if rows_and_columns:
        print('Number of rows:', len(dataset))
        print('Number of columns:', len(dataset[0]))


```

Let's print the required results and find out the no. of rows and columns of each data set.


```python
print(google_header)
print('\n')
explore_data(google, 0, 4, True)
```

    ['App', 'Category', 'Rating', 'Reviews', 'Size', 'Installs', 'Type', 'Price', 'Content Rating', 'Genres', 'Last Updated', 'Current Ver', 'Android Ver']
    
    
    ['Photo Editor & Candy Camera & Grid & ScrapBook', 'ART_AND_DESIGN', '4.1', '159', '19M', '10,000+', 'Free', '0', 'Everyone', 'Art & Design', 'January 7, 2018', '1.0.0', '4.0.3 and up']
    
    
    ['Coloring book moana', 'ART_AND_DESIGN', '3.9', '967', '14M', '500,000+', 'Free', '0', 'Everyone', 'Art & Design;Pretend Play', 'January 15, 2018', '2.0.0', '4.0.3 and up']
    
    
    ['U Launcher Lite – FREE Live Cool Themes, Hide Apps', 'ART_AND_DESIGN', '4.7', '87510', '8.7M', '5,000,000+', 'Free', '0', 'Everyone', 'Art & Design', 'August 1, 2018', '1.2.4', '4.0.3 and up']
    
    
    ['Sketch - Draw & Paint', 'ART_AND_DESIGN', '4.5', '215644', '25M', '50,000,000+', 'Free', '0', 'Teen', 'Art & Design', 'June 8, 2018', 'Varies with device', '4.2 and up']
    
    
    Number of rows: 10841
    Number of columns: 13


We see that the Google Play data set has `10841 apps` and `13 columns`. Useful ones for the purpose of our analysis are '`App`', '`Category`', '`Reviews`', '`Installs`', '`Type`', '`Price`', and '`Genres`'.

Now let's take a look at the Apple App Store data set.


```python
print(apple_header)
print('\n')
explore_data(apple, 0, 3, True)
```

    ['id', 'track_name', 'size_bytes', 'currency', 'price', 'rating_count_tot', 'rating_count_ver', 'user_rating', 'user_rating_ver', 'ver', 'cont_rating', 'prime_genre', 'sup_devices.num', 'ipadSc_urls.num', 'lang.num', 'vpp_lic']
    
    
    ['284882215', 'Facebook', '389879808', 'USD', '0.0', '2974676', '212', '3.5', '3.5', '95.0', '4+', 'Social Networking', '37', '1', '29', '1']
    
    
    ['389801252', 'Instagram', '113954816', 'USD', '0.0', '2161558', '1289', '4.5', '4.0', '10.23', '12+', 'Photo & Video', '37', '0', '29', '1']
    
    
    ['529479190', 'Clash of Clans', '116476928', 'USD', '0.0', '2130805', '579', '4.5', '4.5', '9.24.12', '9+', 'Games', '38', '5', '18', '1']
    
    
    Number of rows: 7197
    Number of columns: 16


On analysis, we can see that we have `7197 iOS apps` in this data set, and the columns that seem interesting are: `'track_name'`, `'currency'`, `'price'`, `'rating_count_tot'`, `'rating_count_ver'`, and `'prime_genre'`. 
