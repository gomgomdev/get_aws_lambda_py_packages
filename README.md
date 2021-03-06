# Python 3 PIP Packaging Tool for AWS Lambda
[![made-with-python](https://img.shields.io/badge/Made%20with-Python-1f425f.svg)](https://www.python.org/)
[![Working on AWS !](https://img.shields.io/badge/Working%20on-AWS-orange.svg)](https://aws.amazon.com)
[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)
[![Maintenance](https://img.shields.io/badge/Maintained%3F-yes-green.svg)](https://github.com/gomgomdev/pypubdata/pulse)
[![Ask Me Anything !](https://img.shields.io/badge/Ask%20me-anything-1abc9c.svg)](https://github.com/gomgomdev/pypubdata/issues)

한국어 설명(README.ko.md)은 [여기](https://github.com/gomgomdev/get_aws_lambda_py_packages/blob/master/README.ko.md)

## Intro
**This AWS Lambda Python script works for making pip package of Amazon Linux.**
If you needs Amazon Linux's pip package for AWS Lambda Python script, this tool will help you.

Such as, if you needs 'requests' and 'PyMySQL' pip packages for your AWS Lambda, you have to insert these packages in your AWS Lambda script.

If you are using Amazon Linux, it's quite easy to you because you can make virtualenv and get site-packages, but if you don't you may turn on EC2 instance of Amazon Linux.  
But you have to pay 1 hour's price *JUST FOR GETTING PIP PACKAGES*.

This tool makes pip packages of Amazon Linux on AWS Lambda, and upload packages to your S3.
You just download packages file, and you can put it in your AWS Lambda script. How easy!

## How To Use
1. **Make S3 Bucket for uploading packages.** If you have your bucket already, you can use that also.
2. Make AWS Lambda Function for Python 3.6, and **this Lambda's rule needs S3 access policy(this script will upload object.)**
3. **Copy my script of 'lambda_function.py'** to your default lambda script.
4. **Make test event for this lambda, and write test event's JSON as follow.**
```json
{
  "packages_name": ["your_pip_package1_name", "your_pip_package2_name", "and more ..."],
  "s3_bucket_name": "your_s3_bucket_name",
  "s3_path": "s3_path (NOT ESSENTIAL, default is none)",
  "file_name": "file_name.tar (NOT ESSENTIAL, NEED '.tar' EXTENSION, default is aws-linux-pip-packages.tar)"
}
```
5. And in default settings, you can change lambda's memory and limit time.  
In general, **I recommend '192MB memory / 2 minutes limit' to avoid forced termination.**
6. Finally, If you **push 'Test'**, your lambda script will work.
7. After finishing lambda, **check your S3 bucket and directory, maybe you can see tar file.**
8. **Use this file to your AWS Lambda script. Done!**

## Contact
I'm not good programmer and I know this script is shoddy.  
But if you have questions to me, I'm welcoming your questions (but still don't know I can answer. :P)

Please send to me email or open a issue.

Made by Gomgom (https://gomgom.io, dev@gomgom.io)