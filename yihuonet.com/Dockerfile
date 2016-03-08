#Base Define
FROM tomcat:7-jre7
MAINTAINER kai.zhu "kai.zhu@yihuonet.com"
ENV REFRESHED_AT 2016-03-08 10:00

#Version Define
ENV YIHUONET_VER 0.2.4
ENV YIHUONET_FILENAME yihuonet-v$YIHUONET_VER.zip

########################################
# History  
# 2015-11-27 v0.0.1 First Version
# 2015-12-23 v0.1.0 Push Online-test Version
########################################
########################################
#Official Code by docker-library, https://hub.docker.com/_/tomcat/

ENV TOMCAT_ORIGIN_ROOT webapps/ROOT
ENV MCMS_DOWNLOAD_FILE http://us.oss.yihuonet.com/yihuonet-official-website/$YIHUONET_FILENAME

#Deploy AND Delete origin root directory
WORKDIR $CATALINA_HOME/webapps
RUN apt-get install -y wget unzip \
    && rm -rf ROOT \
    && mkdir ROOT \
	&& cd $CATALINA_HOME/$TOMCAT_ORIGIN_ROOT \
	&& wget $MCMS_DOWNLOAD_FILE \
	&& unzip $YIHUONET_FILENAME \
	&& rm -f $YIHUONET_FILENAME \
    && cd $CATALINA_HOME/webapps \
	&& rm -rf manager
ADD tomcat/conf/server.xml $CATALINA_HOME/conf/server.xml

