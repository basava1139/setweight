Argocd 

Argo CD is a declarative, GitOps continuous delivery tool for Kubernetes.

Prerequisites Tools Installed :
  - Docker
  - Git
  - Kubernetes
 
Task 1: Setup and Configuration

Create a GitRepository: Create a Github repository and host your source code in the same repository.
         
        Github Repo Link: https://github.com/basava1139/setweight/

2.    Install Argo CD on Your Kubernetes Cluster:
       minikube version: v1.32.0
     
3.   Install Argo Rollouts:
      kubectl-argo-rollouts: v1.6.0+7eae71e



Task 2: Creating the GitOps Pipeline:

1.  Dockerize the Application:
     Custom docker image code: 
        From nginx
        COPY ./index.html  /usr/share/nginx/html/index.html

        - From command , you are instructing Docker to use the official NGINX Docker image as the starting point for your 
          custom image.
        - COPY command, It copies the index.html file from the current directory of the Docker build context 
           into the /usr/share/nginx/html/ directory within the Docker image.


      index.html contains a below code
         <!DOCTYPE html>
         <html>
         <head>
             <title>Green Background - Version 2</title>
             <style>
                body {
                  background-color: green;
                    }
        
                    .version {
                      font-size: 40px;
                      text-align: center;
                      margin-top: 200px;
                      color: white;
                      text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.5);
                    }
             </style>
        </head>
        <body>
           <div class="version">Argo-Rollouts Demo by Basava</div>
           <div class="version">Version 2</div>
        </body>
        </html>



     docker build -t basu1139/canarydeploy:v2 .
       This command will build a Docker image using the Dockerfile found in the current directory  and tag it with 
       basu1139/canarydeploy:v2.
      
     DockerImage: basu1139/canarydeploy:v2                       
        
     To pull an image to local machine: 
     
     docker pull docker.io/basu1139/canarydeploy:v2


3.  Deploy the Application Using Argo CD:
     
     Install argocd by using following command:
      -kubectl create namespace argocd
      -kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/. argo-cd/stable/manifests/install.yaml






