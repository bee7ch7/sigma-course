## Preparation:

Fix sysctl settings

> echo "vm.max_map_count=262144" >> /etc/sysctl.conf && sysctl -p

## How to create index templates

1. Open Stack Management
2. Go to the Index patterns
3. Choose Create index pattern --> Name: nginx-* --> time field: @timestamp

