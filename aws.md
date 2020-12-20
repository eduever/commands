EC2 Service:

```
aws ec2 start-instances --instance-ids $instance_id --region us-west-2 --output json

aws ec2 stop-instances --instance-ids $instance_id --region us-west-2 --output json

```
