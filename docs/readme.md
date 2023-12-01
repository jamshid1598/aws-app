# in local
<!-- login ECR docker repository in server -->
aws ecr get-login-password --region eu-north-1 | docker login --username AWS --password-stdin 257996401114.dkr.ecr.eu-north-1.amazonaws.com

<!-- copy local files to server -->
scp -i ~/Downloads/jamshid982.pem -r $(pwd)/{compose,dc-prod.yml,env_vars,entrypoint.sh,manage.py,config,dc-prod-aws.yml,dc-staging-aws.yml,requirements} ubuntu@51.20.156.167:projects/aws-app




# in amazon server
<!-- login ECR docker repository in server -->
aws ecr get-login-password --region eu-north-1 | docker login --username AWS --password-stdin 257996401114.dkr.ecr.eu-north-1.amazonaws.com

<!-- pull images form docker registery -->
docker pull 257996401114.dkr.ecr.eu-north-1.amazonaws.com/django-ec2:backend
docker pull 257996401114.dkr.ecr.eu-north-1.amazonaws.com/django-ec2:nginx-proxy



scp -i ~/Downloads/jamshid982.pem -r $(pwd)/{dc-prod-aws.yml} ubuntu@51.20.156.167:projects/aws-app