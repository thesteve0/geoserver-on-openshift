A quickstart for GeoServer to run on OpenShift

I used Tomcat 7 (JBoss EWS 2.0)

This is based on GeoServer 2.8.0 WAR file. http://geoserver.org/release/2.8.0/

To fully appreciate what is happening here please read the [blog post](https://www.openshift.com/blogs/build-your-own-google-maps-and-more-with-geoserver-on-openshift) to accompany this repo.

The SQL files were originally obtained from Santa Cruz county http://gis.co.santa-cruz.ca.us/file_download_site/ as shapefiles

They were then reprojected to EPSG:4326 and converted to PostGIS SQL (using ogr2ogr)

=============================

Here are the instructions to add this git repo to a blank tomcat 7 application local git repo.

Given the size of this repository in  Megabytes, it will definitely timeout and fail if you try to use it with --from-code and the rhc command line tools

	$ rhc app create geoserver tomcat7
	
	#if you are in the paid tier I highly recommend using a medium or large gear
	# $ rhc app create geoserver tomcat7 -g medium
	# $ rhc app create geoserver tomcat7 -g large
	
	
	$ cd geoserver

	$ git remote add github -m master git@github.com:thesteve0/geoserver-on-openshift.git

	$ git pull -s recursive -X theirs github master

	$ git push origin
	

This WAR file takes a *very* long time to deploy, please be patient. 

Once it works, the URL to access it will be:

http://geoserver-{your domain}.rhcloud.com/web

Please change the default username and password immediately

