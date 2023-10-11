# Evaluation of Restaurant Ratings Using **MongoDB** and **Pymongo**
  As part of this project, database related to restaurants across the United Kingdom was evaluated.
  
## Step 1: Importing Dataset and Setup of Collection
The provided restaurants datasets in json format was imported to Mongo database as *'uk_food'* and saved with a collection name as *'establishments'* using the below command:

*"mongoimport --type json -d uk_food -c establishments --drop --jsonArray establishments.json"*

![Screenshot 2023-10-11 205756](https://github.com/pkrachakonda/NoSQL_Challenge/assets/20739237/cc569e82-5ec2-4146-b98c-aadf25683e06)

After importing the required dependencies, a connection to MongoDB is made and all the existing *databases* as well as *collections* in the MongoDB are listed. 

Using *find_one()* function one of the document of the ***establishments*** collection is reviewed, in order to confirm that all documents are imported properly.

![Screenshot 2023-10-11 210948](https://github.com/pkrachakonda/NoSQL_Challenge/assets/20739237/e92ce132-7211-491d-ac8d-e9967799d732)


## Step 2: Adding Document to Collection and Updating fields 
As part of this process, a new document (dictionary) related *Penang Flavours* is created based on data provided in the BCS. The document is added to *establishments* collections using *"insert_one()"* function. 

The presence of document in collection was verified using *'find_one()'* function. **Penang Flavour** type of restaurants were compared in order to obtain the missing *'BussinessTypeID'* information from the collection. The relevant field of the restaurant was updated and verified.

![Screenshot 2023-10-11 212434](https://github.com/pkrachakonda/NoSQL_Challenge/assets/20739237/2d73affd-1c29-4209-874f-9b15e38eb6bc)
![Screenshot 2023-10-11 212450](https://github.com/pkrachakonda/NoSQL_Challenge/assets/20739237/d02fb27b-4699-4a5d-8ef0-2f46dd75c39f)
![Screenshot 2023-10-11 212548](https://github.com/pkrachakonda/NoSQL_Challenge/assets/20739237/7ffa978a-11f8-468f-ab3d-264a4cb846ab)

## Step 3: Deleting Documents from Collections

As part of this process, initially number of documents (restaurants) located in the local government area ('Dover') in the collection were estimated using *'count_documents'* function.

The documents were deleted from the *establishments* collection using *delete_many()* function and the deletion process was later verified.

It was also verified that deletion process did not removed documents of restaurants located in local government areas.

![Screenshot 2023-10-11 213935](https://github.com/pkrachakonda/NoSQL_Challenge/assets/20739237/bf692151-82c0-4404-b0b2-aafaa175dacb)

## Step 4: Converting Strings to other Datatypes

Longitudes, Latitudes and Rating values of documents were converted to Double and Integer respectively using *data conversion functions*. The datatype conversion were later verified.

![Screenshot 2023-10-11 220238](https://github.com/pkrachakonda/NoSQL_Challenge/assets/20739237/133187f1-b089-4ec6-aee8-b132dc2cf61c)
![Screenshot 2023-10-11 220251](https://github.com/pkrachakonda/NoSQL_Challenge/assets/20739237/69561892-6870-40a4-9c1a-b278289521d4)

