# **ModelsSimulation1ProyectIA**

## Proyect for curse Model 1

---

## **Uber Fares Prediction**

## **Student:**

* Luis Felipe Cadavid Chica  CC: 98711955

## **Dataset:**

Uber Fares Dataset \
<https://www.kaggle.com/datasets/yasserh/uber-fares-dataset>

I based myself on the model built by Anjali Singh (anjali1510) \
<https://www.kaggle.com/code/anjali1510/uber-fare-prediction>

## PHASE 1

---
In the phase-1 folder, there are the files that in summary correspond to the selection of the dataset, the data analysis, the testing of different models and the saving of the selected model 'Gradient Boosting Regressor'.

## PHASE 2

---
There is a set of folders and files where we can find,
data: where files with a csv extension are saved, which are used to train the model and make predictions.

model: Folder where the pkl are located, created by the picklet library to use them from the predict.py file and make the predictions from the file found in the data folder.

src: In this folder you will find the files with python code that allow you to train the model and predict.

Dockerfile: File with which a container is built with the instructions to run the project in a new instance.

Requirements.txt: File that contains all the libraries that will be used in the python scripts found in src.

### How to run the container

Open a terminal in the main project directory (fase-2) and run the following commands:

* docker build -t model_fare_amount .
* docker run -v $(pwd)/models:/app/models -v $(pwd)/data:/app/data model_fare_amount

Please note that the file located in data, which will be used to train the model, must have the following characteristics:

### INFORMATION RELATED TO PERIOD

    'Early Morning' : 1,
    'Morning'       : 2,
    'Noon'          : 3,
    'Evening'       : 4,
    'Night'         : 5,
    'Late Night'    : 6.

### INFORMATION RELATED TO MONTH

    'January'       : 1, 
    'February'      : 2, 
    'March'         : 3, 
    'April'         : 4,
    'May'           : 5,
    'June'          : 6,
    'July'          : 7,
    'August'        : 8,
    'September'     : 9, 
    'October'       : 10, 
    'November'      : 11, 
    'December'      : 12.

### INFORMATION RELATED TO WEEK DAY

    'Monday'        : 1,
    'Tuesday'       : 2,
    'Wednesday'     : 3,
    'Thursday'      : 4,
    'Friday'        : 5,
    'Saturday'      : 6,
    'Sunday'        : 7.

### INFORMATION RELATED TO YEAR

    2009            : 1,
    2010            : 2,
    2011            : 3,
    2012            : 4,
    2013            : 5,
    2014            : 6,
    2015            : 7.

## PHASE 3

---
In this phase of the project, an API Rest has been built with the help of the Python framework, FastApi, which in addition to allowing two Endpoint:
**localhost:8000/predict**
**localhost:8000/train**

It is also possible to observe from its automatic documentation with Swagger: **localhost/8000/docs**, all the details offered by the endpoints.

The structure of the project is as follows:
![Alt text](image-1.png)

The Apirest.py file is in charge of creating the API and giving access to the different endpoints,

In the predict endpoints, a file with CSV extension is requested, where the data is loaded to generate the desired prediction, through the previously loaded model located in the Models folder.

In the Endpoints Train, a file with CSV extension is entered, with which the model will be trained again and the PKL files will be saved in the Models folder.

### Execute the server:

The Dockerfile file, continues all the instructions for the container to run after entering the following commands:

* **docker build -t phase3 .**
* **docker run -p 9000:9000 phase3**

![Alt text](image-6.png)

To easily test the /predict endpoint, use tools like curl or httpie from the command line, or you can use a graphical interface like Swagger UI provided by FastAPI.

you can test the /predict endpoint with curl from the command line:
* curl -X POST "http://localhost:9000/predict" -H "accept: application/json" -H "Content-Type: multipart form-data" -F "file=@/ruta/del/archivo.csv"

When opening the local direction in the browser: 9000/docs

![Alt text](image.png)

In Docs, we can see that if we give it in the "Try It Out" button, it gives us the possibility of opening the file to which we want to predict

![Alt text](image-2.png)

![Alt text](image-3.png)

![Alt text](image-4.png)

Then it gives you in the Execute button and you will get the result of the prediction:

![Alt text](image-5.png)

The same process for Train.
