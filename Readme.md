[![Docker Pulls](https://img.shields.io/docker/pulls/immauss/openvas.svg)](https://hub.docker.com/r/immauss/openvas/)
[![Docker Stars](https://img.shields.io/docker/stars/immauss/openvas.svg?maxAge=2592000)](https://hub.docker.com/r/immauss/openvas/)
[![Docker Stars](https://img.shields.io/docker/image-size/immauss/openvas.svg?maxAge=2592000)](https://hub.docker.com/r/immauss/openvas/)
[![Docker Stars](https://img.shields.io/docker/cloud/build/immauss/openvas.svg?maxAge=2592000)](https://hub.docker.com/r/immauss/openvas/)
[![Docker Stars](https://img.shields.io/docker/cloud/automated/immauss/openvas.svg?maxAge=2592000)](https://hub.docker.com/r/immauss/openvas/)
[![GitHub Issues](https://img.shields.io/github/issues-raw/immauss/openvas.svg)](https://github.com/immauss/openvas/issues)
[![Discord](https://img.shields.io/discord/809911669634498596?label=Discord&logo=discord)](https://discord.gg/DtGpGFf7zV)
[![Twitter Badge](https://badgen.net/badge/icon/twitter?icon=twitter&label)](https://twitter.com/immauss)
![GitHub Repo stars](https://img.shields.io/github/stars/immauss/openvas?style=social)

# A Greenbone Vulnerability Management docker image
### Brought to you by ###
[![Immauss Cybersecurity](https://github.com/immauss/openvas/raw/master/images/ics-hz.png)](https://immauss.com "Immauss Cybersecurity")


# Tags  #
tag              | Description
----------------|-------------------------------------------------------------------
21.04.02   | The latest and greatest !
multi      | A new approach. amd64 & arm64 in a single docker image.
buster    | The new container based on Debian Buster No change to operation, or features, just easier to maintain. (Hopefuly)
armv7     | The latest build for ArmV7 with Postgresql11. (Coming soon.)
20.08.04.6 | The last 20.08 image
beta            | from the latest master source from greenbone. This may or may not work.
pre-20.08   | This is the last image from before the 20.08 update. 
v1.0             | old out of date image for posterity. (Dont` use this one. . . . ever)


- - - -
## Documentation ##
The current docs are maintained on github [here](https://github.com/immauss/openvas/tree/master/docs)
- - - -
### 19 July 2021 ###
- Buster. When i started this journey, I only wanted to add a few features I thought were missing to an already existing container. I guess I let it get a little out of hand. One of things that bothered me about the orignal, that I didn't have the time deal with, was that it was running on a base container image using Ubuntu. Nothing against Ubuntu, but I know the Greenbone Devs build on Debian Buster. With all the dependancy issues I was having trying to get the ArmV7 image to build, I decided it needed to be done. So I finally took the time to rebuild the whole thing using Debian Buster. The idea is that this should reduce the number of problems I have with dependencies and be more in line with Greenbone.
Just one glitch:

   Postgresql 12

   When I moved to 20.08, I went to the current Postgressql with Ubuntu, which was 12.  But Greenbone is still standardizing on 11. Now I could build the image on 11, but then anyone with an existing DB (myself included would have to go throught the pain of downgrading the DB. This doesn't work well with the idea of having an easy to use slim container. So, I now have an image, based on Buster, and using Postgresql 12. 
   
   The Bad news. Postgresql12 is not available on ArmV7. But since I've never had a working ArmV7 image, there shoudln't be anyone with a Postgresql12 DB. So ... there will be an ArmV7 image, but it will be seperate and live with it's own tag in GitHub and Docker Hub, while the AMD64 & Arm64 images will be a multi-arch image as the latest. I know I can build ArmV7 on Buster, but only with Postgresql11. 
   
   ## Status: ## 
   - The multi-arch image is almost ready. (Expected by 22 July)
   - The ArmV7 will need a re-write of the start scripts to support Postgresql11. (Expected 29 July)
           
     
- - - -
### 12 July 2021 ###
- armv7 ..... is failing to build gvmLibs because of dependancies. At the moment, the latest tag only has amd64 & arm64

- Scott

- - - -
### 28 June 2021 ###
- armv7 is now live with the latest tag. 
- I've also just noticed that Greenbone has release 21.4.1 !! I'm building now and will try to test and have it up in the next day or so. 


-Scott

- - - - 
### 21 June 2021 ###
- Finally!!! The latest image on Docker Hub is now a multi-arch image. amd64 & arm64. These should run on any 64 bit x86 kernel and on the arm 64 bit kernels. (aarc64 & arm64). I also resolved a bug in weekly rebuild script that was having the images built with an old DB. If you expereinced a rather slow to ready container recently, that should be resolved. I've also moved the rebuilds off to my own hardware vs using the Docker Hub build system. This allows me to do the multi-arch builds with buildx.  There was also a minor update from Greenbone. 

-Scott

- - - -
### 14 June 2021 ###
- A new approach. Now that Docker is going to be charging for using thier build environment .... I decided to go a step further. I'm going to be doing the builds on my own infrastructure, so why not go for a multi-arch build. Something I don't think docker hub offers anyway. So the first (of hopefully many) multi-arch images is now on docker hub. The tag is simple "multi". I can't stress enough that this is very BETA at the moment. I've not done any serious testing with it. Please let me know if you find any isues on any platform. And maybe drop me a note if you have succes too. ( here, a twitter @immauss ... ) 

-Scott

- - - - 
### 12 May 2021 ###
- Looking for feedback on the ARM images. I have not yet attempted the 21.04 on ARM. If you are interested, please open an issue and let me know. 
- - - -
### 10 May 2021 ###
- 21.04 is now the latest! The new image will upgrade your DB, so no worries on using an older DB. Bonus, 21.04 is WAY faster with postgres 12. I`ve also added all the environement options to the docker_composer.yaml in the git repo, so if composer is your thing, start there. No other new functionality added to the image, but lots of changes from Greenbone.  If you have any problems, please open an issue. 
- - - -
### 4 May 2021 ###
***May the 4th be with you***
- So the 21.04 is taking a little longer than anticipated. What would be great, would be a few more testers. If you have the cycles, I would really appreciate any testing. Just make sure you are not working on your production data yet!

Thanks,
-Scott

- - - -
### 27 April 2021 ###
***New GVM version !!***
- OK ... I's here!! 21.04. It has some tweaks and fixes. But the biggest change that I see is that it seems to be performing much better with postgresql 12. This is good news. I have it working but I have NOT made it the latest yet. The current tag is 21.04-beta. It is currently not tested with upgrading a current DB. I've only tested with a fresh start. If you choose to test, please drop me not and PLEASE open an issue if you find a problem with it. 

-Scott

- - - -
### 28 Mar 2021 ###
***gmp option added***
- At the request of [hoboristi](https://github.com/hoboristi) , I`ve added an option to enable the gmp service. It will require two options though.
  - First, enable the service in the container with ``` -e GMP=<service port number> ```
  - Then publish the port from the container ``` -p <external port number>:<service port number> ``` 
  - Example:
```
docker run -d -p 9392:9392 -p 9390:9390 -e GMP=9390 --name openvas -v openvas:/data immauss/openvas:latest 
```

-Scott 

### 27 Mar 2021 ###
***Doh!***
- Appologies to anyone who tried to pull the latest image in the last 24 hours. It looks like I accidently pusshed my dev branch to master and Docker Hub diligently built a new image.  ....... This didn't work. I've reveresed the changes and the "latest" tag is now good. Thanks to [cybermcm](https://github.com/cybermcm) for catching the problem and opening an issue. 
- For the curious, the new work is on finding a clean way to downgrade the DB from postgresql 12 to 11. Apprently there are some performance issues with gmvd and postgresql 12. 

-Scott

- - - -

### 16 Mar 2021 ###
**Tag 20.08.04.6**
- Added the HTTPS environment variable. Setting this to true will cause gsa to start with https enabled. I`m working on a better implementation of this, but as this was requested, I went ahead and added it. The `better` implementation will be able to use letsencrypt certificates! 

-Scott

### 23 Feb 2021 ###
**Tag 20.08.04.5**
- Fixed the PASSWORD and USERNAME env vars. Make sure you check checks the docs for the caveats.
- Wrote a new script to make sure I`m getting the latest releaes from all of the Greenbone github repos.

-Scott

- - - -
### 18 Feb 2021 ###
## A few minor updates and one **BIG** change ##
- The restore logs now go to /usr/local/var/log/db-restore.log instead of the terminal
- The start.sh is modifying the feed sync scripts (greenbone-nvt-sync and greenbone-feed-sync) to make the normal output a little quieter.
- And the **BIG** announcement:
# Automated weekly builds with content updates!! #
Early every Monday morning, the image will be rebuilt with the latest feed updates. This means that the latest image will always have  feed data less than 1 week old!!!

-Scott
- - - -
### 16 Feb 2021 ###
I have added some additional functionality to the image:
- Container now does a proper shutdown of postgresql on container stop. (I believe not having this has been the cause of some DB corruption seen in the past.)
- New "RESTORE" option added to restore from a DB backup. [See the Docs](https://github.com/immauss/openvas/tree/master/docs#database-backup)
- Updated  [documentation](https://github.com/immauss/openvas/tree/master/docs)
- New latest tag is now 20.08.04.4.
- There is also a 'beta' tag now. Use this at your own peril as it may or may not work. (probably it will not.)

-Scott

- - - - 



### 14 Feb 2021 ###
# Short update
After pushing 20.08.04.1, I realized I had not merged the base db changes. So 20.08.04.2 includes the changes to support the base DB and contains a DB from today. 

-Scott

- - - - 



### 13 Feb 2021 ###
# Greenbone release 20.08.1 about a week ago. 
### I found out yesterday, and today ... I'm releasing tag: 20.08.04.1. 
- This has the fix in gvmd to make the processing of the feeds more resilient. If you are getting a ton of errors for an NVT that is not in the family, this image will fix it. The problem is actually in the feed,  but the latest gvmd does not get stuck on feed issues. 

- There is also a new beta tag, but as you might expect, this is not really working as it is pulling from the master branch of all the tools. The backend seems to work, but the gsa is just not getting it. This is mainly to help me be ready for the next version by keeping me alert on any new dependencies that may come with the next version. Use it at your own peril. 

-Scott

- - - - 


### 3 Feb 2021 ###
# Big News !

The latest image, tag 20.08.04 includes a baseline database and feed sync. No more waiting for the feeds to sync and then waiting for gvmd to build the database. This means you can login and start running scans about a minute after running the container!

The downside is the USER and PASSWORD environment variables no longer work as they default (admin:admin) is part of the baseline database. I think I can work around this, but that will have to wait for 20.08.05.

There is also a new environment variable: SKIPSYNC . This does exactly what it says, it bypasses the feed sync on container start to speed you along. 

-Scott

- - - - 

### Jan 2021 ###
# 20.08 
# NOTE: DO NOT USE THIS WITH YOUR OLD PRE-20.08 database. 

## New with the 20.08 images. ##
- Added an environment var for quietening the feed syncs.
  - QUIET="true" will send the output of the sync scripts on startup to /dev/null
- Added an environment var for increasing redis DBs. 
  - REDISDBS="<number of DBs>"   default is 512.
- This is only what I've added. There are tons of other changes with 20.08 itself.
- New multistage build makes for a MUCH smaller image. Down by more than 1 Gig. Same functionality! 
- - - - 





For License info, see the [GNU Affero](https://github.com/immauss/openvas/blob/master/LICENSE) license.

Thu Feb 25 23:59:13 UTC 2021
