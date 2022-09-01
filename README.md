# podman
kubectl apply -f pod.yaml
####
kubectl exec -it podman-priv -- sh
#### install wizcli into the containet for scaninng
curl -o wizcli https://wizcli.test.wiz.io/wizcli
####
chmod +x wizcli
####Set up the registry config file
podman run ubi8 echo hello
### set up environment
WIZ_ENV="test"
#### auth with the wiz
./wizcli auth --id xxxxxx --secret xxxxxxxx
### start the podman service and expose the sock
podman system service --time=0 & export DOCKER_HOST="unix:/run/podman/podman.sock"
#### pulling the image into the container
podman pull docker.io/library/mongo:latest
### scan the image
DOCKER_HOST=unix:///run/podman/podman.sock  ./wizcli docker scan --image mongo:latest
