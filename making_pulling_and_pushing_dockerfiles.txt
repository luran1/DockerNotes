##how to make a dockerfile 

##after you've written all the code for you dockerfile you will need to open docker and know where you've stored your dockerfile.

## you will then use the docker build command to construct your docker. this will not creat your container nor will it creat your image. this is to initialize the code and see if the proccedures are being followed correctly and that the file can run.

##After verifiying that the dockerfile is viable you will then run your docker image with the docker run command. you can run your temporary image by calling it with the command.

##After this happen you may not know if you have run the image so I add CMD ["echo", "ran fully"] to the end of my Dockerfiles to know I did't screw this part up. Once you've confirmed your image you might want to push it to your dockerhub repository. To do this follow these steps:

* you will need to first log into your dockerhub account through your docker 
	* use the command docker login --name=username  it'll then prompt you to put your password in. you might not be able to see what you are typing but you are inputting your password. once inputed, hit enter.

*now you'll need to tag your image. to do this you can use the docker tag imageID repositoryaddress:comment

*once you've completed this task you can then push your image into docker hub using docker push repositoryaddress 



##personal attempt to push files back into dockerhub:

cloned github repository onto my PC
placed repository directory into dockertools directory so that it is excessable 
open dockertools 
change directory to ipsa-nf 
use docker build docker to construct the ipsa-nf image (docker is the directory where the dockerfile is)
once the docker image is build, test ran it using docker --name test imageID
once this ran correctly from the hello world output i begain to try pushing the image ID to my repository in dockerhub
i used docker tag imageID dockerusername/ipsa-nf:comment 
after this i recived confirmation that the image ID's were pushed 
after this I found a new repository in dockerhub called ipsa-nf
I had an issue in pulling this repository back up to my dockerhub using docker pull dockerusername/ipsa-nf which is the name of the repository 
I am reciving a manifest not found error