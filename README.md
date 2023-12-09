# Load_prediction_app

## Objective
This machine learning project aims to create a robust ML model and a corresponding web application for status of loan approval process. The goal is to use this system to classify loan applicants, determining whether they should be granted a loan or not.

## Evaluation Criteria
Submissions will be assessed based on the F1 Score, ensuring the effectiveness of the model in accurately classifying loan applicants.

## Data
About the Data
The dataset comprises information about loan applicants, encompassing 12 independent columns and 1 dependent column. Notable attributes include Loan ID, gender, marital status, education level, applicant's income, and more.

## Dataset
Train and test datasets are provided in repo.

## Data Description
* Loan_ID: A unique identifier assigned to each loan applicant.
* Gender: Gender of the applicant (Male, Female).
* Married: Marital status of the applicant (Yes, No).
* Dependents: Number of people dependent on the applicant (0, 1, 2, 3+).
* Education: Education level of the applicant (Graduated, Not Graduated).
* Self_Employed: Indicates if the applicant is self-employed (Yes, No).
* ApplicantIncome: The amount of income the applicant earns.
* CoapplicantIncome: The amount of income the co-applicant earns.
* LoanAmount: The amount of loan the applicant has requested.
* Loan_Amount_Term: The number of days over which the loan will be paid.
* Credit_History: A record of a borrower's responsible repayment of debts (1 - all debts paid, 0 - not paid).
* Property_Area: The type of location where the applicant’s property lies (Rural, Semiurban, Urban).

Target:
* Loan_Status: Indicates whether the loan was granted or not (Y, N).

## Deployment
Executed in Google cloud console using docker containers and Google Kubernetes Engine
Run commands in Active cloud shell

Follow the commands on gcp cloud shell
1.	Clone Git repository: git clone https:
* //github.com/T-ushita/Load_prediction_app
3.	Change the directory to Loan Prediction App:
* cd Load_prediction_app/
5.	Set Project ID Environment Variable:
* export PROJECT_ID=assignment_project
7.	Build Docker Image:
* docker build -t gcr.io/${PROJECT_ID}/loan_prediction-app:v1
9.	View Docker images:
* docker images
11.	Authenticate Container registry and Upload the container image:
* gcloud auth configure-docker
* docker push gcr.io/${PROJECT_ID}/loan_prediction_app:v1
8.	Create Cluster:
* gcloud config set project $PROJECT_ID 
* gcloud config set compute/zone us-central1
* gcloud container clusters create prediction-cluster --num-nodes=2
10.	Deploy Application: 
* kubectl create deployment prediction-app --image=gcr.io/${PROJECT_ID}/prediction-app:v1
11.	Expose application to internet:
* kubectl expose deployment prediction-app --type=LoadBalancer --port 80 --target-port 8080
* kubectl get service
