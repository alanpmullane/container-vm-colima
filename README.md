# README

## Overview

setup and run of colima, VM container runtime on mac and linux for docker and k8s

Also supports containerd and incus as well as running ollama AI models with gpu accelerated workloads

## Details

### install

- install docker and k8s
```
brew install docker docker-compose kubectl kubectx
```

- install colima
```
brew install colima
```

### starting colima

- start options

```
colima start
```

- start with more cpu and memory
```
colima start --cpu 4 --memory 8
```

### k8s support

- start with k8s
```
colima start --kubernetes
```

### AI support

- install krunkit
```
brew tap slp/krunkit
brew install krunkit
```

- setup colima for AI models
```
colima start --runtime docker --vm-type krunkit
colima model setup
```

- start with multiple options
```
colima start --kubernetes --cpu 4 --memory 8 --runtime docker --vm-type krunkit
```

- run some models
```
colima model run gemma3

colima model run hf://tinyllama

colima model run ollama://tinyllama
```


### clean up colima instance

- stop colima
```
colima stop
```

- delete colima
```
colima delete
```


## git stuff

### git repo setup and access

- setup ssh key
```
ssh-keygen -t rsa -b 4096 -C "<add-your-user-email-here>"
```

- after creating and accepting defaults, copy and paste id_rsa.pub contents to your github.com account'sssh keys in admin
```
cat ~/.ssh/id_rsa.pub
```

- clone repo (crete first on github.com)
```
git clone git@github.com:<username>/container-vm-colima.git
```

- create a new repository on the command line
```
echo "# container-vm-colima" >> README.md
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin git@github.com:alanpmullane/container-vm-colima.git
git push -u origin main
```

- push an existing repository from the command line
```
git remote add origin git@github.com:alanpmullane/container-vm-colima.git
git branch -M main
git push -u origin main
```


