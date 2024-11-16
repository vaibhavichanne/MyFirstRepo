Applying CI/CD Principles to Web Development Using Jenkins, Git, and Local 
HTTP Server
Step 1: Set Up the Web Application and Local HTTP Server
● Create a simple web application or use an existing one. Ensure it can be hosted 
by a local HTTP server.
● Set up a local HTTP server (e.g., Apache or Nginx) to serve the web application. 
Ensure it's configured correctly and running.

Step 2: Set Up a Git Repository
Create a Git repository for your web application. Initialize it with the following 
commands: git init, git add, git commit -m "Initial commit"
● Create a remote Git repository (e.g., on GitHub or Bitbucket) to push your code 
to later.

Step 3: Install and Configure Jenkins
● Download and install Jenkins following the instructions for your operating 
system (https://www.jenkins.io/download/).
● Open Jenkins in your web browser (usually at http://localhost:8080) and 
complete the initial setup.
● Install the necessary plugins for Git integration, job scheduling, and webhook 
support.
● Configure Jenkins to work with Git by setting up your Git credentials in the 
Jenkins Credential Manager

Step 4: Create a Jenkins Job
● Create a new Jenkins job using the "Freestyle project" type.
● Configure the job to use a webhook trigger. You can do this by selecting the 
"GitHub
hook trigger for GITScm polling" option in the job's settings.

Step 5: Set Up the Jenkins Job (Using Execute Shell)
● In the job configuration, go to the "Build" section.
● Add a build step of type "Execute shell."
● In the "Command" field, define the build and deployment steps using shell 
commands. For example:
# Checkout code from Git
# Build your web application (e.g., npm install, npm run build)
# Copy the build artefacts to the local HTTP server directory
rm -rf /var/www/html/webdirectory/*
cp -r * /var/www/html/webdirectory/

Step 6: Set Up a Webhook in Git Repository
● In your Git repository (e.g., on GitHub), go to "Settings" and then "Webhooks."
● Create a new webhook, and configure it to send a payload to the Jenkins 
webhook
URL (usually http://jenkins-server/github-webhook/). Make sure to set the content 
type to "application/json."
● OR use “GitHub hook trigger for GITScm polling?” Under Build Trigger

Step 7: Trigger the CI/CD Pipeline
● Push changes to your Git repository. The webhook should trigger the Jenkins job 
automatically, executing the build and deployment steps defined in the "Execute 
Shell" build step.
● Monitor the Jenkins job's progress in the Jenkins web interface.

Step 8: Verify the CI/CD Pipeline
Visit the URL of your local HTTP server to verify that the web application has 
been updated with the latest changes.