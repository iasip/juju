# Overview

Selenium is a software testing framework for automating web browsers.
	[http://docs.seleniumhq.org/] 

Mozilla FireFox is a web browser that can be used for testing purposes with this charm.
	[http://www.mozilla.org/en-US/]	

PhantomJS is a headless webkit used mainly for optimizing tests of web applications.
	[http://phantomjs.org/]

# Installation

To deploy this charm you will need at a minimum: a cloud environment, a working Juju installation with a successful bootstrap.  Once bootstrapped, execute the following deploy commands: 

	juju deploy selenium
	juju deploy jenkins-selenium-example-job

Add a relation between these two charms:

	juju add-relation selenium jenkins-selenium-example-job

Expose the Selenium service:

	juju expose selenium

After these steps, a successful deployment will look similar to this (juju status):

	environment: amazon
	machines:
	  "0":
	    agent-state: started
	    dns-name: ec2-107-21-147-86.compute-1.amazonaws.com
	    instance-id: i-5c379c27
	    instance-state: running
	    series: precise
	  "1":
	    agent-state: started
	    dns-name: ec2-50-19-35-186.compute-1.amazonaws.com
	    instance-id: i-08309b73
	    instance-state: running
	    series: precise
	services:
	  selenium:
	    charm: local:precise/selenium-0
	    exposed: true
	    units:
	      selenium/0:
	        agent-state: installed
	        agent-version: 1.14.1
	        machine: "1"
	        public-address: ec2-50-19-35-186.compute-1.amazonaws.com
# General 	

As of now, before using Firefox, you must add the following environment variable for xvfb (X Virtual Framebuffer):
	
	 "export DISPLAY=:0"
 
# Configuration

Download URLs are specified in 'config.yaml'. Here you can update the versions of Selenium, PhantomJS, and FireFox. 
