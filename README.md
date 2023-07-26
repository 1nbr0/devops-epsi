# Construire une machine Nginx avec Docker

## Prérequis

- Docker
- Une machine avec un accès à Internet

## Instructions

1. Créez un nouveau répertoire pour votre projet.
2. Dans le répertoire, créez un fichier nommé `Dockerfile`.
3. Copiez et collez le code suivant dans le fichier `Dockerfile`.

```
FROM nginx:latest

COPY . /usr/share/nginx/html

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
```

4. Exécutez la commande suivante pour construire l'image Docker.

`bash docker build -t devops-app . `

#### Résultat console :

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

5. Une fois l'image construite, vous pouvez l'exécuter en exécutant la commande suivante.

`bash docker run -p 80:80 devops-app`

6. Une fois le conteneur démarré, vous pouvez accéder à votre application Nginx sur l'adresse http://localhost:80/.

#### Résultat :

![Capture d'écran du résultat](/screenshot/nginx-docker.png)

# Création d'une application Jenkins avec docker

## Prérequis

- Docker
- Une machine avec un accès à Internet

## Instructions

1. Créez un nouveau répertoire pour votre projet.
2. Dans le répertoire, créez un fichier nommé `Dockerfile`.
3. Copiez et collez le code suivant dans le fichier `Dockerfile`.

```
FROM jenkins/jenkins

ENV JAVA_OPTS="-Djenkins.install.runSetupWizard=false"

RUN jenkins-plugin-cli

EXPOSE 8080

EXPOSE 50000
```

4. Exécutez la commande suivante pour construire l'image Docker.

`bash docker build -t jenkins-app .`

#### Résultat console :

```
[+] Building 28.3s (7/7) FINISHED
 => [internal] load build definition from Dockerfile                                                                                    0.0s
 => => transferring dockerfile: 167B                                                                                                    0.0s
 => [internal] load .dockerignore                                                                                                       0.0s
 => => transferring context: 2B                                                                                                         0.0s
 => [internal] load metadata for docker.io/jenkins/jenkins:latest                                                                       1.8s
 => [auth] jenkins/jenkins:pull token for registry-1.docker.io                                                                          0.0s
 => [1/2] FROM docker.io/jenkins/jenkins@sha256:265b6607c75f4ca47b71375517cb5c7aa5c59b36c2496a4bbb30850375348f1f                       25.7s
 => => resolve docker.io/jenkins/jenkins@sha256:265b6607c75f4ca47b71375517cb5c7aa5c59b36c2496a4bbb30850375348f1f                        0.0s
 => => sha256:4a9e1c4c0155f50106eda003c94d7b13ae17d74ba608655768bb92c33c8b0407 51.63MB / 51.63MB                                       19.5s
 => => sha256:29279ac7c19f9c667f1c6b07bfba6fba20ca0d945b9fbc6edad6f75d13361fae 53.70MB / 53.70MB                                        7.7s
 => => sha256:d27b54177ee9b259b66644325d9a46f5681f9d9e11040c3c2134c548ed7d505d 13.09kB / 13.09kB                                        0.0s
 => => sha256:3e5948d051eb85a8d4453674a45b625d206963604090b51f4a7f2bd053613253 2.77kB / 2.77kB                                          0.0s
 => => sha256:e401a386cb75a227d24361481c1346978289302018e80577a15b081430ee269b 8.38MB / 8.38MB                                          5.3s
 => => sha256:265b6607c75f4ca47b71375517cb5c7aa5c59b36c2496a4bbb30850375348f1f 3.12kB / 3.12kB                                          0.0s
 => => sha256:ea1e5d41a11dbfab7bf1ffff084a35d4a563eae24f8fb5894efb91a70bd641fb 1.22kB / 1.22kB                                          5.5s
 => => sha256:44620243f5cbd73cb2d2425446f5b5536f137a49eedb09c606630d35c6187cfd 183B / 183B                                              5.8s
 => => sha256:e24e8ea25b5882ba322217d94140bc8030ebbbcc78943dbf41daf317127bdd6d 89.33MB / 89.33MB                                       24.5s
 => => extracting sha256:29279ac7c19f9c667f1c6b07bfba6fba20ca0d945b9fbc6edad6f75d13361fae                                               1.2s
 => => sha256:3c4de42f7681de3f26f0aa11cc304ba33e31d316e16b0e0b8579b4790ef68736 187B / 187B                                              8.0s
 => => sha256:9dcdb9588d3ecca3f7c3489d5c3db37ef8640cd01c28578d6111ad67b3ba8d9e 6.09MB / 6.09MB                                          9.5s
 => => sha256:10008f2913ea3afe4a844cd2b02f1e8a44c3a56e173c2107b9c719284726e4ee 75.38MB / 75.38MB                                       21.8s
 => => sha256:34f29d8298bf68680298c1c9579c3e7d1c87204c950ca6b7e928bf535266a131 1.92kB / 1.92kB                                         20.0s
 => => extracting sha256:4a9e1c4c0155f50106eda003c94d7b13ae17d74ba608655768bb92c33c8b0407                                               1.0s
 => => sha256:93b029a50eaef57cf8b288b7664e0ad624aa7d0c7ad4894f0b531ef6924d1513 1.16kB / 1.16kB                                         20.3s
 => => sha256:548a13bccc6c9b6cf7d114f6a006b5d04da5485edd311f4d6c89ed66342a1c72 368B / 368B                                             20.6s
 => => sha256:437a5b934e8bb456841a2af81792049289a182d355e048991c1dc9315c138da9 264B / 264B                                             20.8s
 => => extracting sha256:e401a386cb75a227d24361481c1346978289302018e80577a15b081430ee269b                                               0.1s
 => => extracting sha256:ea1e5d41a11dbfab7bf1ffff084a35d4a563eae24f8fb5894efb91a70bd641fb                                               0.0s
 => => extracting sha256:44620243f5cbd73cb2d2425446f5b5536f137a49eedb09c606630d35c6187cfd                                               0.0s
 => => extracting sha256:e24e8ea25b5882ba322217d94140bc8030ebbbcc78943dbf41daf317127bdd6d                                               0.3s
 => => extracting sha256:3c4de42f7681de3f26f0aa11cc304ba33e31d316e16b0e0b8579b4790ef68736                                               0.0s
 => => extracting sha256:9dcdb9588d3ecca3f7c3489d5c3db37ef8640cd01c28578d6111ad67b3ba8d9e                                               0.1s
 => => extracting sha256:10008f2913ea3afe4a844cd2b02f1e8a44c3a56e173c2107b9c719284726e4ee                                               0.4s
 => => extracting sha256:34f29d8298bf68680298c1c9579c3e7d1c87204c950ca6b7e928bf535266a131                                               0.0s
 => => extracting sha256:93b029a50eaef57cf8b288b7664e0ad624aa7d0c7ad4894f0b531ef6924d1513                                               0.0s
 => => extracting sha256:548a13bccc6c9b6cf7d114f6a006b5d04da5485edd311f4d6c89ed66342a1c72                                               0.0s
 => => extracting sha256:437a5b934e8bb456841a2af81792049289a182d355e048991c1dc9315c138da9                                               0.0s
 => [2/2] RUN jenkins-plugin-cli                                                                                                        0.7s
 => exporting to image                                                                                                                  0.0s
 => => exporting layers                                                                                                                 0.0s
 => => writing image sha256:a620c57aa657e723f085757fb257127b099301aa79d2faad8b03ce969edab3af                                            0.0s
 => => naming to docker.io/library/jenkins-app                                                                                          0.0s
```

5. Une fois l'image construite, vous pouvez l'exécuter en exécutant la commande suivante.

`bash docker run -p 8080:8080 -p 50000:50000 jenkins-app`

6. Une fois le conteneur démarré, vous pouvez accéder à votre application Nginx sur l'adresse http://localhost:8080/

#### Résultat :

![Capture d'écran du résultat](/screenshot/jenkins-docker.png)

## Screenshots manipulation jenkins :

### Configuration pipeline sur jenkins

1. Ajout du repo github pour récupérer le fichier Jenkinsfile lors du build

![Capture d'écran du résultat](/screenshot/config-pipeline.png)

2. Build la pipeline

![Capture d'écran du résultat](/screenshot/sortie-console-pipeline.png)

3. Sortie complète de la console

```
Started by user unknown or anonymous
Obtained Jenkinsfile from git https://github.com/1nbr0/devops-epsi
[Pipeline] Start of Pipeline
[Pipeline] node
Running on Jenkins in /var/jenkins_home/workspace/p1
[Pipeline] {
[Pipeline] stage
[Pipeline] { (Declarative: Checkout SCM)
[Pipeline] checkout
Selected Git installation does not exist. Using Default
The recommended git tool is: NONE
No credentials specified
Cloning the remote Git repository
Cloning repository https://github.com/1nbr0/devops-epsi
 > git init /var/jenkins_home/workspace/p1 # timeout=10
Fetching upstream changes from https://github.com/1nbr0/devops-epsi
 > git --version # timeout=10
 > git --version # 'git version 2.30.2'
 > git fetch --tags --force --progress -- https://github.com/1nbr0/devops-epsi +refs/heads/*:refs/remotes/origin/* # timeout=10
 > git config remote.origin.url https://github.com/1nbr0/devops-epsi # timeout=10
 > git config --add remote.origin.fetch +refs/heads/*:refs/remotes/origin/* # timeout=10
Avoid second fetch
 > git rev-parse refs/remotes/origin/main^{commit} # timeout=10
Checking out Revision 6b9c73f843f90dcf9942eb0f3ad419d58c991952 (refs/remotes/origin/main)
 > git config core.sparsecheckout # timeout=10
 > git checkout -f 6b9c73f843f90dcf9942eb0f3ad419d58c991952 # timeout=10
Commit message: "ajout jenkinsfile"
First time build. Skipping changelog.
[Pipeline] }
[Pipeline] // stage
[Pipeline] withEnv
[Pipeline] {
[Pipeline] stage
[Pipeline] { (Build)
[Pipeline] echo
Exécution de l'étape de build
[Pipeline] }
[Pipeline] // stage
[Pipeline] stage
[Pipeline] { (Hello1)
[Pipeline] sh
+ echo hello1
hello1
[Pipeline] }
[Pipeline] // stage
[Pipeline] stage
[Pipeline] { (sleep)
[Pipeline] sh
+ sleep 60
[Pipeline] }
[Pipeline] // stage
[Pipeline] stage
[Pipeline] { (Hello2)
[Pipeline] sh
+ echo hello2
hello2
[Pipeline] }
[Pipeline] // stage
[Pipeline] }
[Pipeline] // withEnv
[Pipeline] }
[Pipeline] // node
[Pipeline] End of Pipeline
Finished: SUCCESS
```
