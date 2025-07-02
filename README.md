<h1>
Configuration of the entire "V2V-Automation Platform" to migrate from VMWare to CloudSigma
</h1>
<code>
$ openvpn --config tan.dovan.conf

$ ./oneswap list vms --datacenter 'NEXT-Datacenter' --cluster 'Cluster' --vcenter '11.251.102.140' --vuser 'administrator@vsphere.local' --vpass 'XXXX'
$./oneswap convert node2-win2025-49I4 --vddk /root/workspace/vmware-vix-disklib-distrib/


libvirt (https://libvirt.org/compiling.html)
$ meson setup --wipe build
$ meson setup build -Ddriver_esx=enabled --reconfigure
$ meson configure build/
$ meson setup build -Ddriver_esx=enabled -Dsystem=true
$ ninja -C build
$ ninja -C build test
$ sudo ninja -C build install

$ cd /root/workspace/one-swap
$ ./oneswap convert node1-ubuntu24.04-sEVA
</code>


<code>
$ vi /etc/one/oneswap.yaml

VDDK setup
$ https://developer.broadcom.com/sdks/vmware-virtual-disk-development-kit-vddk/latest


  nbdkit setup
  $ nbdkit vddk --dump-plugin | grep ^vddk_default_libdir
  $ git clone https://gitlab.com/nbdkit/nbdkit.git
  $ autoreconf -i 
  $ ./configure --with-vddk=/opt/vmware-vix-disklib-distrib
  $ make
  $ make check
  $ sudo make install
  $ ls /usr/local/lib/nbdkit/plugins/nbdkit-vddk-plugin.so
  $ nbdkit --dump-config | grep plugindir

Libguest upgrade
https://gitlab.com/nbdkit/libnbd
https://ocaml.org/install#linux_mac_bsd
hivex  stuff

</code>
