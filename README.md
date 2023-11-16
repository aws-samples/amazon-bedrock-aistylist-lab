![Alt text](aistylist/images/AIStylist.png?raw=true "AI Stylist Lab")
# Amazon Bedrock AI Stylist lab

## Introduction

Welcome to the AI Stylist Lab!

This lab explores some of the most common usage patterns for Generative AI use cases. You will gain hands-on experience implementing these patterns with Amazon Bedrock.

Amazon Bedrock is a fully managed service that provides access to Foundation Models (FMs) from third-party providers and Amazon. With Amazon Bedrock, you can choose from a variety of models to find the one that’s best suited for your use case.

In this lab, you'll build your own AI Stylist application, a new shopping experience for customers where you will explore how Amazon Bedrock features come together to help the customer create an outfit for going back to the office. This lab is the next step of your Amazon Bedrock learning journey, after the [AI Stylist demo](https://aistylist.awsplayer.com/). We will use techniques for generating text and images, chat experience, entity extraction, and retrieval-augmented generation (RAG). You will gain hands-on experience with implementing these patterns via Amazon Bedrock APIs and SDKs, as well as open-source software like LangChain and FAISS.

Lab objectives:

* Extract product attributes from a customer prompt
* Use RAG to embed a product catalog and order history in Amazon Titan Embeddings
* Query the embeddings to generate 5 style looks from the customer prompt
* Generate images for the 5 looks.
* Add a chatbot to answer questions about customer reviews about the product
* Generate a summary for the customers reviews about the product
* Integrate a DIY agent to associate weather data and recommend accessories

## Getting started

### Choose a notebook environment

This workshop is presented as a series of **Python notebooks**, which you can run from the environment of your choice:

- For a fully-managed environment with rich AI/ML features, we'd recommend using [SageMaker Studio](https://aws.amazon.com/sagemaker/studio/). To get started quickly, you can refer to the [instructions for domain quick setup](https://docs.aws.amazon.com/sagemaker/latest/dg/onboard-quick-start.html).
- For a fully-managed but more basic experience, you could instead [create a SageMaker Notebook Instance](https://docs.aws.amazon.com/sagemaker/latest/dg/howitworks-create-ws.html).
- If you prefer to use your existing (local or other) notebook environment, make sure it has [credentials for calling AWS](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-configure.html).

### Running the workshop
- Run the [Intro to Bedrock](./aistylist/intro_to_bedrock.ipynb) notebook to get started and install the necessary libraries
- Run the [AiStylist notebook](./aistylist/aistylist.ipynb) to execute the workshop


### Enable AWS IAM permissions for Bedrock

The AWS identity you assume from your notebook environment (which is the [*Studio/notebook Execution Role*](https://docs.aws.amazon.com/sagemaker/latest/dg/sagemaker-roles.html) from SageMaker, or could be a role or IAM User for self-managed notebooks), must have sufficient [AWS IAM permissions](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies.html) to call the Amazon Bedrock service.

To grant Bedrock access to your identity, you can:

- Open the [AWS IAM Console](https://us-east-1.console.aws.amazon.com/iam/home?#)
- Find your [Role](https://us-east-1.console.aws.amazon.com/iamv2/home?#/roles) (if using SageMaker or otherwise assuming an IAM Role), or else [User](https://us-east-1.console.aws.amazon.com/iamv2/home?#/users)
- Select *Add Permissions > Create Inline Policy* to attach new inline permissions, open the *JSON* editor and paste in the below example policy:

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "BedrockFullAccess",
            "Effect": "Allow",
            "Action": ["bedrock:*"],
            "Resource": "*"
        }
    ]
}
```

> ⚠️ **Note:** With Amazon SageMaker, your notebook execution role will typically be *separate* from the user or role that you log in to the AWS Console with. If you'd like to explore the AWS Console for Amazon Bedrock, you'll need to grant permissions to your Console user/role too.

For more information on the fine-grained action and resource permissions in Bedrock, check out the Bedrock Developer Guide.


### Clone and use the notebooks

> ℹ️ **Note:** In SageMaker Studio, you can open a "System Terminal" to run these commands by clicking *File > New > Terminal*

Once your notebook environment is set up, clone this workshop repository into it.

```sh
sudo yum install -y unzip
git clone https://github.com/aws-samples/amazon-bedrock-aistylist-lab.git
cd amazon-bedrock-aistylist-lab
```


You're now ready to explore the lab notebooks!
