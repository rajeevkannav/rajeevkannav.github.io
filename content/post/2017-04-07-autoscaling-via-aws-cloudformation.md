---
layout: post
title: AWS cloudformation with AutoScalingGroup and LaunchConfiguration    
excerpt: "aws AutoScalingGroup LaunchConfiguration"
modified: 2017-04-07
tags: [aws, auto-scaling, cloudformation]
comments: true
---

#### Problem

We're currently looking into such an option to run multiple number
of ec2 instances into already running environment(VPC) with launch
configurations too.
     
    
#### Solution

           Amazon web services - Cloudformation - AutoScaling

CloudFormation is one of the coolest services from AWS at no additional charge.
You can run/start and update a full stack(collection of resources) over aws with
the help of a template written in JSON/YAML by using the AWS Management Console,
AWS Command Line Interface, or APIs. It gives developers and systems administrators
an easy way to create and manage a collection of related AWS resources,
provisioning and updating them.

    
##### Syntax and Example(s)  
 
 This example shows an Auto Scaling AWS::AutoScaling::AutoScalingGroup
 resource.
 
    {
       "Type" : "AWS::AutoScaling::AutoScalingGroup",
       "Properties" : {
          "AvailabilityZones" : [ String, ... ],
          "Cooldown" : String,
          "DesiredCapacity" : String,
          "HealthCheckGracePeriod" : Integer,
          "HealthCheckType" : String,
          "InstanceId" : String,
          "LaunchConfigurationName" : String,
          "LoadBalancerNames" : [ String, ... ],
          "MaxSize" : String,
          "MetricsCollection" : [ MetricsCollection, ... ],
          "MinSize" : String,
          "NotificationConfigurations" : [ NotificationConfigurations, ... ],
          "PlacementGroup" : String,
          "Tags" : [ Auto Scaling Tag, ... ],
          "TargetGroupARNs" : [ String, ... ],
          "TerminationPolicies" : [ String, ..., ],
          "VPCZoneIdentifier" : [ String, ... ]
       }
    }     


    "WebServerGroup" : {
       "Type" : "AWS::AutoScaling::AutoScalingGroup",
       "Properties" : {
          "AvailabilityZones" : { "Fn::GetAZs" : "" },
          "LaunchConfigurationName" : { "Ref" : "LaunchConfig" },
          "MinSize" : "2",
          "MaxSize" : "2",
          "LoadBalancerNames" : [ { "Ref" : "ElasticLoadBalancer" } ],
          "MetricsCollection": [
             {
                "Granularity": "1Minute",
                "Metrics": [
                   "GroupMinSize",
                   "GroupMaxSize"
                ]
             }
          ]
       }
    }

 This example shows an Auto Scaling AWS::AutoScaling::LaunchConfiguration
 resource.


    {
       "Type" : "AWS::AutoScaling::LaunchConfiguration",
       "Properties" : {
          "AssociatePublicIpAddress" : Boolean,
          "BlockDeviceMappings" : [ BlockDeviceMapping, ... ],
          "ClassicLinkVPCId" : String,
          "ClassicLinkVPCSecurityGroups" : [ String, ... ],
          "EbsOptimized" : Boolean,
          "IamInstanceProfile" : String,
          "ImageId" : String,
          "InstanceId" : String,
          "InstanceMonitoring" : Boolean,
          "InstanceType" : String,
          "KernelId" : String,
          "KeyName" : String,
          "PlacementTenancy" : String,
          "RamDiskId" : String,
          "SecurityGroups" : [ SecurityGroup, ... ],
          "SpotPrice" : String,
          "UserData" : String
       }
    }
    
    
    "LaunchConfig" : {
       "Type" : "AWS::AutoScaling::LaunchConfiguration",
       "Properties" : {
          "KeyName" : { "Ref" : "KeyName" },
          "ImageId" : {
             "Fn::FindInMap" : [
                "AWSRegionArch2AMI",
                { "Ref" : "AWS::Region" },
                {
                   "Fn::FindInMap" : [
                      "AWSInstanceType2Arch", { "Ref" : "InstanceType" }, "Arch"
                   ]
                }
             ]
          },
          "UserData" : { "Fn::Base64" : { "Ref" : "WebServerPort" }},
          "SecurityGroups" : [ { "Ref" : "InstanceSecurityGroup" } ],
          "InstanceType" : { "Ref" : "InstanceType" },
          "BlockDeviceMappings" : [
             {
               "DeviceName" : "/dev/sda1",
               "Ebs" : { "VolumeSize" : "50", "VolumeType" : "io1", "Iops" : 200 } 
             },
             {
               "DeviceName" : "/dev/sdm",
               "Ebs" : { "VolumeSize" : "100", "DeleteOnTermination" : "true"}
             }
          ]
       }
    } 
    
    
    
On the back-ground it will create given number of EC2 instances to current
stack following with the launch-configurations.
 
Still we're digging into AWS-CloudFormation as beginner level and continue
with major-minor details with this blog series.
  
######  And if you get stuck… [Ask Here](http://stackoverflow.com/)
                  
<sup> <b>email me</b>  [rajeevsharma86@gmail.com](#myfootnote1)</sup>
