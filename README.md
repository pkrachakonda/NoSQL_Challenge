# Evaluation of Restaurant Ratings Using **MongoDB** and **Pymongo**
  As part of this project, database related to restaurants across the United Kingdom was evaluated.
  
### Step 1: Importing Dataset and Setup of Collection
The provided restaurants datasets in json format was imported to Mongo database as *'uk_food'* and saved with a collection name as *'establishments'* using the below command:

*"mongoimport --type json -d uk_food -c establishments --drop --jsonArray establishments.json"*

![Screenshot 2023-10-11 205756](https://github.com/pkrachakonda/NoSQL_Challenge/assets/20739237/cc569e82-5ec2-4146-b98c-aadf25683e06)

After importing the required dependencies, a connection to MongoDB is made and all the existing *databases* as well as *collections* in the MongoDB are listed. Using *find_one()* function one of the document of the ***establishments*** collection is reviewed, in order to confirm that all documents are imported properly.

![Screenshot 2023-10-11 210948](https://github.com/pkrachakonda/NoSQL_Challenge/assets/20739237/e92ce132-7211-491d-ac8d-e9967799d732)


### Step 2: Adding Document to Collection and Updating fields 
As part of this process, a new document (dictionary) related *Penang Flavours* is created based on data provided in the BCS. The document is added to *establishments* collections using *"insert_one()"* function. The presence of document in collection was verified using *'find_one()'* function. **Penang Flavour** type of restaurants were compared in order to obtain the missing *'BussinessTypeID'* information from the collection. The relevant field of the restaurant was updated and verified.

![Screenshot 2023-10-11 212434](https://github.com/pkrachakonda/NoSQL_Challenge/assets/20739237/2d73affd-1c29-4209-874f-9b15e38eb6bc)
![Screenshot 2023-10-11 212450](https://github.com/pkrachakonda/NoSQL_Challenge/assets/20739237/d02fb27b-4699-4a5d-8ef0-2f46dd75c39f)
![Screenshot 2023-10-11 212548](https://github.com/pkrachakonda/NoSQL_Challenge/assets/20739237/7ffa978a-11f8-468f-ab3d-264a4cb846ab)

### Step 3: Deleting Documents from Collections

As part of this process, initially number of documents (restaurants) located in the local government area ('Dover') in the collection were estimated using *'count_documents'* function.The documents were deleted from the *establishments* collection using *delete_many()* function and the deletion process was later verified. It was also verified that deletion process did not removed documents of restaurants located in local government areas.

![Screenshot 2023-10-11 213935](https://github.com/pkrachakonda/NoSQL_Challenge/assets/20739237/bf692151-82c0-4404-b0b2-aafaa175dacb)

### Step 4: Converting Strings to other Datatypes

*Longitudes, Latitudes and Rating values* of documents were converted to **Double and Integer** respectively using *data conversion functions*. The datatype conversion were later verified.

![Screenshot 2023-10-11 220238](https://github.com/pkrachakonda/NoSQL_Challenge/assets/20739237/133187f1-b089-4ec6-aee8-b132dc2cf61c)
![Screenshot 2023-10-11 220251](https://github.com/pkrachakonda/NoSQL_Challenge/assets/20739237/69561892-6870-40a4-9c1a-b278289521d4)

## Data Analysis

Similar to previous section, all the required dependencies were imported initially, a connection to MongoDB using Pymongo functions were made. Existing list of databases as well as collections were printed to verify whether ***uk_food*** database and *establishments* collection does exist in the MongoDB.

![Screenshot 2023-10-11 222157](https://github.com/pkrachakonda/NoSQL_Challenge/assets/20739237/58b7d0e0-4b8a-4440-b600-5203db3afdbe)

### *Analysis: 1*

In order to find all the establishments with a *hygiene score* of "20", initially a query was constructed using *query* function of *Pymongo*. 

Using this query function, all documents within *establishments* collection were searched. Total number of documents that were matching with the search criteria were printed. Later the results wee converted and stored as a Pandas DataFrame.


![Screenshot 2023-10-11 223051](https://github.com/pkrachakonda/NoSQL_Challenge/assets/20739237/4961f702-a0f7-452d-b6a8-cd20ad93fa90)
![Screenshot 2023-10-11 223107](https://github.com/pkrachakonda/NoSQL_Challenge/assets/20739237/5f5c7b1d-af06-42ea-a457-15f994c0ac53)

### *Analysis: 2*

In oder to find all the establishments located in *London*, a query was built using *City of London Corporation* as *Local Authority Name'*. Also for each establishment, *rating values* were selected to be greater than or equal to 4. Similar to above analysis the *establishments* collection was initially searched with the above query and resulted were converted into a list and later into a Pandas DataFrame.

![Screenshot 2023-10-11 223809](https://github.com/pkrachakonda/NoSQL_Challenge/assets/20739237/530e86f3-0a35-4f2e-b3e5-dfc05a8d0553)
![Screenshot 2023-10-11 223822](https://github.com/pkrachakonda/NoSQL_Challenge/assets/20739237/c422deac-53b7-41d6-bf76-98945fae1b6f)

### *Analysis: 3*

In oder to find top 5 establishments with a rating value of 5 and located at a distance of 0.01 degree to *Penang Flavours*, a query was built using *Penang Flavours* co-ordinates as centre. A search distance of 0.01 degrees was used and the *establishments* collection was searched to find all matching establishments/restaurants. Rating value of 5 was also included as part of search criteria. The results which were sorted by lowest hygiene scores was converted into a list and later into a Pandas DataFrame.

![Screenshot 2023-10-11 225001](https://github.com/pkrachakonda/NoSQL_Challenge/assets/20739237/26261913-3f06-4b06-92d0-dcbf4ec8c852)
![image](https://github.com/pkrachakonda/NoSQL_Challenge/assets/20739237/9dcd1546-da4b-484c-9287-79c1a3fb10ba)


### *Analysis: 4*

In order to find establishments (restaurants) with hygiene score of "0", *pipeline* functions of aggregate were used. As part of the pipeline, a *match query* with hygiene score of "0" followed by a *group query* with *local authority name* as *id* were constructed. Finally, the query values were *sorted* based on the *group* query *count* value in descending order. The pipeline (i.e. sequence of query) was constructed and was used to query the *establishments* collection.
Similar to above analysis, results were initially were converted into list and later into a Pandas DataFrame.

![Screenshot 2023-10-11 230630](https://github.com/pkrachakonda/NoSQL_Challenge/assets/20739237/63ddc148-3510-471a-b97d-45c143de7f7e)
![Screenshot 2023-10-11 230645](https://github.com/pkrachakonda/NoSQL_Challenge/assets/20739237/a5be6e09-11c8-4872-a78a-0ec9fe83ef07)
