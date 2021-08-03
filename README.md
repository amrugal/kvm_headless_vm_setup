# kvm_headless_vm_setup

virt-install --virt-type=kvm --name eve-ng --memory 8192 --vcpus=8 --os-variant=ubuntu16.04 --cdrom=/var/lib/libvirt/boot/EVE-20171007.iso --network=bridge=virbr0,model=virtio --graphics vnc --disk path=/var/lib/libvirt/images/eve-ng.qcow2,size=40,bus=virtio,format=qcow2
* change disk bus to IDE with eve-ng image or ubuntu. "No root file system defined" error occurs during install when using virtio bus. Change to virtio after install using "virsh edit <guestname>". Error origin unknown. 


virsh dumpxml eve-ng | grep vnc
* output: <graphics type='vnc' port='5900' autoport='yes' listen='127.0.0.1'>

ssh username@server_ip -L 5900:127.0.0.1:5900
* then use vnc client to interact with virtual machine using localhost@5900
