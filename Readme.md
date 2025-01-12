**This article provides a step by step process to build a solution to collect weather data and store it in S3 bucket for various locations.**

**Software Access needed to get this project done**

          Visual studio code
          
          GitHub
          
          Free Tier AWS account
          
          Python and PIP libraries installed (I used Python 3.12.8 and PIP - 24.3.1)
          
          Open Weather API keys -Free of cost https://openweathermap.org/api
          
          ChatGPT for help to debug/troubleshoot. Its free use it :-)



****Verify python and PIP are installed correctly ****
Use below commands to validate. Both the commands should list versions, If not then you did not install them correctly. 

Note: Make sure installation path is added to your env variables on your workstation.

      Python --version

      PIP --version

**Folder Structure in VS Code/GitHub**
    Weather-DataCollection >

        data - to store the results

        Src  -  Contains the source code

        test  - Any test scripts used for testing. 

**Within the src folder create two files **

      1. python init file -  This makes the source folder a python library.
      
         touch --init__.py
      
      2. weather_dashboard.py - This is where all the python code is written
      
         touch weather_dashboard.py

**Within the Weather-DataCollection directory create Readme, .env, .gitignore and requirements file to list dependencies of the project.**

      touch readme.md
      
      touch requirements.txt  - This files contains the python libraries 
      
      touch .gitignore - The file contains the parameters or file name that should be excluded when changes are committed in GitHub. For example .env files are used to store API secret keys which are not meant for outside world to view them when we share the Git repo to public. Therefore we mention the .env in .gitignore file. 

**Add the following to requirements file so we can install these libraries via PIP install command.**

            boto3==1.26.137 

            python-dotenv==1.0.0

            requests==2.28.2

Boto3 is the official Amazon Web Services (AWS) SDK for Python. It provides an easy way to interact with AWS services.

python-dotenv is a Python library used for managing environment variables that contains secret keys

requests is one of the most popular Python libraries used for making HTTP requests


**Create an IAM user in AWS, assign policy/permissions and generate an Access Key**
For further explanation, please reference the AWS IAM user documentation.

I have created the user "awsguy", and added the policy of "Administratoraccess". This gives the user the necessary permissions to create an S3 bucket. Without proper permission you will see an error during code execution saying "not sufficient access to create a S3 bucket".

Install AWS CLI for logging into AWS console via VScode. https://aws.amazon.com/cli/

Within VScode enter below command and enter the newly created IAM user access keys 

At this point we are securely authenticating with AWS console to run the python code.

**Configure AWS credentials:**
aws configure
By this point all the directory should be setup with all the files. Now we are ready to write the python script in weather_dashboard.py file under the src/ directory.

Please check my Gitrepo for source code https://github.com/rajpola453/AWS-Projects.git 

**After the source code is ready, execute the below command to run the python script**

python src/weather_dashboard.py
    If the code runs successfully, you should see the output with weather related info for various cities/states mentioned in the source code. 
        S3 bucket will be created in AWS account that contains the JSON files.



**Learnings:**
This was my first AWS project. Though I had the book knowledge I did not have the practical project experience until I started doing the #30daysdevopschallenge

Handled secure API keys with .env

Troubleshooting PIP library dependencies

Gained hands-on experience with AWS S3 and cloud resource management

Interacting with public API's

Documentation and writing this tech article
