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

Libguest upgrade - https://download.libguestfs.org/

https://gitlab.com/nbdkit/libnbd
https://ocaml.org/install#linux_mac_bsd
hivex  stuff

Thank you for downloading libguestfs 1.56.1

This is how we have configured the optional components for you today:

    Daemon ................................. yes
    Appliance .............................. yes
    QEMU ................................... /usr/bin/kvm
    guestfish .............................. yes
    FUSE filesystem ........................ no
    Default backend ........................ direct
    GNU gettext for i18n ................... no
    OCaml bindings ......................... yes
    Perl bindings .......................... no
    Python bindings ........................ yes
    Ruby bindings .......................... no
    Java bindings .......................... no
    Haskell bindings ....................... no
    PHP bindings ........................... no
    Erlang bindings ........................ no
    Lua bindings ........................... no
    Go bindings ............................ no
    gobject bindings ....................... yes
    gobject introspection .................. no
    Vala bindings .......................... no
    bash completion ........................ yes
    Rust bindings .......................... no

If any optional component is configured 'no' when you expected 'yes'
then you should check the preceding messages.

Please report bugs back to the mailing list:
https://lists.libguestfs.org

Next you should type 'make' to build the package,
then 'make check' to run the tests.
</code>
