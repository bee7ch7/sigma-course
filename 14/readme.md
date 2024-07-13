
# install docker and docker-compose
```
sudo yum install docker -y
sudo curl -L https://github.com/docker/compose/releases/latest/download/docker-compose-$(uname -s)-$(uname -m) -o /usr/bin/docker-compose && sudo chmod +x /usr/bin/docker-compose && docker-compose --version

sudo systemctl start docker
sudo systemctl enable docker
```
`sudo docker-compose -f docker-compose-cloudwatch.yaml up`

# check logs in aws

sudo yum install amazon-cloudwatch-agent

sudo vi /opt/aws/amazon-cloudwatch-agent/etc/amazon-cloudwatch-agent.json
```
{
    "agent": {
        "metrics_collection_interval": 10,
        "logfile": "/opt/aws/amazon-cloudwatch-agent/logs/amazon-cloudwatch-agent.log"
    },
    "logs": {
        "logs_collected": {
            "files": {
                "collect_list": [
                    {
                        "file_path": "/var/log/nginx/access*",
                        "log_group_name": "{instance_id}/var/log/nginx",
                        "log_stream_name": "access.log"
                    },
                    {
                        "file_path": "/var/log/nginx/error*",
                        "log_group_name": "{instance_id}/var/log/nginx",
                        "log_stream_name": "error.log"
                    }
                ]
            }
        }
    }
}
```

sudo /opt/aws/amazon-cloudwatch-agent/bin/amazon-cloudwatch-agent-ctl -a fetch-config -m ec2 -s -c file:/opt/aws/amazon-cloudwatch-agent/etc/amazon-cloudwatch-agent.json

# elk
`cd /root/elk-stack/elk`

`docker-compose up -d`

`http://<ip_address>/`


