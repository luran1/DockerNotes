#Bioconductor docker pulling and running 

docker pull bioconductor/release_base

#this will pull the image from the docker repository to my docker 

docker images
REPOSITORY                  TAG                 IMAGE ID            CREATED  
bioconductor/release_base   latest              18f6a97aa589        2 years ago
1.28GB

#this is confirmation that I have sucessfully pulled the image. Now we need to run it within a container to modify it. 

docker run -ti bioconductor/release_base R

#I've now booted into the bioconducter Rstudio, from here I want to try and install xcms as a package.
#before this I will check what packages are installed and if xcms is within this Rstudio. 

installed.packages()
find.package("xcms")

#the return for the second command for searching for xcms has returned an error because there is no xcms installed.
Error in find.package("xcms") : there is no package called ‘xcms’

#now we are going to try to install xcms from Rstudio. Following instructions from the Bioconductor website https://bioconductor.org/packages/release/bioc/html/xcms.html ,we need to first install BiocManager inot our Rstudio.
install.packages("BiocManager")

#this returns a warning message: package ‘BiocManager’ is not available (for R version 3.3.2), so we know now that we need to update the Rstudio first before we can install xcms.

#to do this I am going to exit out of the Rstudio and enter the container again through bash to update first my base linox operator and then my Rstudio version.

ctrl+D
docker run -ti bioconductor/release_base bash
apt-get update 

#this will update your linix 

#now we need to update our Rstudio, but the only way I've seen to do this is to reinstall Rstudio with the latest verson. I dont know how to do this in docker so I'll have to try doing something else.



# The next thing I want to try is now changing the Rstudio verson from the dockerfile. to try this I'll need to first download the dockerfile from the image. 
# After some reading online I've concluded that trying to make a dockerfile from an image would be too much work and that it would be easier to pull a dockerfile that has xcms already installed within the image. this will assure the latest verson of Rstudio and will allow me to install other packages along with xcms.

#The docker repository that I am pulling is from https://github.com/wilsontom/xcms-dockerdev , I've follwed the Pull instuctions and am now going to open his image into R 

docker run -ti wilsontom/xcms-dockerdev R
installed.packages()

#xcms is present as an installed packages. So in theory raw data can be run through this container and be processed through the xcms package. 

#now I am going to push this image into my repository for later use. to do this you can follow the instructions below:

docker tag IMAGEID username/repository:tag
docker push username/repository

