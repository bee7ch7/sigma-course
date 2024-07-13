## AWS CloudWatch Logs

docker-compose.yml example:

```sh
version: '3'
services:
    webserver:
        image: nginx:alpine
        ports:
            - 80:80
        logging:
            driver: awslogs
            options:
                awslogs-region: xxx
                awslogs-group: xxx
                awslogs-stream: xxx
```
------------------------------------

# AWS CloudWatch 
* Setup simple application (nginx, or whatever) logging aggregation
* Configure metric filter
* Configure email alerting for specific word/string in the logs

Usefull links:
- [What is Amazon CloudWatch Logs?](https://docs.aws.amazon.com/AmazonCloudWatch/latest/logs/WhatIsCloudWatchLogs.html)
- [Creating metrics from log events using filters](https://docs.aws.amazon.com/AmazonCloudWatch/latest/logs/MonitoringLogData.html)
- [Filter and pattern syntax](https://docs.aws.amazon.com/AmazonCloudWatch/latest/logs/FilterAndPatternSyntax.html)

# ELK Stack
* Deploy existing example, play with existing logs and "beats"
* Using existing configuration parse logs from nginx using [GROK](https://www.elastic.co/guide/en/logstash/current/plugins-filters-grok.html) filter from the Logstash (*)
* Add additional "beat" Packetbeat and configure traffic logging
* Configure Logstash to fetch ALB/Cloudfront/etc (on your choise) logs from S3 bucket

Usefull links:
- [Grok Debug](http://grokdebug.herokuapp.com/)
 
