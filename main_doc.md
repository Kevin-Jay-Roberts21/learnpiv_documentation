# Learnpiv.org Documentation
#### By: Kevin Roberts
#### Last modified: January/2023

## Introduction and Purpose

This documentation file was created to describe the code written for Learnpiv.org. Learnpiv.org is a Django-based website; 
a high-level Python web framework. The purpose of Learnpiv.org is to educate novice PIV (Particle Image Velocimetry) learners
as well as advanced PIV educators. Our driving goal is to create a user-friendly, cost-efficient environment where students, 
teachers, and all other learners can study PIV with ease. 

## Structure and Outside Sources

### Structure
The overall structure of learnpiv is shown below and is very much based off a Django Framework:

<img src="https://raw.githubusercontent.com/Kevin-Jay-Roberts21/learnpiv_documentation/main/pivdoc_images/structure1.png" height="400"/>

### Github
We use a Github repository to store all our code updates and progress. This repository is currently private, but can be accessed by 
the permission of the repository holder Kevin Roberts (kevinjrob9@gmail.com). As heroku is the host of the website, it requires
access to the information from the Github account. If one is to edit the website, one must first make changes and push them
to the github account, then afterwards push the github code to heroku. This will be shown more in depth in the following
Code Additions, Navigation and Testing section.

### AWS
AWS or Amazon Web Services, is where we keep all of our static images, videos, css, and javascript code. All of this information 
is kept in a s3 bucket called learnpiv-images. This bucket includes a static folder which holds all static and new information
that can be uploaded into the website. Additionally, the experiment images that a user creates and saves are also stored 
in this bucket. It may seem odd that the bucket holds static and non-static information, but that is just the format
of the bucket for now.

Another important note, please observe the following structure of the website, similar to what was shown above, only the 
main/ folder is expanded: 

<img src="https://raw.githubusercontent.com/Kevin-Jay-Roberts21/learnpiv_documentation/main/pivdoc_images/AWS1.png" height="400"/>

Notice how css/ and js/ are folders that are included in the code that's pushed to the github repository. These folders are
included solely to make testing javascripts functions and css styles easier. If anything in these folders is changed and
pushed to the github repository and then pushed to heroku, then the live site WILL NOT include these changes because heroku
is grabbing information from the AWS s3 bucket, and not from the folders that have been pushed. To be consistent in making 
changes to the css styles and javascript functions, it must be tested locally first (again, how to test will be shown below),
and then the developer must include these changes additionally to the s3 bucket. This must be done to make changes to the
website that are shown publicly and not just locally. In the settings.py file of the project, in the AWS information section, 
it is shown that the STATICFILES_STORAGE is connected to the AWS s3 bucket. This variable ensures that the static files 
are taken from the s3 bucket and not from the static/ folder in the project when the project is in production. To make the
website use the static information from the bucket, one must navigate into the project, activate it, and run ``python manage.py collectstatic``.
This process is shown in the figure below: 

<img src="https://raw.githubusercontent.com/Kevin-Jay-Roberts21/learnpiv_documentation/main/pivdoc_images/AWS2.png" height="600"/>

### Mailjet
Mailjet is the mailing service we chose to send emails to our users. The only types of emails that we currently send to users
include email for resetting account password, and emails to notify a user for when they've submitted a content suggestion, 
and finally an email if their suggestion was accepted or declined. Our Mailjet information can be found in the email section 
of the setting.py file, and it's usage can be found in the register/views.py file as well as the main/views.py file in the
project.

### Gmail
Coordinating with mailjet, we have created a learnpiv gmail account: learnpiv@gmail.com. This gmail account is the account that will send all
the mail to the users of the learnpiv.com website. Mailjet uses this email to send mail. As of now this is the only use for the gmail account.

### Heroku
Heroku is the host of the entire django app project. Heroku is a cloud platform as a service (Paas) that allows us to update, 
monitor, and scale the learnpiv.com application. There are a few important aspects of Heroku that we are using which I'll 
list below and explain:

#### General Information

Upon logging into the heroku account, you should see something like the following which is a list of applications. In our
case, we only have the learnpiv app: 

<img src="https://raw.githubusercontent.com/Kevin-Jay-Roberts21/learnpiv_documentation/main/pivdoc_images/heroku1.png" height="600"/>

To navigate into all the learnpiv app general information, click on the app and you will be brought to the following page: 

<img src="https://raw.githubusercontent.com/Kevin-Jay-Roberts21/learnpiv_documentation/main/pivdoc_images/heroku2.png" height="600"/>



#### Dynos

#### Postgres database

#### Environment Variables

#### Updates


### .env



## Code Additions, Navigation and Testing

(include database access through both admin and heroku terminal)
(include migrations)

(how to add/test code)
For the developer, if a change in the code is to be made, one must first have the learnpiv project cloned from the github 
repository and put somewhere on their computer. Testing to see if the website will run on their device is vital before making 
and changes. The developer must first open up a terminal and navigate to the where the learnpiv project is cloned: 

![alt text](pivdoc_images/test_code1.png)

The developer must then activate the virtual environment with the following command ``source bin/activate``, and ``cd`` 
into the pivwebsite folder: 

![alt text](pivdoc_images/test_code2.png)

Finally, to run the site locally, the user must execute the command: ``python manage.py runserver``, copy the given link,
and paste it into a browser: 

![alt text](pivdoc_images/test_code3.png)

After pasting the link into a browser, you should see the following: 

![alt text](pivdoc_images/test_code4.png)

This is a "testing version" of the website. The developer is free to create users, run experiments, and test anything in
the website. If the developer does create any users or experiments or anything that will modify the database, then the said 
data will be saved in a local database file, namely: ``db.sqlite3``. This database file is saved and pushed to github as 
we don't include it in our ``.gitignore`` file. Modifications made to ``db.sqlite3`` WILL NOT be uploaded to the database 
in heroku. Heroku uses a separate Postgres Database. Thus, when pulling from the github repository, ``dpsqlite`` may be 
edited, however the developer should not pay mind to it's edits as it's treated as a "testing database".



(heroku rollback)
(push heroku)
(how to test in local environment)


## Code Descriptions

(say that you'll go through each folder and file)

### bin/

### lib/

### pivwebsite/

### pivwebsite/main/

### pivwebsite/pivwebsite/

### pivwebsite/register/

### pivwebsite/.env

### pivwebsite/db.sqlite3

### pivwebsite/manage.py

### .gitignore

### Home.docx

### pyvenv.cfg

### Procfile

### requirements.txt 

### runtime.txt 