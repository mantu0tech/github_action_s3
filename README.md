# github_action_s3
Host your portfolio on s3 using github

Create a git hub repo 

Now upload your code for repo



Now go to aws and create s3 bucket 

Added bucket policy 

{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "PublicReadGetObject",
            "Effect": "Allow",
            "Principal": "*",
            "Action": "s3:GetObject",
            "Resource": "arn:aws:s3:::my009portfolio/*"
        }
    ]
}

Now go to iam user and create access key 



Now go to github 
go to settings
Scroll down a little bit 
\
Click on actions 

Click on create\

Again click on add 

Click on action 


Click on set up workflow 

name: my-portfolio # Name of the deployment

on:
  push: # Trigger the workflow when changes are pushed
    branches:
      - main
jobs: # Any name can be provided
  build-and-deploy:
    runs-on: ubuntu-latest # Latest version of Ubuntu
    steps:
      - name: Checkout # Check out the repository's code into the workflow's execution environment.
        uses: actions/checkout@v1 # Script actions

      - name: Configure AWS Credentials
        uses: aws-actions/configure-aws-credentials@v1
        with:
          aws-access-key-id: ${{ secrets.AWS_ACCESS_KEY_ID }}
          aws-secret-access-key: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
          aws-region: us-east-1

      - name: Deploy static site to S3 bucket
        run: aws s3 sync . s3://my009portfolio --delete # Change bucket name


Click on commit changes 
Go to action and you will see in progress status 

From github it will automatically upload all the code to github 


It mean its completed 
Now lets enable the static website hosting 


And boom you have finally uploaded you files from github


