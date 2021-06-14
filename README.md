# Amazon EC2 Deployment: CICD Pipeline using GitHub Actions and AWS CodeDeploy

### Step 1
- Fork https://github.com/ufuu/FlaskAppCodeDeploy.git

### Step 2 
- Get Terraform code from https://github.com/ufuu/awslambda/tree/master/github_actions_ec2 and change git repo url in script.tpl file(line 14). 
- Also create an SSH key using ssh-keygen command.

### Step 3
- Now apply the code.
- This will create our code deploy job along with an auto-scaling group with 2 EC2 instances, running behind an ALB. Once setup is created, try accessing ALB url and make sure our app is running

### Step 4
- In the repo,Go to Actions and Enable work flow. Also create these 2 secrets (Settings-Secrets) which are required to trigger Code Deploy job.

### Step 5
- Now make some changes to templates/index.html file and commit to the main branch. This will trigger our GitHub workflow which will eventually start our Code Deploy job.

### Concluding Remarks
Once Code Deployment is completed, access the application and check if it got updated or not.

Note: We are using IN_PLACE deployment type, so when code is deployed onto one instance, it won’t be serving traffic. However since we have at least 2 instances in our ASG, our application will still be available.
