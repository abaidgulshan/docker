# Docker


##AWS Elastic Beanstalk with docker Multicontainer private Repo
###Initial AWS EBS command line tool Configuration

0. Download the AWS EBS command line tool https://aws.amazon.com/code/6752709412171743
0. Configure the tool and set the AWS Access and Secret key
0. Check its working fine `eb --help`
0. Go to the  git checkout folder of the project
0. Initialization the Elastic Beanstalk Environment `eb init` 
0. In the eb Initialization setup it will ask question about region and names of environment
0. Start the EB Environment `eb start`

###AWS EBS Deployment 

0. `git status`  if any file need to add and commit
0. `eb push` to deployment the current change to EBS

### Private Docker Hub Credetails Setting

0. Here is the link which I used for the private docker hub credetails setting https://www.youtube.com/watch?v=pLw6MLqwmew&feature=youtu.be

In this Setup I have use Dockerrun.aws.json, my private repo with image on the Docker hub

###AWS Multicontainer Port setting and security group setting

0. I have used port 9090 so I need to to add elasitc load balancer listen the port that setting is in .ebextension foder 
1. You need to go to ec2 security group and open the port of TCP 9090
2. Also you need to change the health check on Elastic load balancer 
3. You need to open the elastic load balancer security group 9090 port
4. You need to add the listener port 9090
