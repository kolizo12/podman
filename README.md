# podman
kubectl apply -f pod.yaml
===
kubectl exec -it podman-priv -- sh
===
curl -o wizcli https://wizcli.test.wiz.io/wizcli
===
chmod +x wizcli
====
podman run ubi8 echo hello
====
WIZ_ENV="test"
===
./wizcli auth --id xxxxxx --secret xxxxxxxx
====
podman system service --time=0 & export DOCKER_HOST="unix:/run/podman/podman.sock"
===
podman pull docker.io/library/mongo:latest
====
DOCKER_HOST=unix:///run/podman/podman.sock  ./wizcli docker scan --image mongo:latest
