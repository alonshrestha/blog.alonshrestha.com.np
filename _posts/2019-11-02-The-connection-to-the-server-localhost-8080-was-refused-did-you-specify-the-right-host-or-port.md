---
title: SOLVED = The connection to the server localhost8080 was refused -did you specify the right host or port ? | Kubernetes
layout: post
author: alonshrestha
categories:
- Linux
- Docker
- Kubernetes
- port
- right 
- permission
- tech
- tech tips
- Linux tips
- Installation
---

I got this error while checking the version of `kubectl`

{%highlight ruby%}

root@shrestha:/home/alon# kubectl version
Client Version: version.Info{Major:"1", Minor:"16", GitVersion:"v1.16.2", GitCommit:"c97fe5036ef3df2967d086711e6c0c405941e14b", GitTreeState:"clean", BuildDate:"2019-10-15T19:18:23Z", GoVersion:"go1.12.10", Compiler:"gc", Platform:"linux/amd64"}
The connection to the server localhost:8080 was refused - did you specify the right host or port?

{%endhighlight ruby%}

The below solution worked for me. 

{%highlight ruby%}
[alon@localhost ~]$ minikube delete 
[alon@localhost ~]$ minikube start --vm-driver none
{%endhighlight%}

First delete minikube with command `minikube delete` and start with `minikube start --vm-driver none`.

I still got the issue at `first hit`. It gets stuck at `Waiting for: apiserver` operation. This might be the issue from my internet. 
{%highlight ruby%}

⌛
  Waiting for: apiserver


💣
  Wait failed
❌
  Error: [APISERVER_TIMEOUT] waiting for apiserver: timed out waiting for the condition
💡
  Suggestion: A VPN or firewall is interfering with HTTP access to the minikube VM. Alternatively, try a different VM driver: https://minikube.sigs.k8s.io/docs/start/
📘
  Documentation: https://minikube.sigs.k8s.io/docs/reference/networking/vpn/
⁉️   Related issues:
    
▪
https://github.com/kubernetes/minikube/issues/4302

😿
  If the above advice does not help, please let us know: 
👉
  https://github.com/kubernetes/minikube/issues/new/choose
  
{%endhighlight%}

At the `second hit`. This worked for me.

{%highlight ruby%}
root@shrestha:/home/alon# minikube delete

🔄
  Uninstalling Kubernetes v1.16.2 using kubeadm ...
🔥
  Deleting "minikube" in none ...
💔
  The "minikube" cluster has been deleted.
🔥
  Successfully deleted profile "minikube"


root@shrestha:/home/alon# minikube start --vm-driver none

🙄
  minikube v1.5.2 on Ubuntu 18.04
🤹
  Running on localhost (CPUs=2, Memory=5937MB, Disk=47804MB) ...
ℹ
️   OS release is Ubuntu 18.04.3 LTS
🐳
  Preparing Kubernetes v1.16.2 on Docker '18.09.7' ...
    
▪
kubelet.resolv-conf=/run/systemd/resolve/resolv.conf
🚜
  Pulling images ...
🚀
  Launching Kubernetes ... 
🤹
  Configuring local host environment ...

⚠
️  The 'none' driver provides limited isolation and may reduce system security and reliability.
⚠
️  For more information, see:
👉
  https://minikube.sigs.k8s.io/docs/reference/drivers/none/

⚠
️  kubectl and minikube configuration will be stored in /root
⚠
️  To use kubectl or minikube commands as your own user, you may need to relocate them. For example, to overwrite your own settings, run:

    
▪
sudo mv /root/.kube /root/.minikube $HOME
    
▪
sudo chown -R $USER $HOME/.kube $HOME/.minikube

💡
  This can also be done automatically by setting the env var CHANGE_MINIKUBE_NONE_USER=true
⌛
  Waiting for: apiserver
🏄
  Done! kubectl is now configured to use "minikube"
  
  
root@shrestha:/home/alon# kubectl version
Client Version: version.Info{Major:"1", Minor:"16", GitVersion:"v1.16.2", GitCommit:"c97fe5036ef3df2967d086711e6c0c405941e14b", GitTreeState:"clean", BuildDate:"2019-10-15T19:18:23Z", GoVersion:"go1.12.10", Compiler:"gc", Platform:"linux/amd64"}
Server Version: version.Info{Major:"1", Minor:"16", GitVersion:"v1.16.2", GitCommit:"c97fe5036ef3df2967d086711e6c0c405941e14b", GitTreeState:"clean", BuildDate:"2019-10-15T19:09:08Z", GoVersion:"go1.12.10", Compiler:"gc", Platform:"linux/amd64"}


{%endhighlight%}


`Please write me in the comment if you need help.`