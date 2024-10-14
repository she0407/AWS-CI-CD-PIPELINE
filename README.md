# AWS Continuous Integration Demo

## Set Up GitHub Repository

The first step in our CI journey is to set up a GitHub repository to store our Python application's source code. If you already have a repository, feel free to skip this step. Otherwise, let's create a new repository on GitHub by following these steps:

- Go to github.com and sign in to your account.
- Click on the "+" button in the top-right corner and select "New repository."
- Give your repository a name and an optional description.
- Choose the appropriate visibility option based on your needs.
- Initialize the repository with a README file.
- Click on the "Create repository" button to create your new GitHub repository.

Great! Now that we have our repository set up, we can move on to the next step.

## Create an AWS CodePipeline
In this step, we'll create an AWS CodePipeline to automate the continuous integration process for our Python application. AWS CodePipeline will orchestrate the flow of changes from our GitHub repository to the deployment of our application. Let's go ahead and set it up:

- Go to the AWS Management Console and navigate to the AWS CodePipeline service.
- Click on the "Create pipeline" button.
- Provide a name for your pipeline and click on the "Next" button.
- For the source stage, select "GitHub" as the source provider.
- Connect your GitHub account to AWS CodePipeline and select your repository.
- Choose the branch you want to use for your pipeline.
- In the build stage, select "AWS CodeBuild" as the build provider.
- Create a new CodeBuild project by clicking on the "Create project" button.
- Configure the CodeBuild project with the necessary settings for your Python application, such as the build environment,  build commands, and artifacts.
- Save the CodeBuild project and go back to CodePipeline.
- Continue configuring the pipeline stages, such as deploying your application using AWS Elastic Beanstalk or any other suitable deployment option.
- Review the pipeline configuration and click on the "Create pipeline" button to create your AWS CodePipeline.

Awesome job! We now have our pipeline ready to roll. Let's move on to the next step to set up AWS CodeBuild.

## Configure AWS CodeBuild

In this step, we'll configure AWS CodeBuild to build our Python application based on the specifications we define. CodeBuild will take care of building and packaging our application for deployment. Follow these steps:

- In the AWS Management Console, navigate to the AWS CodeBuild service.
- Click on the "Create build project" button.
- Provide a name for your build project.
- For the source provider, choose "AWS CodePipeline."
- Select the pipeline you created in the previous step.
- Configure the build environment, such as the operating system, runtime, and compute resources required for your Python application.
- Specify the build commands, such as installing dependencies and running tests. Customize this based on your application's requirements.
- Set up the artifacts configuration to generate the build output required for deployment.
- Review the build project settings and click on the "Create build project" button to create your AWS CodeBuild project.

Fantastic! With AWS CodeBuild all set up, we're now ready to witness the magic of continuous integration in action.

## Trigger the CI Process

In this final step, we'll trigger the CI process by making a change to our GitHub repository. Let's see how it works:

- Go to your GitHub repository and make a change to your Python application's source code. It could be a bug fix, a new feature, or any other change you want to introduce.
- Commit and push your changes to the branch configured in your AWS CodePipeline.
- Head over to the AWS CodePipeline console and navigate to your pipeline.
- You should see the pipeline automatically kick off as soon as it detects the changes in your repository.
- Sit back and relax while AWS CodePipeline takes care of the rest. It will fetch the latest code, trigger the build process with AWS CodeBuild, and deploy the application if you configured the deployment stage.

## AWS DEMO

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/voy1lsm3aco7vnkcjzqc.png)
Step 1: GitHub Repository Setup
Create a GitHub repository to store the source code for your Python application.(https://github.com/she0407/CI-CD-PIPELINE-DEMO)
Ensure that the repository is correctly configured with the necessary files for your project.

Step 2: AWS CodePipeline Creation
Create a new AWS CodePipeline to automate the CI process.
Connect the pipeline to the GitHub repository, specifying the repository and branch.

Step 3: AWS CodeBuild Setup
In the AWS CodeBuild service, create a new build project.
Under the Source Provider, log in to your GitHub account and choose the repository for the project.
In the Environment section, choose Ubuntu as the operating system and select the latest image version. Create a new service role if needed.
In the Buildspec section, switch to the editor mode and enter the commands for building your Python application. 
Create the build project once everything is configured.

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/rpk6swv9wnpvapzjp2ly.png)


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/vffa4i606a1tnskg8xy5.png)

under the environment section I chose the os as ubuntu and cjhose the latest image version and created new service role.


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/h6qjlmp21bml8t7fpyi3.png)

under the buildspec I chose inster build commands and switch to editor and wrote commands for building 

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/1tu1j0olq8rl754zqxpn.png)

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/iaerspmmhqhifj4umtz4.png)
and I have created a code build.
afterwards I chose aws system manager and created three parameters to connect to my dockerhub one is url (docker.io) and username and passwords

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/0aw5m8ntt25p0my7c2q8.png)

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/ldhim1eues29wyxb373v.png)

Step 4: AWS Systems Manager Parameter Store Setup
Navigate to AWS Systems Manager and create three parameters to connect to Docker Hub:
Docker Hub URL (e.g., docker.io)
Docker Hub Username
Docker Hub Password
These parameters will be used later to push the Docker image to Docker Hub.
so I have successfully created a three parameters as shown below:

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/ypbx8vbde0cteznhbuzm.png)

Step 5: IAM Role and Permissions
In IAM, create the necessary roles and permissions for your build process. You’ll need roles for CodeBuild and CodeDeploy, ensuring they have access to push images to Docker Hub and interact with EC2 instances.

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/h1w9bp3699ytoxot5bn3.png)

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/ar3na8loy442gvpabnf8.png)
Step 6: Build Execution
Return to AWS CodeBuild and click on Start Build. The build process will run according to the specified build commands.
Once the build is complete, the Docker image will be created and pushed to Docker Hub.


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/bmlvn8yujyt9e5n36gck.png)


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/t69futy0purf48m70nka.png)


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/umx9qymx5god3coy920u.png)
the image has been created in the Docker hub 

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/x4by1yqhsq8rq4vxk3wd.png)

Step 7: Pipeline Configuration
Set up the pipeline by defining the source, build, and deploy stages. For the source stage, select the GitHub repository and the branch to monitor.
Skip the deployment stage for now if it’s not required.


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/hkus3d3clikidwauwfvs.png)

under the source stage I chose the latest git version and connected to github.

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/9x3zxkfc13l33km19ba7.png)

I chose the repo and the branch and format 

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/c9sm9goxuc9tjzrbvyfs.png)

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/e8o1tv95ip863asedx4c.png)
and I have created pipeline skipping the deployment stage.

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/k2hghf0cg1okm2p6xkih.png)

Step 8: EC2 Instance Setup for Deployment
In AWS EC2, launch a new instance for deployment. Ensure that the appropriate security groups are configured, and connect to the instance via SSH.
Verify that the CodeDeploy Agent is running.
as we can see  under the build “build has succeeded ”
now I have created an application in the codedeploy then created application


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/7wks1a54nglfyncbmoyu.png)
 
 
![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/3p9cnjk3x2n1xiohlp48.png)

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/y0w5g52r1kvymbvrz9ak.png)

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/0uqsbrhxqfse6xcztoom.png)

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/isbot9k89y1viakhbfro.png)

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/4fc7a6wx27u8has8mo25.png)

I have gave the command to update and install the code deploy agent and checked if the instance has started or no 

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/j4jbv93rsk1dyfzxt27p.png)


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/yfm8pd9suvvq4707dv23.png)


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/pa0slwwelrc67tsmzde9.png)

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/1kqq41zv0hpfk62ikos6.png)
as the agent is under running status we can see from the below capture,

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/jye3dbxizsscbfomtsbm.png)

after that we create role to give the necessary information one I have created is for ec2 role full access and the code deploy role 

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/z5jqxbb9o136lts6dib1.png)
Step 9: CodeDeploy Configuration
In AWS CodeDeploy, create a new application and deployment group.
Select the EC2 service role for CodeDeploy.
For deployment, select GitHub as the source and provide the repository token and commit ID for the latest version of the application.
Execute the deployment, which will pull the application code from GitHub and deploy it on the EC2 instance.


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/qmlonut3kfg7bfyiej25.png)


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/lbpbmg5vh90j8126sxxe.png)

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/redh6wyuag9w8m5ymiu4.png)

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/umrxmgr0kn4txqrn31o7.png)

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/88czgk70l5cr4oo6imko.png)

after that will move to dockerhub and copy the pull command and paste it into the startcontainer.sh file 

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/ecsn6t1gmgdhn01vr97k.png)


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/6o57n2rrs73e1s7lxmvr.png)
and will commit and push it to github

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/h6ieqg31tmci2wjj59cc.png)

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/n478tweigdzw001b1dyi.png)
will take the latest commit and then edit in the code deployment and now paste it ,

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/8rbhwpwb4p2njwbsiaxm.png)

then all three build source and deployment stage individually succeed so will create a pipeline for that will add a stage to running pipeline and then add the build artifact as input artifact and run the pipeline ,

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/7rlqv207l1yj0bv88pla.png)


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/dpjl11mfck7lghcqj83q.png)


![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/rei2i8fqaednj9mdy7kk.png)

Step 11: Final Deployment and Pipeline Success
Use the latest commit and edit the CodeDeploy settings to deploy this updated version.
Verify that all three stages (source, build, and deployment) succeed, ensuring the complete CI pipeline runs smoothly.

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/9tzmre7fodf85b22jdoz.png)
and the whole pipeline is succeed as well . 

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/54jktmizk5pa9ozz4jyz.png)

![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/ozyrvnxi7l742md5gd73.png)

I implemented continuous integration for my Python application using AWS and GitHub. To begin, I created a GitHub repository for my code. Then, I set up an AWS CodePipeline to automate the integration, linking it to my GitHub repository and configuring AWS CodeBuild to handle the build process. I specified the necessary build environment and commands in CodeBuild. Once configured, I initiated the CI process by making updates to my GitHub code, which automatically triggered the pipeline, building and deploying the application as planned. This approach optimized my workflow by automating the steps from code updates to deployment, ensuring seamless and efficient integration and deployment.




















































