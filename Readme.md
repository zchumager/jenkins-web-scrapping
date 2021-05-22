1. Create a new folder to store the git project
2. Create a new file without extension just called Jenkinsfile
3. Initialize the repository with git init command
4. Create a new remote repository in github
5. New Task -> Enter a valid name, then click on Pipeline and finally click OK button
6. Choose Definition Pipeline script from SCM in Definition dropdown
7. Choose Git in SCM dropdown
8. Put the http url from the repository created in step 4 in Repository URL textbox
9. Use valid credentials then click Apply button and finally Save button

Concepts

Agent: It is the machine where the terminal is open to execute the shell commands in the script section (inside steps section)
environment section: It creates ENVIROMENT VARIABLES to be used by the shell opened by the agent


Notes:
All new commit are being shown in the next job execution