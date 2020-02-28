# BART NLP with Amazon SageMaker

A workshop showing how to host a BART NLP MxNET model with Amazon SageMaker. 
We use a pre-trained model for this workshop, as the training time is too long to be practical, but the training script is included for the curious.

# Steps

### Get the Code
Clone this repository, by running 

``` git clone foo```

### Create an Amazon SageMaker notebook instance

- Login to the console at [console.aws.amazon.com](https://console.aws.amazon.com/console/home)

- Go to the SageMaker service
- Choose the Ireland (eu-west-1) region
- ## Create a LifeCycle Configuration
  - On the left hand menu browse to Notebooks / Lifecycle configurations
  - Select Create Configuration
  - Enter `BART` as the Configuration Name
  - In 'Start Notebook', paste the contents of the file `tutorial/sagemaker-lifecycle-start.config`
  - In 'Create Notebook', paste the contents of the file `tutorial/sagemaker-lifecycle-create.config`
  - Hit `Create Configuration`
- ## Create a note book instance
  - On the Left Hand Menu, select Notebook Instances, and press 'Create notebook instance'
  - Give your instance a Name
  - For 'instance type' choose `ml.t3.2xlarge`
  - Expand out 'Additional configuration'
    - Select `BART` as your Lifecycle Configuration
    - Enter `50` for Volume size in GB
  - Scroll down to 'Git Repositories'
  - Choose `Clone a public Git repository to this notebook instance only`
  - Enter the `https` variant of this repository
  - Hit 'Create notebook instance'
- ## Watch the CloudWatch logs as it launches
  - Click on your new instances Name, and go to the instance details page
  - Click on 'View Logs', just under the Lifecycle Configuration link, and the logs will open in a new tab
  - Hit the reload button until you see an entry. This can take a couple of minutes as the machine needs to be created.
  - Look at the logs for the 2 lifecycle events we attached to the instance, Create and Start
  - When both Create and Start have completed, close the logs tab and go back to the SageMaker tab
  - Select Open Jupyter

### Do the lab

- Browse to `tutorials/deploy.ipynb`, this will open in a new tab
- Step thru the cells one at a time, reading as you go

