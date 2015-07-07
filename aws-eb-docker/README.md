# docker
##Initial AWS EBS command line tool Configuration

0. Download the AWS EBS command line tool https://aws.amazon.com/code/6752709412171743
0. Configure the tool and set the AWS Access and Secret key
0. Check its working fine `eb --help`
0. Go to the  git checkout folder 
0. Initialization the Elastic Beanstalk Environment `eb init`
0. In the eb Initialization setup it will ask question about region and names of environment
0. Start the EB Environment `eb start`

##AWS EBS Deployment 

0. `git status`  if any file need to add and commit
0. `eb push` to deployment the current change to EBS
