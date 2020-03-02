# NLP with Amazon SageMaker

@roberto - Maybe bang an overview in here, about the state of the nation with NLP or something?

## Steps

### Get the Code

Clone this repository onto your local machine, by running 

`git clone https://github.com/podulator/Jan2020-NLPLab.git`

### Create an Amazon SageMaker notebook instance

- Login to the console at [console.aws.amazon.com](https://console.aws.amazon.com/console/home)

- Go to the SageMaker service
- Choose the Ireland (eu-west-1) region
- ## Create a LifeCycle Configuration
  - On the left hand menu browse to Notebooks / Lifecycle configurations
  - Select Create Configuration
  - Enter `BART` as the Configuration Name
  - In 'Start Notebook', paste the contents of the file `sagemaker-lifecycle-start.config`
  - In 'Create Notebook', paste the contents of the file `sagemaker-lifecycle-create.config`
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
  - Enter the `https` variant of this repository, `https://github.com/podulator/Jan2020-NLPLab.git`
  - Hit 'Create notebook instance'
- ## Watch the CloudWatch logs as it launches
  - Click on your new instances Name, and go to the instance details page
  - Click on 'View Logs', just under the Lifecycle Configuration link, and the logs will open in a new tab
  - Hit the reload button until you see an entry. This can take a couple of minutes as the machine needs to be created.
  - Look at the logs for the 2 lifecycle events we attached to the instance, Create and Start
  - When both Create and Start have completed, close the logs tab and go back to the SageMaker tab
  - Select `Open Jupyter`, which will launch in another tab 

### Do the labs

#### Lab 1

In this lab, we’ll train and test a Sentiment Analysis (Text Classification) model on SageMaker using SageMaker’s pre-built Deep Learning containers. 
These containers are available for TensorFlow, MXNet, PyTorch, and Chainer.

With this approach, you simply bring your own Python training script, and SageMaker handles the rest. 
All of this is simplified using the conveniences provided by the SageMaker Python SDK, which abstracts away many of the low level details of setting up training jobs and endpoints.

We'll cover 

- Bringing your own training script for pre-built containers
- Local training and remote cluster training
- Deploying a real-time prediction endpoint
- Deploying a batch endpoint

- Steps
  - Open the `tutorial-1` folder
  - Launch the [sentiment-analysis.ipynb](./tutorial-1/sentiment-analysis.ipynb) notebook
  - Step through the cells

#### Lab 2

Lab 2 involves deploying a BERT model, pre-trained with MxNet and gluonNLP. 
In this lab we will cover some more advanced Amazon SageMaker features, like 

- Bringing your own model
- Creating your own container
- Interacting with Elastic Container Registry (ECR)

- Steps
  - Open the `tutorial-2` folder
  - Launch the [deploy.ipynb](./tutorial-2/deploy.ipynb) notebook
  - Step through the cells

