1) Firstly you have to run this command in Local computer

2) vagrant plugin install vagrant-vbguest

then > 

# Start the old vagrant
3) vagrant init centos-7
4) vagrant up
# You should see a message like:
# Installing Virtualbox VBoxGuestAdditions_6.1.16 - guest version is unknown


5) vagrant ssh

6) sudo yum install -y dkms binutils gcc make patch libgomp glibc-headers glibc-devel kernel-headers install xorg-x11-drivers xorg-x11-utils kernel-devel

7) sudo rpm -Uvh https://dl.fedoraproject.org/pub/epel/7/x86_64/Packages/e/epel-release-7-13.noarch.rpm
8) sudo yum -y update
9) sudo yum -y install wget nano
10) cd /opt
11) sudo wget -c http://download.virtualbox.org/virtualbox/6.1.16/VBoxGuestAdditions_6.1.16.iso -O VBoxGuestAdditions_6.1.16.iso

12) sudo mount VBoxGuestAdditions_6.1.16.iso -o loop /mnt
13) cd /mnt
14) sudo sh VBoxLinuxAdditions.run --nox11
15) cd /opt
16) cat /dev/null > ~/.bash_history
17) exit

# Now check that the Guest Additions work
18) vagrant halt
19) vagrant up

# Package the new VM

20) vagrant halt
21) vagrant package
22) mv package.box centos-7.box



