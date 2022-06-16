# OpenRefine

This is a fork of https://github.com/wetneb/openrefine-wikibase. 

### Generate image and push to ECR

Build image (on Apple Silicon)(dev)
```
docker buildx build --platform linux/amd64 . -t 294118183257.dkr.ecr.eu-west-1.amazonaws.com/linkedopendata-openrefine-reconciliation
 
```

Login on ECR repository(dev)
```
aws ecr get-login-password --region eu-west-1 | docker login --username AWS --password-stdin 294118183257.dkr.ecr.eu-west-1.amazonaws.com
```

Push to repository(dev)
```
docker push 294118183257.dkr.ecr.eu-west-1.amazonaws.com/linkedopendata-openrefine-reconciliation
```

If you change the image tag you need to update the manifest on the gitops repository, 
otherwise you can only delete the pod on the cluster and it will regenerate with the new version.
