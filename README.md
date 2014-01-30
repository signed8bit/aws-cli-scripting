AWS CLI Scripting
=================

A collection of useful (to me) scripts for interacting with AWS resources using both [_aws cli_](http://aws.amazon.com/cli/) and [_jq_](http://stedolan.github.io/jq/). As you might expect, both of these are required along with the ability to run Bash scripts in a typical *nix environment. 

Installation
============

Copy the scripts to a location on your path and make sure they are executable.

Scripts
=======

ec2-ssh
-------

A convenient way to SSH into an EC2 instance by referencing the value of an instance's "Name" tag. 

    Usage: ec2-ssh [-p profile] [-u user] instance_name
    
_Profile_ is a named profile as found in your _~/.aws/config_ file. Instead of the command line option, you may specify an environment variable called "EC2\_SSH\_PROFILE". If neither are specified, "default" is used.

_User_ is the user who will be referenced when connecting to the instance. Instead of the command line option, you may specify an environment variable called "EC2\_SSH\_USER". If neither are specified, the current user is used.

_Instance Name_ is the name of the instance to connect to as specified in the "Name" tag. If more than one instance is matched, the available instances will be displayed and one can be selected.

The script prefers to connect to an instance using the specified public DNS name. If no public DNS name is available, the instance's private IP address is used. Any needed keys are expected to be located in your _~/.aws/config_ directory.

    % ls ~/.aws
    config				my-key.pem

