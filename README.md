## Wafer Fault Detection

#### Problem Statement:
 
To build a classification methodology to predict the quality of wafer sensors based on the given training data
   
The inputs of various sensors for different wafers have been provided. In electronics, a wafer (also called a slice or substrate) is a thin slice of semiconductor used for the fabrication of integrated circuits
There are two classes: +1 and -1.

    +1: Means that the wafer is in a working condition and it doesn't need to be replaced.

    -1: Means that the wafer is faulty and it needa to be replaced.
    
    
### Data Description
    
The client will send data in multiple sets of files in batches at a given location.
Data will contain Wafer names and 590 columns of different sensor values for each wafer.
The last column will have the "Good/Bad" value for each wafer.

Apart from training files, we laso require a "schema" file from the client, which contain all the
relevant information about the training files such as:

Name of the files, Length of Date value in FileName, Length of Time value in FileName, NUmber of Columnns, 
Name of Columns, and their dataype.
    
### Data Validation

In this step, we perform different sets of validation like filename validation, number of columns, name of the columns,data type of each columns and other kind of validations


### Data Insertion in Database
     
All the files in the "Good_Data_Folder" are inserted in the Database table. If any file has invalid data type in any of the columns, the file is not loaded in the table and is moved to "Bad_Data_Folder".

     
### Model Training
    
Data Export from Db: The data in a stored database is exported as a CSV file to be used for model training.

Data Preprocessing: 
Check for null values in the columns. If present, impute the null values using the KNN imputer.

Check if any column has zero standard deviation, remove such columns as they don't give any information during 
model training.

Clustering: KMeans algorithm is used to create clusters in the preprocessed data. The optimum number of clusters 
is selected


## Create a file "Dockerfile" with below content

```
FROM python:3.7
COPY . /app
WORKDIR /app
RUN pip install -r requirements.txt
ENTRYPOINT [ "python" ]
CMD [ "main.py" ]
```


    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
     
    
     
    
