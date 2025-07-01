<h1>
Configuration of the entire "V2V-Automation Platform" to migrate from VMWare to CloudSigma
</h1>
<code>
$ openvpn --config tan.dovan.conf

$ ./oneswap list vms --datacenter 'NEXT-Datacenter' --cluster 'Cluster' --vcenter '11.251.102.140' --vuser 'administrator@vsphere.local' --vpass 'XXXX'
$./oneswap convert node2-win2025-49I4 --vddk /root/workspace/vmware-vix-disklib-distrib/

</code>
