<img src="index.assets/Screen Shot 2021-09-29 at 4.43.58 PM.png" alt="Screen Shot 2021-09-29 at 4.43.58 PM" style="zoom:50%;" />

## EC2

like a digital server, choose what you need in the virtul machine

## S3

Object storage service. each object stored as file with metadata and ID. With that ID, we can access whatever object that ID stores.

It enables us to upload and store and also download any file or object.

File size limit: 5GB

## Lambda

We only need to provide function to Lambda, and tell when to run it.

Zero administration. Zero configuration

Instances of the function is scalable for multiple concurent users.

## CloudFront

A web service that speeds up distribution of our static files. Can be think as a CDN.

Makes apps extremely fast when we request our HTML, CSS and JavaScript files.

Provide automatic HTTPS

## DynamoDB

noSQL database, key-value storage

# Amazon flowchart:

<img src="index.assets/Screen Shot 2021-09-29 at 4.44.14 PM.png" alt="Screen Shot 2021-09-29 at 4.44.14 PM" style="zoom:50%;" />

# Monolithic vs Micro-Services

<img src="index.assets/Screen Shot 2021-09-29 at 4.48.24 PM.png" alt="Screen Shot 2021-09-29 at 4.48.24 PM" style="zoom:50%;" />

Micro-Services advantages:

small chunks can be tested on their own, can have different developer teams on their own, and all of them can be released individually to production one at a time. Don't have to make sure that all the pieces work together.

Service level agreement(SLA): just make sure no matter what updates you do, that you give me this return data or you repond to me this way.