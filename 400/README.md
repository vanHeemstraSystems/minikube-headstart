# 400 - Troubleshooting

If something goes wrong during the process, try to follow the error messages. You can add the ```--alsologtostderr``` flag to get detailed error info to the console. 

Everything Minikube does is organized neatly under ```~/.minikube```. 

Here is the directory structure:

```
$ tree ~/.minikube -L 2 
/Users/${USER}/.minikube 
├── addons 
├── apiserver.crt 
├── apiserver.key 
├── ca.crt 
├── ca.key 
├── ca.pem 
├── cache 
│   ├── images 
│   ├── iso 
│   ├── kic 
│   └── preloaded-tarball 
├── cert.pem 
├── certs 
│   ├── ca-key.pem 
│   ├── ca.pem 
│   ├── cert.pem 
│   └── key.pem 
├── client.crt 
├── client.key 
├── config 
│   └── config.json
├── files 
├── key.pem 
├── logs 
│   ├── audit.json 
│   └── lastStart.txt 
├── machine_client.lock
├── machines 
│   ├── minikube 
│   ├── server-key.pem 
│   └── server.pem 
├── profiles 
│   └── minikube 
├── proxy-client-ca.crt 
├── proxy-client-ca.key 
├── proxy-client.crt 
└── proxy-client.key
 13 directories, 19 files
```
