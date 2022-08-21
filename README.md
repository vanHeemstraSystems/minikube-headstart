minikube-headstart
# Minikube - Headstart

Based on "Creating a single-node cluster with Minikube" at https://subscription.packtpub.com/book/programming/9781839211256/2

## 100 - Introduction

See [README.md](./100/README.md)

## 200 - Requirements

### 100 - Getting ready

There are some prerequisites to install before you can create the cluster itself. These include VirtualBox, the kubectl command-line interface to Kubernetes, and, of course, Minikube itself. Here is a list of the latest versions at the time of writing:

- VirtualBox: https://www.virtualbox.org/wiki/Downloads
- Kubectl: https://kubernetes.io/docs/tasks/tools/install-kubectl/
- Minikube: https://kubernetes.io/docs/tasks/tools/install-minikube/

### 200 - On Windows
Install VirtualBox and make sure kubectl and Minikube are on your path. I personally just throw all command-line programs I use into ```c:```. You may prefer another approach. I use the excellent ConEMU to manage multiple consoles, terminals, and SSH sessions. It works with Command Prompt, PowerShell, PuTTY, Cygwin, msys, and Git-Bash. It does not get much better than that on Windows.

With Windows 10 Pro, you have the option to use the Hyper-V hypervisor. This is technically a better solution than VirtualBox, but it requires the Pro version of Windows and is completely Windows-specific. By using VirtualBox, these instructions are universal and will be easy to adapt to other versions of Windows, or other operating systems altogether. If you have Hyper-V enabled, you must disable it because VirtualBox cannot coexist with Hyper-V.

I recommend using PowerShell in administrator mode. You can add the following alias and function to your PowerShell profile:

```
Set-Alias -Name k -Value kubectl
function mk
{
  minikube-windows-amd64 `
  --show-libmachine-logs `
  --alsologtostderr      `
  @args
}
```

### 300 - On macOS
On macOS, you have the option of using HyperKit instead of VirtualBox:

```
$ curl -LO https://storage.googleapis.com/minikube/releases/latest/docker-machine-driver-hyperkit \
  && chmod +x docker-machine-driver-hyperkit \
  && sudo mv docker-machine-driver-hyperkit /usr/local/bin/ \
  && sudo chown root:wheel /usr/local/bin/docker-machine-driver-hyperkit \
  && sudo chmod u+s /usr/local/bin/docker-machine-driver-hyperkit
```

Check if you have kubectl installed.
```
$ kubectl version --output=yaml
```

Install kubectl if not already installed, see: https://kubernetes.io/docs/tasks/tools/install-kubectl/

Check if you have minikube installed:
```
$ minikube version
```

Install minikube if not already installed, see: https://kubernetes.io/docs/tasks/tools/install-minikube/

You can add aliases to your ```.bashrc``` file (similar to the PowerShell alias and function on Windows):

```
alias k='kubectl'
alias mk='/usr/local/bin/minikube'
```

Reload your profile file:
```
cd ~
source ./bashrc
```

If you chose HyperKit instead of VirtualBox, you need to add the flag ```--vm-driver=hyperkit``` when starting the cluster.

It is also important to disable any VPN when using HyperKit.

Now, you can use ```k``` and ```mk``` and type less. The flags to Minikube in the mk function provide better logging and direct it to the console in addition to files (similar to tee).

Type ```mk version``` to verify Minikube is correctly installed and functioning:

```
$ mk version
minikube version: v1.26.1
```

Type ```k version --output=yaml``` to verify kubectl is correctly installed and functioning:

```
$ k version --output=yaml
Client Version: version.Info{Major:"1", Minor:"24", GitVersion:"v1.24.1", GitCommit:"641856db18352033a0d96dbc99153fa3b27298e5", GitTreeState:"clean", BuildDate:"2020-05-24T12:26:197Z", GoVersion:"go1.18.2", Compiler:"gc", Platform:"darwin/amd64"}
kustomizeVersion: v4.5.4

The connection to the server localhost:8080 was refused — did you specify the right host or port?
Unable to connect to the server: dial tcp 192.168.99.100:8443: getsockopt: operation timed out
```

Do not worry about the error on the last line. There is no cluster running, so kubectl cannot connect to anything. That is expected.

You can explore the available commands and flags for both Minikube and kubectl. I will not go over each command, only the commands I use.

### 400 - Creating the cluster
The Minikube tool supports multiple versions of Kubernetes. At the time of writing, the latest version is 1.26.1, which is also the default:














