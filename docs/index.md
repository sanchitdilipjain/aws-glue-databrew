## AWS Glue Databrew

**Introduction**

- AWS Glue DataBrew is a new data preparation tool that simplify the cleansing and normalising the data to prepare it for analytics and machine learning for data analysts and data scientists
- It provides over 250 transformations, no-code blueprint out of the box to automate the preparation tasks. Post the data is in good shape, we can use it for analytics and ML tasks. And the pricing model is also pay for what you use - no upfront commitment.

**Tutorial**

- Step 1 : Prerequisite  

  -  Download the <a href="https://github.com/sanchitdilipjain/aws-glue-databrew/blob/main/dataset.csv">dataset</a> from this link and upload to S3 bucket
  
  -  Download the <a href="https://github.com/sanchitdilipjain/aws-glue-databrew/blob/main/cloudformation.json">cloudformation template</a> from this link and Deploy it
  
  -  Once the Cloudformation stack is deployed successfully please capture the values for RoleName and S3Bucket details
      
      <img src="images/image1.png" class="inline"/> 

- Step 2 : Working with Glue Databrew
  
  In this section, we will be working with AWS Glue Databrew and this section is divided into below parts
  
    - Creating a project
    - Exploring the dataset
    - Preparing the dataset
    - Creating a DataBrew job
    - Viewing data lineage

- Step 2.1 : Creating a project

    1. Traverse to the AWS Glue DataBrew service

       <img src="images/image2.png" class="inline"/> 

    2. From the DataBrew console, select Projects

       <img src="images/image3.png" class="inline"/> 

    3. Select Create project

    4. In the Project details section, provide the project name 

       <img src="images/image4.png" class="inline"/> 

    5. In the Select a dataset section, select New dataset and provide a name to it

       <img src="images/image5.png" class="inline"/> 

    6. Under the Connect to a new dataset section, click Amazon S3 under “Data lake/data store”

       <img src="images/image6.png" class="inline"/> 

    7. Under the Sampling, leave the default configuration values

       <img src="images/image7.png" class="inline"/> 

    8. Under the Permissions section, select the role DataBrew-DataBrewLabRole--xxxxx from the drop-down list 

       <img src="images/image8.png" class="inline"/> 

       **Note:** This role name should match to the one we deployed via Cloudformation in the prerequisite section

    9. Select Create project

       <img src="images/image9.png" class="inline"/> 

- Step 2.2 : Exploring the dataset

- Step 2.3 : Preparing the dataset

- Step 2.4 : Creating a DataBrew job

- Step 2.5 : Viewing data lineage
