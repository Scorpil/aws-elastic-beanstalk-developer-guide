# eb init<a name="eb3-init"></a>

## Description<a name="eb3-initdescription"></a>

Sets default values for Elastic Beanstalk applications created with EB CLI by prompting you with a series of questions\.

**Note**  
The values you set with `init` apply only to the current directory and repository\.

## Syntax<a name="eb3-initsyntax"></a>

 eb init 

 eb init *application\-name* 

## Options<a name="eb3-initoptions"></a>

If you run eb init without specifying the `--platform` option, the EB CLI prompts you to enter a value for each setting\.

**Note**  
To use eb init to create a new key pair, you must have `ssh-keygen` installed on your local machine and available from the command line\.


****  

|  Name  |  Description  |  | 
| --- | --- | --- | 
|  `-i` `--interactive`  |  Forces EB CLI to prompt you to provide a value for every eb init command option\.  The `init` command prompts you to provide values for eb init command options that do not have a \(default\) value\. After the first time you run the eb init command in a directory, EB CLI might not prompt you about any command options\. Therefore, use the `--interactive` option when you want to change a setting that you previously set\.   |  | 
|  `-k` *keyname* `--keyname` *keyname*  |  The name of the Amazon EC2 key pair to use with the Secure Shell \(SSH\) client to securely log in to the Amazon EC2 instances running your Elastic Beanstalk application\.  |  | 
|  `--modules folder-1 folder-2`  |  List of child directories to initialize\. Only for use with [Compose Environments](ebcli-compose.md)\.  |  | 
|  `-p` *platform\-configuration*  `--platform` *platform\-configuration*  |  The [platform version \(configuration\)](concepts.platforms.md) to use\. You can specify a platform name, a platform name and version, a solution stack name, or a solution stack ARN\. For example: [\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/elasticbeanstalk/latest/dg/eb3-init.html) Use [`eb platform list`](eb3-platform.md) to get a list of available configurations\. Specify the `--platform` option to skip interactive configuration\.  When you specify this option, then EB CLI does not prompt you for values for any other options\. Instead, it assumes default values for each option\. You can specify options for anything for which you do not want to use default values\.   |  | 
|  `--source codecommit/repository-name/branch-name`  |  CodeCommit repository and branch\. See [Using the EB CLI with AWS CodeCommit](eb-cli-codecommit.md)\.  |  | 
|  `-﻿-﻿tags key1=value1[,key2=value2 ...]`  |  Tag your application\. Tags are specified as a comma\-separated list of `key=value` pairs\. For more details, see [Tagging Applications](applications-tagging.md)\.  | 
|  [Common options](eb3-cmd-options.md)  |  |  | 

## CodeBuild Support<a name="eb3-init-codebuild"></a>

If you run eb init in a folder that contains a [buildspec\.yml](https://docs.aws.amazon.com/codebuild/latest/userguide/build-spec-ref.html) file, Elastic Beanstalk parses the file for an eb\_codebuild\_settings entry with options specific to Elastic Beanstalk\. For information about CodeBuild support in Elastic Beanstalk, see [Using the EB CLI with AWS CodeBuild](eb-cli-codebuild.md)\.

## Output<a name="eb3-initoutput"></a>

If successful, the command guides you through setting up a new Elastic Beanstalk application through a series of prompts\.

## Example<a name="eb3-initexample"></a>

The following example request initializes EB CLI and prompts you to enter information about your application\. Replace the red placeholder text with your own values\.

```
$ eb init -i
Select a default region
1) us-east-1 : US East (N. Virginia)
2) us-west-1 : US West (N. California)
3) us-west-2 : US West (Oregon)
4) eu-west-1 : EU (Ireland)
5) eu-central-1 : EU (Frankfurt)
6) ap-south-1 : Asia Pacific (Mumbai)
7) ap-southeast-1 : Asia Pacific (Singapore)
8) ap-southeast-2 : Asia Pacific (Sydney)
9) ap-northeast-1 : Asia Pacific (Tokyo)
10) ap-northeast-2 : Asia Pacific (Seoul)
11) sa-east-1 : South America (São Paulo)
12) cn-north-1 : China (Beijing)
13) cn-northwest-1 : China (Ningxia)
14) us-east-2 : US East (Ohio)
15) ca-central-1 : Canada (Central)
16) eu-west-2 : EU (London)
17) eu-west-3 : EU (Paris)
18) eu-north-1 : EU (Stockholm)
19) ap-east-1 : Asia Pacific (Hong Kong)
20) me-south-1 : Middle East (Bahrain)
(default is 3): 3

Select an application to use
1) HelloWorldApp
2) NewApp
3) [ Create new Application ]
(default is 3): 3

Enter Application Name
(default is "tmp"):
Application tmp has been created.

It appears you are using PHP. Is this correct?
(y/n): y

Select a platform version.
1) PHP 5.5
2) PHP 5.4
3) PHP 5.3
(default is 1): 1
Do you want to set up SSH for your instances?
(y/n): y

Select a keypair.
1) aws-eb
2) [ Create new KeyPair ]
(default is 2): 1
```