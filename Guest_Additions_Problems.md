Firstly you have to run this command in Local computer

vagrant plugin install vagrant-vbguest

then > 

# Start the old vagrant
vagrant init centos-7
vagrant up
# You should see a message like:
# Installing Virtualbox VBoxGuestAdditions_6.1.16 - guest version is unknown


vagrant ssh

sudo yum install -y dkms binutils gcc make patch libgomp glibc-headers glibc-devel kernel-headers install xorg-x11-drivers xorg-x11-utils kernel-devel

sudo rpm -Uvh https://dl.fedoraproject.org/pub/epel/7/x86_64/Packages/e/epel-release-7-13.noarch.rpm
sudo yum -y update
sudo yum -y install wget nano
cd /opt
sudo wget -c http://download.virtualbox.org/virtualbox/6.1.16/VBoxGuestAdditions_6.1.16.iso -O VBoxGuestAdditions_6.1.16.iso

sudo mount VBoxGuestAdditions_6.1.16.iso -o loop /mnt
cd /mnt
sudo sh VBoxLinuxAdditions.run --nox11
cd /opt
sudo rm *.iso
cat /dev/null > ~/.bash_history
exit

# Now check that the Guest Additions work
vagrant halt
vagrant up

# Package the new VM

vagrant halt
vagrant package
mv package.box centos-7.box

