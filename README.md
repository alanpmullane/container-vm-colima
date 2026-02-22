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

- start with more cpu (4 cores), 8g for memory and 100g for disk space
```
colima start --cpu 4 --memory 8 --disk 100
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
colima start --kubernetes --cpu 4 --memory 8 --disk 100 --runtime docker --vm-type krunkit
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


## git repo commands

### git repo setup and access

- setup ssh key
```
ssh-keygen -t rsa -b 4096 -C "<add-your-user-email-here>"
```

- after creating and accepting defaults, copy and paste id_rsa.pub contents to your github.com account'sssh keys in admin
```
cat ~/.ssh/id_rsa.pub
```

- check git user config
Run the following command to check git config and if no values or incorrect values for user.name and user.email then update to match user email used in previous step to setup
ssh key.

```
git config --global --list
```

- configure git user
Do this step only if user name and user email are not set or incorrect from previous step to check git user config.
```
git config --global user.name "<your-user-name>"
git config --global user.email "<your-user-email>"
```

- clone git repo (crete first on github.com)
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


