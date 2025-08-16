# image-converter-web 
![image alt](https://github.com/Bala-6478/Image_Converter_Online/blob/main/Image%20Converter.png)


Overview of the Process
Prepare Project Files: We need to add two files (requirements.txt and .gitignore) to tell the server what software your project needs and which files to ignore.

Upload to GitHub: You'll put your project into a GitHub repository, which is a standard way to manage code.

Deploy on Render: You will create a free Render account, connect it to your GitHub, and tell it how to run your app.

## Step 1: Prepare Your Project for Production
Before uploading, we need to make a few small but crucial additions to your project folder.

1. Create requirements.txt
This file lists all the Python libraries your project needs to run. The web server will use this file to install them automatically.

Create a new file named requirements.txt in your main project folder (image_converter_web/) and add the following lines. This includes Flask, Pillow for image processing, and Gunicorn, a server needed to run a Flask app in production.

Plaintext

# requirements.txt
Flask
Pillow
gunicorn
2. Create .gitignore
This file tells Git (the software used by GitHub) to ignore certain files and folders that shouldn't be uploaded, like the temporary uploads folder.

Create a new file named .gitignore in the same folder and add the following:

Plaintext

# .gitignore
uploads/
__pycache__/
*.pyc
Your final project folder should now look like this:

![image alt](https://github.com/A-Santhosh-Hub/image-converter-web/blob/main/formate.png)


## Step 2: Push Your Project to GitHub
If you don't have a GitHub account, sign up for a free one here.

Create a New Repository: On your GitHub dashboard, click the "New" button to create a new repository. Give it a name like image-converter-web, keep it Public, and click "Create repository".

Upload Your Files: On the new repository page, click the "uploading an existing file" link. Drag and drop all your project files and folders (except uploads/ and __pycache__/) into the browser window.

Commit Changes: Type a short message like "Initial commit" and click the "Commit changes" button. All your code is now on GitHub.

## Step 3: Deploy on Render
This is the final step where you bring your app to life.

Create a Render Account: Sign up for a free account at Render.com. You can sign up using your GitHub account to make things easier.

Create a New Web Service:

Once you are on the Render Dashboard, click "New +" and then select "Web Service".

Connect your GitHub account if you haven't already. Find your image-converter-web repository in the list and click "Connect".

Configure the Settings:

Name: Give your app a unique name (e.g., my-image-app). Your final URL will be my-image-app.onrender.com.

Region: Choose a region closest to you (e.g., Singapore or Frankfurt).

Branch: main (or master).

Build Command: pip install -r requirements.txt (this is usually the default).

Start Command: This is very important. Enter this exact command: gunicorn app:app

Instance Type: Make sure you select Free.

Deploy!: Scroll to the bottom and click the "Create Web Service" button.

Render will now start building and deploying your application. You can watch the progress in the log window. This will take a few minutes.

## Step 4: Access Your Live App!
Once the deployment is finished, Render will provide you with your live URL at the top of the page (e.g., https://my-image-app.onrender.com).

Click that link, and you will see your web application running live on the internet, ready for anyone to use!

Important Notes on the Free Tier:
Sleeps after inactivity: If no one visits your app for 15 minutes, Render will put it to "sleep" to save resources. The next person who visits will have to wait about 30 seconds for it to "wake up". This is normal for free plans.

Temporary File Storage: The uploads folder on Render is temporary. This is perfectly fine for your app because you upload a file, process it immediately, and send the result back. The server cleans up old files on its own.


Environment Variables

Set environment-specific config and secrets (such as API keys), then read those values from your code. Learn more.


Required


Add Environment Variable

Add from .env


Show thinking
You can safely skip this section. You do not need to add any Environment Variables for the image converter project we built.

That section is for more advanced applications that need to handle secret information, like passwords or API keys.

## What Are Environment Variables? 🔑
Think of Environment Variables as a secure "contact list" for your application.

Instead of writing a secret password directly in your code (which is insecure, especially if your code is on GitHub), you save it on the server as an environment variable. Your code then just says, "Hey server, what's the password?"

Key: The name of the secret (e.g., DATABASE_PASSWORD).

Value: The secret itself (e.g., S3cur3P@ssw0rd!).

## Why Are They Used?
Security: It keeps your secrets out of your public code. This is the main reason.

Flexibility: You can use different passwords for your local computer and the live server without changing the code itself.

Our image converter doesn't connect to any databases or external services, so it has no secrets to protect.

✅ You can just scroll past this section and continue with the deployment.
