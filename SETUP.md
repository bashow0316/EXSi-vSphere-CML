# SETUP MEMO (2022/01/28)

use MacOS X.

## EXSi

VMware vSphere Hypervisor 7.0U3c

### Doc (EXSi)

- https://docs.vmware.com/jp/VMware-vSphere/index.html

### Download (EXSi)

- https://customerconnect.vmware.com/jp/dashboard
- https://customerconnect.vmware.com/jp/group/vmware/evalcenter?p=vsphere-eval-7

### Make USB drive (EXSi)

``` sh
diskutil list
diskutil eraseDisk MS-DOS "ESXIBOOT" MBR disk2
diskutil unmountDisk /dev/disk2
```

``` sh
sudo fdisk -e /dev/disk2
> f 1
> write
> y
> exit
```

``` sh
sudo rm -rf /Volumes/ESXIBOOT
hdiutil attach VMware-VMvisor-Installer-XXXXX.x86_64.iso
cp -R /Volumes/ESXI-XXXXX/* /Volumes/ESXIBOOT
```

``` sh
cd /Volumes/ESXIBOOT
cat ISOLINUX.CFG
cat ISOLINUX.CFG | grep APPEND
sed -i "" 's/APPEND -c boot.cfg/APPEND -c boot.cfg -p 1/g' ISOLINUX.CFG
```

### Install (EXSi)

Follow the procedure.

### Login (EXSi)

``` sh
user: root
pass: "PASSWORD"
```

- https://customerconnect.vmware.com/jp/group/vmware/myeval

## Cisco Modeling Labs 2.0 (CML)

version 2.2.3

The Firefox browser recommends.
You need to complete my profile of cisco.com account.
(The chrome browser is not supported(?).(Bad Gateway: 400 Bad Request error))

- https://id.cisco.com/ui/v1.0/profile-ui

### Doc (CML)

- https://www.cisco.com/c/en/us/td/docs/cloud_services/cisco_modeling_labs/v200/quick/start/b_cml_quick_start_2-0/m_deploy_and_configure.html

### Download

- cml2_controller.ova(2.2.3)
- refplat-20210511-fcs.iso

### Deploy cml image

- Virtual Machines -> Create / Register VM
  - Deployment options -> Remove the check from Power on automatically.

- Virtual Machines -> Actions
  - Edit settings
    - Upgrade CPU number, Memory size, and Hard disk size.

### Login (CML2)

#### CLI or port:9090 (CML2)

``` sh
user: sysadmin
pass: "PASSWORD"
```

#### web (CML2)

``` sh
user: admin
pass: "PASSWORD"
```

### License

Need to cisco.com account.

#### Token

- https://learningnetworkstore.cisco.com/myaccount

#### Smart Software Licensing

Input Token.

Wait for a few minutes after the Registration Status becomes Registered.

Registration Status : Registered
License Authorization Status : Authorized
