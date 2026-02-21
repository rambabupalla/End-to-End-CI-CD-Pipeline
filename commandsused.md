# 🛠 Commands Used in CI/CD Project

## Git

git init
git add .
git commit -m "Initial commit - CI/CD pipeline project"
git branch -M main
git remote add origin https://github.com/<your-username>/jenkins-cicd-springboot-k8s.git
git push -u origin main

---

## Maven

mvn clean package

---

## Docker

docker version
docker build -t ram8243/static-web-app:${BUILD_NUMBER} .
docker image list
docker tag ram8243/static-web-app:${BUILD_NUMBER} ram8243/static-web-app:java
echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin
docker push ram8243/static-web-app:java

---

## Kubernetes

kubectl apply -f kubedeploy.yaml
kubectl get pods
kubectl get svc
kubectl get deployment
kubectl describe pod <pod-name>
kubectl logs <pod-name>
kubectl rollout status deployment/<deployment-name>
