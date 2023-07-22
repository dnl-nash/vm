This script can be used to create vms using qemu. It provides the following functions:

creates new vm images. To create a new vm, run: vm init [name] [cores] [memory, in MB] [maximum disk size] [full path to installer ISO] [remote host] [remote port], any missing parameters are prompted
starts vms: vm start [vm name]
shuts down vms: vm shutdown [vm name]

During initialization, several shell scripts are generated:

[vm name].vars: remote startup, default
[vm name].local: local startup using gtk display

Several optional environment variables are supported:

nowin:
if set, disables windows specific segments during creation and first time installation, such as creating a virtio USB with windows drivers, as well as using tools such as msiextract to make a  connection package for windows hosts containing the virt-viewer program and a connection script.
noweb:
disables the integration with websockify to allow spice control through web sockets
nostartupsnap:
disables creation of a snapshot every time the vm starts up, allowing the restore of the disk to any given startup, also makes a primitive audit traill
noshutdownsnap:
same as nostartupsnap, but for shutdowns

Script requirements:

Install the following packages on your Arch system:
ovmf swtpm virtio-win msitools rsync p7zip udisks2 zip qemu-desktop

Windows specific instructions:

Load the virtio drivers:
Load these drivers before you start the Windows installation.
In the Windows out of box experience, press shift F10 to load command prompt.
Run the following command:
pnputil /add-driver c:\*.inf /install /subdirs
After that, you should be able to continue with the Windows installation as normal.

Credits:
Thanks to Jonathan Rodriguez (https://github.com/JonathanR529) for adding more documentation than what was provided.