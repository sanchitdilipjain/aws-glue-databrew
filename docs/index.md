## AWS Glue Databrew

**Introduction**

- AWS Glue DataBrew is a new data preparation tool that simplifies the cleansing and normalizing the data to prepare it for analytics and machine learning for data analysts and data scientists
- It provides over 250 transformations, no-code blueprint out of the box to automate the preparation tasks. Post the data is in good shape, we can use it for analytics and ML tasks. And the pricing model is also paid for what you use - no upfront commitment.

**Tutorial**

- Step 1: Prerequisite  

  -  Download the <a href="https://github.com/sanchitdilipjain/aws-glue-databrew/blob/main/dataset.csv">dataset</a> from this link and upload it to the S3 bucket
  
  -  Download the <a href="https://github.com/sanchitdilipjain/aws-glue-databrew/blob/main/cloudformation.json">cloudformation template</a> from this link and Deploy it
  
  -  Once the Cloudformation stack is deployed successfully please capture the values for RoleName and S3Bucket details
      
      <img src="images/image1.png" class="inline"/> 

- Step 2: Working with Glue Databrew
  
  - In this section, we will be working with AWS Glue Databrew and this section is divided into below parts
    
      - Creating a project
      - Exploring the dataset
      - Preparing the dataset
      - Creating a DataBrew job
      - Viewing data lineage

- Step 2.1: Creating a project

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

       **Note:** This role name should match the one we deployed via Cloudformation in the prerequisite section

    9. Select Create project

       <img src="images/image9.png" class="inline"/> 

- Step 2.2: Exploring the dataset 
    
    1. After the project has been configured, we will be presented with the Grid view. In this view, the data is shown in tabular format

       <img src="images/image10.png" class="inline"/> 
       
       The Grid view presents Columns in the dataset, different Data type of each column,a Summary of the range of values that have been found, and Statistical distribution for numerical columns

    2. Select the Schema tab. In this view, you will be presented with statistics about the data values in each column.

       <img src="images/image11.png" class="inline"/> 
       
       The Schema view presents the checkbox next to a column to view the summary of statistics for the column values, Toggle on/off the columns, Rename columns, Change the data type of columns and Rearrange the column order
       
    3. Select the Profile tab. In this view, you can run a data profile job to examine and collect statistical summaries about the data
    
        - Select Run data profile 
        
        - Under the job details and job run sample panels, leave the default values 
         
            <img src="images/image12.png" class="inline"/> 
        
        - Under the Job output settings section, provide the S3 bucket for storing the output 
        
        - Under the Permissions section, select the role DataBrew-DataBrewLabRole--xxxxx from the drop-down list 

             **Note:** This role name should match the one we deployed via Cloudformation in the prerequisite section
        
        - Select Create and run job
        
            <img src="images/image13.png" class="inline"/>    
        
        - Select on Jobs from the menu on the left hand side of the DataBrew console, Select on the Profile jobs tab to view the status of the profile job
            
            <img src="images/image14.png" class="inline"/>    
            
            <img src="images/image15.png" class="inline"/>    
        
        - When the profile job has successfully completed, click on View data profile

            <img src="images/image16.png" class="inline"/>    
            
            The data profile presents a summary of the rows and columns in the dataset, how many columns and rows are valid, and relationships across the columns
        
        - Select on the Column statistics tab to view a column-by-column breakdown
        
            <img src="images/image17.png" class="inline"/>    

- Step 2.3: Preparing the dataset
  
    - In this section, we will apply the different transformations to the dataset.
    
      - Rename columns
      - Change the data type of columns
      - Filled with the most frequent value
     
    1. Download the <a href="https://github.com/sanchitdilipjain/aws-glue-databrew/blob/main/recipe.json">recipe</a> from this link
    
    2. Select on Recipe from the menu on the left-hand side of the DataBrew console and click Upload Recipe
    
       <img src="images/image18.png" class="inline"/> 
    
    3. Provide below details
    
        - Recipe Name
        - Upload Recipe json script downloaded under Step 1
        - Select Create and publish recipe
        
       <img src="images/image19.png" class="inline"/>  

    4. Verify the recipe 
    
        <img src="images/image20.png" class="inline"/>  
    
    5. Now let's apply this recipe, click the project we configured now and the right side, click Import recipe 
    
        <img src="images/image21.png" class="inline"/>  
    
    6. Under Import recipe, select the recipe we configured and click Next
    
        <img src="images/image22.png" class="inline"/>  
    
    7. Select the Append option from the right side and click Next
    
        <img src="images/image23.png" class="inline"/>  
    
    8. Now let's validate the recipe and wait for all validation to be successful 
    
        <img src="images/image24.png" class="inline"/>   
    
    9. Once the validation is successful, click Import
    
        <img src="images/image25.png" class="inline"/>   
    
    10. Now you will be back to the project screen and with the recipe implied on the dataset
    
        <img src="images/image26.png" class="inline"/>   

- Step 2.4 : Creating a DataBrew job
  
    1. Select on Jobs from the menu on the left hand side of the DataBrew console

    2. Under the Recipe jobs tab, select on Create job
    
    3. Provide below details
    
        - Job Name
        - Job type
        - Select right dataset
        - Select right recipe

       <img src="images/image27.png" class="inline"/> 
     
    4. Provide valid S3 output location and leave rest all default 
     
       <img src="images/image28.png" class="inline"/> 
     
    5. Select Create and Run job
     
       <img src="images/image29.png" class="inline"/>  
     
    6. The DataBrew job is created and the job status is Running
     
       <img src="images/image30.png" class="inline"/>  
     
    7. Pause until the job has completed successfully
     
       <img src="images/image31.png" class="inline"/>  
     
    8. Post the job is completed successfully, verify the output file on the S3 Output location provided 
     
        <img src="images/image32.png" class="inline"/>  

- Step 2.5 : Viewing data lineage
 
    1. In DataBrew, navigate back to the project, select on Lineage at the top right
    
       The below view shows the origin of the data and the transformation steps that the data has been through.

       <img src="images/image33.png" class="inline"/> 
