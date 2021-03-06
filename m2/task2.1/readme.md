# Report task 2.1

**Dmytro Steblyna**

## PART 1. The most popular hypervisors and the main differences between them:

**There are 2 different types of hypervisors that can be used for virtualization.**  

 
<br />
<p align="center">
  <img src="https://networklessons.com/wp-content/uploads/2018/12/hypervisor-type-1-type-2.png" alt="Hypervisors: type 1 vs type 2" width="550"/>
</p>


**Type 1:** a hypervisor is on bare metal. VM resources are scheduled directly to the hardware by the hypervisor. 

- VMware vSphere Hypervisor
- Microsoft Hyper-V
- Citrix XenServer
- KVM

**Type 2:** a hypervisor is hosted. VM resources are scheduled against a host operating system, which is then executed against the hardware.

- Oracle VirtualBox
- VMware Workstation Pro
- Parallels
- Qemu

**One of the best features of Type 1 hypervisors is that they allow for over-allocation of physical resources.**
With Type 1 hypervisors, you can assign more resources to your virtual machines than you have available. For example, if your server has 64 GB of RAM and 8 VMs, you can assign 12 GB of RAM to each of them. This totals to 96 GB of RAM, but the virtual machines themselves will not actually consume all 12 GB from the physical server. The VMs think they have 12 GB, when in reality they only use the amount of RAM they need to perform certain tasks.


## PART 2. WORK WITH VIRTUALBOX

**1. First run VirtualBox and Virtual Machine (VM).** 

**Firstly, I downloaded VirtualBox, installed Ubuntu on it, and got acquainted with the possibilities of managing a virtual machine.**

<p align="center"><img src="screenshots/1.png" height="250"/></p>

**Then I cloned this virtual machine and created a group of two machines. 
Groups enable us to manage and perform functions on VMs collectively, as well as individually.**

<p align="center"><img src="screenshots/2.png" height="180"/></p>

**For VM1, I installed updates and VirtualBox drivers, created some files, added some images, and changed the background.
Changing the state of the VM, I took several different snapshots, forming a branched tree of snapshots. 
The way snapshots work is very similar to how Git works.**

<p align="center"><img src="screenshots/3.png" width="400"/>
<img src="screenshots/4.png" width="400"/></p>

**I exported VM1 and saved it as the ubuntu_steblyna.ova file. 
Then I created a new VM by importing the ubuntu_steblyna.ova file.**

<p align="center"><img src="screenshots/5.png" width="680"/>
<img src="screenshots/6.png" width="320"/>
</p>


**2. Configuration of virtual machines** 

**I explored VM configuration options (like general settings, system settings, display, storage, audio, network and etc.).
Then I configured the USB to connect a USB flash drive on the host machine to the VM.**
<p align="center">
 <img src="screenshots/10.png" width="550"/>
 <img src="screenshots/11.png" width="350"/>
</p>

**Also, I configured a shared folder to exchange data between the virtual machine and the host.** 
<p align="center"><img src="screenshots/12.png" height="280"/></p>

**For correct access I had to add myself to the shared folders group in the VM. I did it by running the command:**
```sh
sudo adduser $USER vboxsf
```
<p align="center"><img src="screenshots/13.png" height="240"/>
<img src="screenshots/14.png" height="100"/></p>



**3. Work with CLI through VBoxManage.** 

**I opened the cmd command line and executed basic VBoxManage commands like list, showvminfo, createvm, startvm, modifyvm, clonevm, snapshot, controlvm. Here are screenshots of some commands execution.**
```sh
VBoxManage list vms
```
<p><img src="screenshots/15.png" width="700"/></p>

```sh
VBoxManage startvm
```

<p><img src="screenshots/16.png" width="700"/></p>

```sh
VBoxManage snapshot
```

<p><img src="screenshots/17.png" width="700"/></p>

```sh
VBoxManage controlvm
```
<p><img src="screenshots/18.png" width="700"/></p>

```sh
VBoxManage modifybm
```

<p><img src="screenshots/19.png" width="700"/></p>

**Also, I created a network between VM1 and VM2 and checked such configurations as: NAT, NAT Network, Bridged adapter, Internal network and Host-only adapter.**

**NAT:** Host<=>VM1; Host<=>VM2; VM1<|X|>VM2.

**NAT Network:** Host<=>VM1; Host<=>VM2; VM1<=>VM2.

**Bridged adapter:** Router<=>Host; Router<=>VM1; Router<=>VM2; Host<=>VM1; Host<=>VM2; VM1<=>VM2. (Host, VM1 and VM2 are in one Network.

**Host-only adapter:** Host works like a Router. Host<=>(VM1<=>VM2).

**Internal network:** Host<|X|>(VM1<=>VM2) (It's a network only between VMs).




## PART 3. WORK WITH VAGRANT


**I installed vagrant, initialized the environment with the default Vagrant box (hashicorp/precise64).
Than I ran the VM and connected to it using the program PuTTY, via SSH.
I recorded the date and time, then stopped and deleted the created VM.
I also experimented with the Vagrantfile, changing its configuration. 
And Vagrant turned out to be very similar to Docker.**

<p><img src="screenshots/111.png" width="570"/></p>
<p><img src="screenshots/222.png" width="570"/></p>
<p><img src="screenshots/333.png" width="570"/></p>
<p><img src="screenshots/444.png" width="570"/></p>
<p><img src="screenshots/555.png" width="570"/></p>
