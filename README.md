---
description: Install Minikube
---

# 1- First Step

## Minikube Installation 

#### Requirements

[https://kubernetes.io/docs/tasks/tools/install-minikube/](https://kubernetes.io/docs/tasks/tools/install-minikube/)

{% tabs %}
{% tab title="Linux" %}
To check if virtualization is supported on Linux, run the following command and verify that the output is non-empty:

```text
grep -E --color 'vmx|svm' /proc/cpuinfo
```
{% endtab %}

{% tab title="macOS" %}
To check if virtualization is supported on macOS, run the following command on your terminal.

```text
sysctl -a | grep -E --color 'machdep.cpu.features|VMX' 
```

If you see `VMX` in the output \(should be colored\), the VT-x feature is enabled in your machine.
{% endtab %}

{% tab title="Windows" %}
To check if virtualization is supported on Windows 8 and above, run the following command on your Windows terminal or command prompt.

```text
systeminfo
```

If you see the following output, virtualization is supported on Windows.

```text
Hyper-V Requirements:     VM Monitor Mode Extensions: Yes
                          Virtualization Enabled In Firmware: Yes
                          Second Level Address Translation: Yes
                          Data Execution Prevention Available: Yes
```

If you see the following output, your system already has a Hypervisor installed and you can skip the next step.

```text
Hyper-V Requirements:     A hypervisor has been detected. Features required for Hyper-V will not be displayed.
```
{% endtab %}
{% endtabs %}

### Installing Minikube

{% tabs %}
{% tab title="Linux" %}
#### Install kubectl

Make sure you have kubectl installed. You can install kubectl according to the instructions in [Install and Set Up kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl-on-linux).

#### Install a Hypervisor <a id="install-a-hypervisor"></a>

If you do not already have a hypervisor installed, install one of these now:

• [KVM](https://www.linux-kvm.org/), which also uses QEMU

• [VirtualBox](https://www.virtualbox.org/wiki/Downloads)

> **Note:** Minikube also supports a `--vm-driver=none` option that runs the Kubernetes components on the host and not in a VM. Using this driver requires [Docker](https://www.docker.com/products/docker-desktop) and a Linux environment but not a hypervisor. It is recommended to use the apt installation of docker from \([Docker](https://www.docker.com/products/docker-desktop), when using the none driver. The snap installation of docker does not work with minikube.

#### Install Minikube using a package <a id="install-minikube-using-a-package"></a>

There are _experimental_ packages for Minikube available; you can find Linux \(AMD64\) packages from Minikube’s [releases](https://github.com/kubernetes/minikube/releases) page on GitHub.

Use your Linux’s distribution’s package tool to install a suitable package.

#### Install Minikube via direct download <a id="install-minikube-via-direct-download"></a>

If you’re not installing via a package, you can download a stand-alone binary and use that.

```text
curl -Lo minikube https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64 \
  && chmod +x minikube
```

Here’s an easy way to add the Minikube executable to your path:

```text
sudo mkdir -p /usr/local/bin/
sudo install minikube /usr/local/bin/
```
{% endtab %}

{% tab title="macOS" %}
#### Install kubectl

Make sure you have kubectl installed. You can install kubectl according to the instructions in [Install and Set Up kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl-on-macos).

#### Install a Hypervisor <a id="install-a-hypervisor"></a>

If you do not already have a hypervisor installed, install one of these now:

• [HyperKit](https://github.com/moby/hyperkit)

• [VirtualBox](https://www.virtualbox.org/wiki/Downloads)

• [VMware Fusion](https://www.vmware.com/products/fusion)

#### Install Minikube <a id="install-minikube"></a>

The easiest way to install Minikube on macOS is using [Homebrew](https://brew.sh/):

```text
brew cask install minikube
```

You can also install it on macOS by downloading a stand-alone binary:

```text
curl -Lo minikube https://storage.googleapis.com/minikube/releases/latest/minikube-darwin-amd64 \
  && chmod +x minikube
```

Here’s an easy way to add the Minikube executable to your path:

```text
sudo mv minikube /usr/local/bin
```
{% endtab %}

{% tab title="Windows" %}
#### Install kubectl <a id="install-kubectl"></a>

Make sure you have kubectl installed. You can install kubectl according to the instructions in [Install and Set Up kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl-on-windows).

#### Install a Hypervisor <a id="install-a-hypervisor"></a>

If you do not already have a hypervisor installed, install one of these now:

• [Hyper-V](https://msdn.microsoft.com/en-us/virtualization/hyperv_on_windows/quick_start/walkthrough_install)

• [VirtualBox](https://www.virtualbox.org/wiki/Downloads)

> **Note:** Hyper-V can run on three versions of Windows 10: Windows 10 Enterprise, Windows 10 Professional, and Windows 10 Education.

#### Install Minikube using Chocolatey <a id="install-minikube-using-chocolatey"></a>

The easiest way to install Minikube on Windows is using [Chocolatey](https://chocolatey.org/) \(run as an administrator\):

```text
choco install minikube
```

After Minikube has finished installing, close the current CLI session and restart. Minikube should have been added to your path automatically.

#### Install Minikube using an installer executable <a id="install-minikube-using-an-installer-executable"></a>

To install Minikube manually on Windows using [Windows Installer](https://docs.microsoft.com/en-us/windows/desktop/msi/windows-installer-portal), download [`minikube-installer.exe`](https://github.com/kubernetes/minikube/releases/latest/download/minikube-installer.exe) and execute the installer.

#### Install Minikube via direct download <a id="install-minikube-via-direct-download"></a>

To install Minikube manually on Windows, download [`minikube-windows-amd64`](https://github.com/kubernetes/minikube/releases/latest), rename it to `minikube.exe`, and add it to your path.
{% endtab %}
{% endtabs %}

### Cleanup Local State

If you have previously installed minikube, and run:

```text
minikube start
```

And this command returns an error:

```text
machine does not exist
```

You need to clear minikube’s local state:

```text
minikube delete
```

