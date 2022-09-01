# podman
kubectl apply -f pod.yaml
####
kubectl exec -it podman-priv -- sh
#### install wizcli into the containet for scaninng

curl -o wizcli https://wizcli.test.wiz.io/wizcli
---
####
chmod +x wizcli
### set up environment#
export WIZ_ENV="test"
#### auth with the wiz#
./wizcli auth --id xxxxxx --secret xxxxxxxx
### start the podman service 
podman system service --time=0
#### pulling the image into the container
podman pull docker.io/library/mongo:latest
### scan the image
DOCKER_HOST=unix:///run/podman/podman.sock  ./wizcli docker scan --image mongo:latest
