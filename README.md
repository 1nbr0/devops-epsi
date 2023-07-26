La commande `bash docker build -t devops-app . `

```
[+] Building 0.7s (7/7) FINISHED
 => [internal] load .dockerignore                                                                                                                   0.0s
 => => transferring context: 2B                                                                                                                     0.0s
 => [internal] load build definition from Dockerfile                                                                                                0.0s
 => => transferring dockerfile: 131B                                                                                                                0.0s
 => [internal] load metadata for docker.io/library/nginx:latest                                                                                     0.6s
 => [1/2] FROM docker.io/library/nginx:latest@sha256:08bc36ad52474e528cc1ea3426b5e3f4bad8a130318e3140d6cfe29c8892c7ef                               0.0s
 => [internal] load build context                                                                                                                   0.0s
 => => transferring context: 4.99kB                                                                                                                 0.0s
 => CACHED [2/2] COPY . /usr/share/nginx/html                                                                                                       0.0s
 => exporting to image                                                                                                                              0.0s
 => => exporting layers                                                                                                                             0.0s
 => => writing image sha256:500ac95176b48b82c5862e3c5971d8123668c94e991cbc7b4997f43cdb454b06                                                        0.0s
 => => naming to docker.io/library/devops-app                                                                                                       0.0s
```

Lancer le docker via cette commande `bash docker run -p 80:80 devops-app`

![Capture d'écran du résultat](/screenshot/nginx-docker.png)
