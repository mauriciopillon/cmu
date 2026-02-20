# Centro Multiusuário CCT

Lista de Recursos de Computação de Alto Desempenho associado ao CMU-LabP2D.

https://www.udesc.br/cct/centro_multiusuario

---

## Sumário

- [CMU-0 (frontend)](#cmu-0-frontend)
- [CMU-1 (motosserra)](#cmu-1-motosserra)
- [CMU-2 (marreta)](#cmu-2-marreta)
- [CMU-3 (chineque)](#cmu-3-chineque)
- [CMU-4 (esmeril)](#cmu-4-esmeril)
- [CMU-5 (makita)](#cmu-5-makita)

---

# CMU-0 (frontend)

Ponto de acesso aos recursos do cluster CMU.  
Os dois principais serviços deste nó são:

- SLURM: https://github.com/mauriciopillon/slurm-labp2d
- Sistema de Arquivos em rede:
  - `/mnt/prj/g<CPF>`
  - `/mnt/scratch/`

---

# CMU-1 (motosserra)

#############################################################################################

## MOTOSSERRA - Sistema

```bash
hostnamectl 
 Static hostname: motosserra
       Icon name: computer-server
         Chassis: server
      Machine ID: 606c85ccd0c046c2a6ba4d2c4a5d141d
         Boot ID: fcdebf7e094e415a975b7d017baa0c8c
Operating System: Ubuntu 22.04.5 LTS              
          Kernel: Linux 6.8.0-94-generic
    Architecture: x86-64
 Hardware Vendor: Intel Corporation
  Hardware Model: S1200SP
```

## MOTOSSERRA - CPUs

```bash
lscpu
  Architecture:             x86_64
  CPU op-mode(s):         32-bit, 64-bit
  Address sizes:          39 bits physical, 48 bits virtual
  Byte Order:             Little Endian
  CPU(s):                   8
  On-line CPU(s) list:    0-7
  Vendor ID:                GenuineIntel
  Model name:             Intel(R) Xeon(R) CPU E3-1230 v6 @ 3.50GHz
    CPU family:           6
    Model:                158
    Thread(s) per core:   2
    Core(s) per socket:   4
    Socket(s):            1
    Stepping:             9
    CPU max MHz:          3900.0000
    CPU min MHz:          800.0000
    BogoMIPS:             6999.82
    Flags:                fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp lm constant_tsc art arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf pni pclmulqdq dtes64 monitor ds_cpl smx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm 3dnowprefetch cpuid_fault epb pti ssbd ibrs ibpb stibp fsgsbase tsc_adjust sgx bmi1 avx2 smep bmi2 erms invpcid mpx rds eed adx smap clflushopt intel_pt xsaveopt xsavec xgetbv1 xsaves dtherm ida arat pln pts hwp hwp_notify hwp_act_window hwp_epp md_clear flush_l1d arch_capabilities ibpb_exit_to_user
Caches (sum of all):      
  L1d:                    128 KiB (4 instances)
  L1i:                    128 KiB (4 instances)
  L2:                     1 MiB (4 instances)
  L3:                     8 MiB (1 instance)
NUMA:                     
  NUMA node(s):           1
  NUMA node0 CPU(s):      0-7
Vulnerabilities:          
  Gather data sampling:   Mitigation; Microcode
  Itlb multihit:          KVM: Mitigation: VMX unsupported
  L1tf:                   Mitigation; PTE Inversion
  Mds:                    Mitigation; Clear CPU buffers; SMT vulnerable
  Meltdown:               Mitigation; PTI
  Mmio stale data:        Mitigation; Clear CPU buffers; SMT vulnerable
  Reg file data sampling: Not affected
  Retbleed:               Mitigation; IBRS
  Spec rstack overflow:   Not affected
  Spec store bypass:      Mitigation; Speculative Store Bypass disabled via prctl
  Spectre v1:             Mitigation; usercopy/swapgs barriers and __user pointer sanitization
  Spectre v2:             Mitigation; IBRS; IBPB conditional; STIBP conditional; RSB filling; PBRSB-eIBRS Not affected; BHI Not affected
  Srbds:                  Mitigation; Microcode
  Tsx async abort:        Mitigation; TSX disabled
  Vmscape:                Mitigation; IBPB before exit to userspace
```

## MOTOSSERRA - GPU

```bash
nvidia-smi
+---------------------------------------------------------------------------------------+
| NVIDIA-SMI 535.288.01             Driver Version: 535.288.01   CUDA Version: 12.2     |
|-----------------------------------------+----------------------+----------------------+
| GPU  Name                 Persistence-M | Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp   Perf          Pwr:Usage/Cap |         Memory-Usage | GPU-Util  Compute M. |
|                                         |                      |               MIG M. |
|=========================================+======================+======================|
|   0  NVIDIA TITAN Xp                Off | 00000000:01:00.0 Off |                  N/A |
| 23%   35C    P8               9W / 250W |      2MiB / 12288MiB |      0%      Default |
|                                         |                      |                  N/A |
+-----------------------------------------+----------------------+----------------------+
                                                                                         
+---------------------------------------------------------------------------------------+
| Processes:                                                                            |
|  GPU   GI   CI        PID   Type   Process name                            GPU Memory |
|        ID   ID                                                             Usage      |
|=======================================================================================|
|  No running processes found                                                           |
+---------------------------------------------------------------------------------------+
```

## MOTOSSERRA - Memória

```bash
sudo dmidecode -t memory
Getting SMBIOS data from sysfs.
SMBIOS 2.7 present.

Handle 0x001E, DMI type 16, 23 bytes
Physical Memory Array
        Location: System Board Or Motherboard
        Use: System Memory
        Error Correction Type: Single-bit ECC
        Maximum Capacity: 64 GB
        Error Information Handle: Not Provided
        Number Of Devices: 4
```

## MOTOSSERRA - Armazenamento

```bash
lsblk -o NAME,SIZE,TYPE,FSTYPE,MOUNTPOINT,MODEL,SERIAL
NAME                SIZE TYPE FSTYPE      MOUNTPOINT        MODEL            SERIAL
loop1              63.8M loop squashfs    /snap/core20/2686                  
loop2              73.9M loop squashfs    /snap/core22/2216                  
loop3                74M loop squashfs    /snap/core22/2292                  
loop4              66.8M loop squashfs    /snap/core24/1267                  
loop5              66.9M loop squashfs    /snap/core24/1349                  
loop6              91.4M loop squashfs    /snap/lxd/36918                    
loop7              91.4M loop squashfs    /snap/lxd/36558                    
loop8              48.1M loop squashfs    /snap/snapd/25935                  
loop9              50.9M loop squashfs    /snap/snapd/25577                  
loop10              7.6M loop squashfs    /snap/yq/2748                      
loop11              7.6M loop squashfs    /snap/yq/2759                      
loop12             63.8M loop             /snap/core20/2717                  
sda               465.8G disk                               WDC WD5000AAKX-0 WD-WCC2E0HFNADN
├─sda1              512M part vfat        /boot/efi                          
└─sda2            465.3G part LVM2_member                                    
  └─vgroot-lvroot 465.3G lvm  ext4        /       
```

## MOTOSSERRA - Rede

```bash
lspci | grep -i ethernet
02:00.0 Ethernet controller: Intel Corporation Ethernet Controller 10-Gigabit X540-AT2 (rev 01)
02:00.1 Ethernet controller: Intel Corporation Ethernet Controller 10-Gigabit X540-AT2 (rev 01)
05:00.0 Ethernet controller: Intel Corporation I210 Gigabit Network Connection (rev 03)
06:00.0 Ethernet controller: Intel Corporation I210 Gigabit Network Connection (rev 03)
```

#############################################################################################

---

# CMU-2 (marreta)
#############################################################################################

## MARRETA - Sistema

```bash
hostnamectl
 Static hostname: marreta
       Icon name: computer-desktop
         Chassis: desktop
      Machine ID: c434145e60de4c1198803d8bcc530beb
         Boot ID: dd6314b2429a490fb2699ade23ca445e
Operating System: Ubuntu 24.04.3 LTS
          Kernel: Linux 6.8.0-100-generic
    Architecture: x86-64
 Hardware Vendor: INTEL
  Hardware Model: X99
 Firmware Version: 5.11
    Firmware Date: Wed 2020-12-30
     Firmware Age: 5y 1month 3w 1d
```

## MARRETA - CPUs

```bash
lscpu
Architecture:                            x86_64
CPU op-mode(s):                          32-bit, 64-bit
Address sizes:                           46 bits physical, 48 bits virtual
Byte Order:                              Little Endian
CPU(s):                                  48
On-line CPU(s) list:                     0-47
Vendor ID:                               GenuineIntel
Model name:                              Intel(R) Xeon(R) CPU E5-2690 v3 @ 2.60GHz
CPU family:                              6
Model:                                   63
Thread(s) per core:                      2
Core(s) per socket:                      12
Socket(s):                               2
Stepping:                                2
CPU max MHz:                             3500.0000
CPU min MHz:                             1200.0000
BogoMIPS:                                5188.04
Virtualization:                          VT-x
Caches (sum of all):
  L1d:                                   768 KiB (24 instances)
  L1i:                                   768 KiB (24 instances)
  L2:                                    6 MiB (24 instances)
  L3:                                    60 MiB (2 instances)
NUMA:
  NUMA node(s):                          1
  NUMA node0 CPU(s):                     0-47
```

## MARRETA - GPU

```bash
nvidia-smi
Fri Feb 20 17:42:34 2026       
+-----------------------------------------------------------------------------------------+
| NVIDIA-SMI 590.48.01              Driver Version: 590.48.01      CUDA Version: 13.1     |
+-----------------------------------------+------------------------+----------------------+
| GPU  Name                 Persistence-M | Bus-Id          Disp.A | Volatile Uncorr. ECC |
| Fan  Temp   Perf          Pwr:Usage/Cap |           Memory-Usage | GPU-Util  Compute M. |
|                                         |                        |               MIG M. |
|=========================================+========================+======================|
|   0  NVIDIA RTX 4500 Ada Gene...    Off |   00000000:03:00.0  On |                    0 |
| 30%   32C    P8              8W /  210W |       8MiB /  23034MiB |      0%      Default |
|                                         |                        |                  N/A |
+-----------------------------------------+------------------------+----------------------+

+-----------------------------------------------------------------------------------------+
| Processes:                                                                              |
|  GPU   GI   CI              PID   Type   Process name                        GPU Memory |
|        ID   ID                                                               Usage      |
|=========================================================================================|
|  No running processes found                                                             |
+-----------------------------------------------------------------------------------------+```
```

## MARRETA - Memória

```bash
sudo dmidecode -t memory
SMBIOS 3.0.0 present.

Physical Memory Array
        Location: System Board Or Motherboard
        Use: System Memory
        Error Correction Type: Multi-bit ECC
        Maximum Capacity: 384 GB
        Number Of Devices: 6

Memory Installed:
        4 x 16 GB DDR4 2133 MT/s (Micron)
        Total instalado: 64 GB
```

## MARRETA - Armazenamento

```bash
lsblk -o NAME,SIZE,TYPE,FSTYPE,MOUNTPOINT,MODEL,SERIAL
NAME                        SIZE TYPE FSTYPE      MOUNTPOINT MODEL               SERIAL
nvme0n1                   931.5G disk                        KINGSTON SNV2S1000G 50026B7686B6DC01
├─nvme0n1p1                   1G part vfat        /boot/efi
├─nvme0n1p2                   2G part ext4        /boot
└─nvme0n1p3               928.5G part LVM2_member
  └─ubuntu--vg-ubuntu--lv   100G lvm  ext4        /
```

## MARRETA - Rede

```bash
lspci | grep -i ethernet
05:00.0 Ethernet controller: Realtek RTL8111/8168/8411 PCIe Gigabit Ethernet (rev 15)
06:00.0 Ethernet controller: Realtek RTL8111/8168/8211/8411 PCIe Gigabit Ethernet (rev 15)
```

#############################################################################################

---
---

# CMU-3 (chineque)

#############################################################################################

## CHINEQUE - Sistema

```bash
hostnamectl
 Static hostname: chineque
       Icon name: computer-server
         Chassis: server 🖳
      Machine ID: 1477a635e1354ac7825d0aae9f9d9b0e
         Boot ID: ef78f524258a4ff382185ed3c6f5f692
Operating System: Ubuntu 24.04.3 LTS
          Kernel: Linux 6.8.0-100-generic
    Architecture: x86-64
 Hardware Vendor: Supermicro
  Hardware Model: Super Server
Firmware Version: 4.4
   Firmware Date: Mon 2024-07-15
    Firmware Age: 1y 7month 6d
```

## CHINEQUE - CPUs

```bash
lscpu
Architecture:                            x86_64
CPU op-mode(s):                          32-bit, 64-bit
Address sizes:                           46 bits physical, 48 bits virtual
Byte Order:                              Little Endian
CPU(s):                                  40
On-line CPU(s) list:                     0-39
Vendor ID:                               GenuineIntel
BIOS Vendor ID:                          Intel(R) Corporation
Model name:                              Intel(R) Xeon(R) Gold 6222V CPU @ 1.80GHz
BIOS Model name:                         Intel(R) Xeon(R) Gold 6222V CPU @ 1.80GHz  CPU @ 1.8GHz
BIOS CPU family:                         179
CPU family:                              6
Model:                                   85
Thread(s) per core:                      2
Core(s) per socket:                      20
Socket(s):                               1
Stepping:                                7
CPU(s) scaling MHz:                      27%
CPU max MHz:                             3600.0000
CPU min MHz:                             800.0000
BogoMIPS:                                3600.00
Flags:                                   fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp lm constant_tsc art arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid dca sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm 3dnowprefetch cpuid_fault epb cat_l3 cdp_l3 intel_ppin ssbd mba ibrs ibpb stibp ibrs_enhanced tpr_shadow flexpriority ept vpid ept_ad fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid cqm mpx rdt_a avx512f avx512dq rdseed adx smap clflushopt clwb intel_pt avx512cd avx512bw avx512vl xsaveopt xsavec xgetbv1 xsaves cqm_llc cqm_occup_llc cqm_mbm_total cqm_mbm_local dtherm ida arat pln pts vnmi pku ospke avx512_vnni md_clear flush_l1d arch_capabilities ibpb_exit_to_user
Virtualization:                          VT-x
L1d cache:                               640 KiB (20 instances)
L1i cache:                               640 KiB (20 instances)
L2 cache:                                20 MiB (20 instances)
L3 cache:                                27.5 MiB (1 instance)
NUMA node(s):                            1
NUMA node0 CPU(s):                       0-39
Vulnerability Gather data sampling:      Mitigation; Microcode
Vulnerability Indirect target selection: Vulnerable
Vulnerability Itlb multihit:             KVM: Mitigation: VMX disabled
Vulnerability L1tf:                      Not affected
Vulnerability Mds:                       Not affected
Vulnerability Meltdown:                  Not affected
Vulnerability Mmio stale data:           Mitigation; Clear CPU buffers; SMT vulnerable
Vulnerability Reg file data sampling:    Not affected
Vulnerability Retbleed:                  Mitigation; Enhanced IBRS
Vulnerability Spec rstack overflow:      Not affected
Vulnerability Spec store bypass:         Mitigation; Speculative Store Bypass disabled via prctl
Vulnerability Spectre v1:                Mitigation; usercopy/swapgs barriers and __user pointer sanitization
Vulnerability Spectre v2:                Mitigation; Enhanced / Automatic IBRS; IBPB conditional; PBRSB-eIBRS SW sequence; BHI SW loop, KVM SW loop
Vulnerability Srbds:                     Not affected
Vulnerability Tsa:                       Not affected
Vulnerability Tsx async abort:           Mitigation; TSX disabled
Vulnerability Vmscape:                   Mitigation; IBPB before exit to userspace
```

## CHINEQUE - GPU

```bash
nvidia-smi
Thu Feb 19 14:29:56 2026       
+-----------------------------------------------------------------------------------------+
| NVIDIA-SMI 580.126.09             Driver Version: 580.126.09     CUDA Version: 13.0     |
+-----------------------------------------+------------------------+----------------------+
| GPU  Name                 Persistence-M | Bus-Id          Disp.A | Volatile Uncorr. ECC |
| Fan  Temp   Perf          Pwr:Usage/Cap |           Memory-Usage | GPU-Util  Compute M. |
|                                         |                        |               MIG M. |
|=========================================+========================+======================|
|   0  NVIDIA RTX A5500               Off |   00000000:B3:00.0 Off |                  Off |
| 30%   32C    P8             14W /  230W |       1MiB /  24564MiB |      0%      Default |
|                                         |                        |                  N/A |
+-----------------------------------------+------------------------+----------------------+

+-----------------------------------------------------------------------------------------+
| Processes:                                                                              |
|  GPU   GI   CI              PID   Type   Process name                        GPU Memory |
|        ID   ID                                                               Usage      |
|=========================================================================================|
|  No running processes found                                                             |
+-----------------------------------------------------------------------------------------+
```

## CHINEQUE - Memória

```bash
sudo dmidecode -t memory
# dmidecode 3.5
Getting SMBIOS data from sysfs.
SMBIOS 3.2.1 present.

Handle 0x0023, DMI type 16, 23 bytes
Physical Memory Array
	Location: System Board Or Motherboard
	Use: System Memory
	Error Correction Type: Single-bit ECC
	Maximum Capacity: 2304 GB
	Error Information Handle: Not Provided
	Number Of Devices: 4
```

## CHINEQUE - Armazenamento

```bash
lsblk -o NAME,SIZE,TYPE,FSTYPE,MOUNTPOINT,MODEL,SERIAL
NAME                        SIZE TYPE  FSTYPE          MOUNTPOINT        MODEL            SERIAL
loop0                      63.8M loop  squashfs        /snap/core20/2682                  
loop1                      63.8M loop  squashfs        /snap/core20/2686                  
loop2                      66.8M loop  squashfs        /snap/core24/1267                  
loop3                      91.4M loop  squashfs        /snap/lxd/36558                    
loop4                      66.9M loop  squashfs        /snap/core24/1349                  
loop5                      91.4M loop  squashfs        /snap/lxd/36918                    
loop6                      50.9M loop  squashfs        /snap/snapd/25577                  
loop7                      48.1M loop  squashfs        /snap/snapd/25935                  
sda                       745.2G disk                                    INTEL SSDSC2BG80 BTHC509202V3800NGN
├─sda1                        1G part  vfat            /boot/efi                          
├─sda2                        2G part  ext4            /boot                              
└─sda3                    742.2G part  LVM2_member                                        
  └─ubuntu--vg-ubuntu--lv 742.2G lvm   ext4            /                                  
sdb                       745.2G disk  ddf_raid_member                   INTEL SSDSC2BG80 BTHC509200SJ800NGN
├─md126                       0B raid0                                                    
└─md127                       0B md                                                       
```

## CHINEQUE - Rede

```bash
lspci | grep -i ethernet
01:00.0 Ethernet controller: Intel Corporation Ethernet Controller 10-Gigabit X540-AT2 (rev 01)
01:00.1 Ethernet controller: Intel Corporation Ethernet Controller 10-Gigabit X540-AT2 (rev 01)
19:00.0 Ethernet controller: Intel Corporation Ethernet Connection X722 for 10GBASE-T (rev 09)
19:00.1 Ethernet controller: Intel Corporation Ethernet Connection X722 for 10GBASE-T (rev 09)
```

### CHINEQUE - Rede (ethtool eno1np0)

```bash
sudo ethtool eno1np0
Settings for eno1np0:
	Supported ports: [ TP ]
	Supported link modes:   1000baseT/Full
	                        10000baseT/Full
	Supported pause frame use: Symmetric Receive-only
	Supports auto-negotiation: Yes
	Supported FEC modes: Not reported
	Advertised link modes:  1000baseT/Full
	                        10000baseT/Full
	Advertised pause frame use: No
	Advertised auto-negotiation: Yes
	Advertised FEC modes: Not reported
	Speed: 1000Mb/s
	Duplex: Full
	Auto-negotiation: on
	Port: Twisted Pair
	PHYAD: 0
	Transceiver: internal
	MDI-X: Unknown
	Supports Wake-on: g
	Wake-on: g
        Current message level: 0x00000007 (7)
                               drv probe link
	Link detected: yes
```

#############################################################################################

---

# CMU-4 (esmeril)

#############################################################################################

## ESMERIL - Sistema

```bash
hostnamectl
 Static hostname: esmeril
       Icon name: computer-server
         Chassis: server 🖳
      Machine ID: 5ecab09c3c0245a8baf91dcfb29514c9
         Boot ID: b076d0836faf495fbf71c5350a659f44
Operating System: Ubuntu 24.04.3 LTS
          Kernel: Linux 6.8.0-100-generic
    Architecture: x86-64
 Hardware Vendor: Supermicro
  Hardware Model: UPD AS-2015CS-TNR
Firmware Version: 3.6
   Firmware Date: Mon 2025-05-12
    Firmware Age: 9month 1w 2d
```

## ESMERIL - CPUs

```bash
lscpu
Architecture:                            x86_64
CPU op-mode(s):                          32-bit, 64-bit
Address sizes:                           52 bits physical, 57 bits virtual
Byte Order:                              Little Endian
CPU(s):                                  48
On-line CPU(s) list:                     0-47
Vendor ID:                               AuthenticAMD
BIOS Vendor ID:                          Advanced Micro Devices, Inc.
Model name:                              AMD EPYC 9224 24-Core Processor
BIOS Model name:                         AMD EPYC 9224 24-Core Processor                 Unknown CPU @ 2.5GHz
BIOS CPU family:                         107
CPU family:                              25
Model:                                   17
Thread(s) per core:                      2
Core(s) per socket:                      24
Socket(s):                               1
Stepping:                                1
Frequency boost:                         enabled
CPU(s) scaling MHz:                      45%
CPU max MHz:                             3707.5371
CPU min MHz:                             1500.0000
BogoMIPS:                                4992.71
Flags:                                   fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm constant_tsc rep_good amd_lbr_v2 nopl nonstop_tsc cpuid extd_apicid aperfmperf rapl pni pclmulqdq monitor ssse3 fma cx16 pcid sse4_1 sse4_2 x2apic movbe popcnt aes xsave avx f16c rdrand lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt tce topoext perfctr_core perfctr_nb bpext perfctr_llc mwaitx cpb cat_l3 cdp_l3 hw_pstate ssbd mba perfmon_v2 ibrs ibpb stibp ibrs_enhanced vmmcall fsgsbase bmi1 avx2 smep bmi2 erms invpcid cqm rdt_a avx512f avx512dq rdseed adx smap avx512ifma clflushopt clwb avx512cd sha_ni avx512bw avx512vl xsaveopt xsavec xgetbv1 xsaves cqm_llc cqm_occup_llc cqm_mbm_total cqm_mbm_local user_shstk avx512_bf16 clzero irperf xsaveerptr rdpru wbnoinvd amd_ppin cppc amd_ibpb_ret arat npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold avic v_vmsave_vmload vgif x2avic v_spec_ctrl vnmi avx512vbmi umip pku ospke avx512_vbmi2 gfni vaes vpclmulqdq avx512_vnni avx512_bitalg avx512_vpopcntdq la57 rdpid overflow_recov succor smca fsrm flush_l1d debug_swap ibpb_exit_to_user
Virtualization:                          AMD-V
L1d cache:                               768 KiB (24 instances)
L1i cache:                               768 KiB (24 instances)
L2 cache:                                24 MiB (24 instances)
L3 cache:                                64 MiB (4 instances)
NUMA node(s):                            1
NUMA node0 CPU(s):                       0-47
Vulnerability Gather data sampling:      Not affected
Vulnerability Indirect target selection: Not affected
Vulnerability Itlb multihit:             Not affected
Vulnerability L1tf:                      Not affected
Vulnerability Mds:                       Not affected
Vulnerability Meltdown:                  Not affected
Vulnerability Mmio stale data:           Not affected
Vulnerability Reg file data sampling:    Not affected
Vulnerability Retbleed:                  Not affected
Vulnerability Spec rstack overflow:      Mitigation; Safe RET
Vulnerability Spec store bypass:         Mitigation; Speculative Store Bypass disabled via prctl
Vulnerability Spectre v1:                Mitigation; usercopy/swapgs barriers and __user pointer sanitization
Vulnerability Spectre v2:                Mitigation; Enhanced / Automatic IBRS; IBPB conditional; STIBP always-on; PBRSB-eIBRS Not affected; BHI Not affected
Vulnerability Srbds:                     Not affected
Vulnerability Tsa:                       Mitigation; Clear CPU buffers
Vulnerability Tsx async abort:           Not affected
Vulnerability Vmscape:                   Mitigation; IBPB before exit to userspace
```

## ESMERIL - GPU

```bash
nvidia-smi
Thu Feb 19 14:30:49 2026       
+-----------------------------------------------------------------------------------------+
| NVIDIA-SMI 580.126.09             Driver Version: 580.126.09     CUDA Version: 13.0     |
+-----------------------------------------+------------------------+----------------------+
| GPU  Name                 Persistence-M | Bus-Id          Disp.A | Volatile Uncorr. ECC |
| Fan  Temp   Perf          Pwr:Usage/Cap |           Memory-Usage | GPU-Util  Compute M. |
|                                         |                        |               MIG M. |
|=========================================+========================+======================|
|   0  NVIDIA RTX PRO 6000 Blac...    Off |   00000000:88:00.0 Off |                    0 |
| N/A   32C    P8             28W /  450W |       0MiB /  97887MiB |      0%      Default |
|                                         |                        |             Disabled |
+-----------------------------------------+------------------------+----------------------+

+-----------------------------------------------------------------------------------------+
| Processes:                                                                              |
|  GPU   GI   CI              PID   Type   Process name                        GPU Memory |
|        ID   ID                                                               Usage      |
|=========================================================================================|
|  No running processes found                                                             |
+-----------------------------------------------------------------------------------------+
```

## ESMERIL - Memória

```bash
# dmidecode 3.5
Getting SMBIOS data from sysfs.
SMBIOS 3.5.0 present.

Handle 0x001B, DMI type 16, 23 bytes
Physical Memory Array
	Location: System Board Or Motherboard
	Use: System Memory
	Error Correction Type: Multi-bit ECC
	Maximum Capacity: 6 TB
	Error Information Handle: 0x001A
	Number Of Devices: 12
```

## ESMERIL - Armazenamento

```bash
lsblk -o NAME,SIZE,TYPE,FSTYPE,MOUNTPOINT,MODEL,SERIAL
NAME          SIZE TYPE  FSTYPE            MOUNTPOINT MODEL            SERIAL
sda         894.3G disk                               SAMSUNG MZ7L3960 S6EKNE0WA01335
├─sda1          1G part  vfat              /boot/efi                   
└─sda2      893.2G part  linux_raid_member                             
  └─md0     893.1G raid1                                               
    ├─md0p1   500M part  ext4              /boot                       
    └─md0p2 892.6G part  ext4              /                           
sdb         894.3G disk                               SAMSUNG MZ7L3960 S6EKNE0WA01337
├─sdb1          1G part  vfat                                          
└─sdb2      893.2G part  linux_raid_member                             
  └─md0     893.1G raid1                                               
    ├─md0p1   500M part  ext4              /boot                       
    └─md0p2 892.6G part  ext4              /                           
```

## ESMERIL - Rede

```bash
lspci | grep -i ethernet
81:00.0 Ethernet controller: Intel Corporation Ethernet Controller X710 for 10GBASE-T (rev 02)
81:00.1 Ethernet controller: Intel Corporation Ethernet Controller X710 for 10GBASE-T (rev 02)
```

### ESMERIL - Rede (ethtool enp129s0f0np0)

```bash
sudo ethtool enp129s0f0np0
Settings for enp129s0f0np0:
	Supported ports: [ TP ]
	Supported link modes:   100baseT/Full
	                        1000baseT/Full
	                        10000baseT/Full
	                        2500baseT/Full
	                        5000baseT/Full
	Supported pause frame use: Symmetric Receive-only
	Supports auto-negotiation: Yes
	Supported FEC modes: Not reported
	Advertised link modes:  100baseT/Full
	                        1000baseT/Full
	                        10000baseT/Full
	                        2500baseT/Full
	                        5000baseT/Full
	Advertised pause frame use: No
	Advertised auto-negotiation: Yes
	Advertised FEC modes: Not reported
	Speed: 100Mb/s
	Duplex: Full
	Auto-negotiation: on
	Port: Twisted Pair
	PHYAD: 0
	Transceiver: internal
	MDI-X: Unknown
	Supports Wake-on: g
	Wake-on: g
        Current message level: 0x00000007 (7)
                               drv probe link
	Link detected: yes
```

#############################################################################################

---

# CMU-5 (makita)

#############################################################################################

## MAKITA - Sistema

```bash
hostnamectl
 Static hostname: makita
       Icon name: computer-server
         Chassis: server 🖳
      Machine ID: 7340047455f44d5fa71ffa14e8024fce
         Boot ID: fdd95f930cb64aa2865bc9aed6fff49c
Operating System: Ubuntu 24.04.3 LTS
          Kernel: Linux 6.8.0-100-generic
    Architecture: x86-64
 Hardware Vendor: Supermicro
  Hardware Model: UPD AS-2015CS-TNR
Firmware Version: 3.6
   Firmware Date: Mon 2025-05-12
    Firmware Age: 9month 1w 2d
```

## MAKITA - CPUs

```bash
lscpu
Architecture:                            x86_64
CPU op-mode(s):                          32-bit, 64-bit
Address sizes:                           52 bits physical, 57 bits virtual
Byte Order:                              Little Endian
CPU(s):                                  48
On-line CPU(s) list:                     0-47
Vendor ID:                               AuthenticAMD
BIOS Vendor ID:                          Advanced Micro Devices, Inc.
Model name:                              AMD EPYC 9224 24-Core Processor
BIOS Model name:                         AMD EPYC 9224 24-Core Processor                 Unknown CPU @ 2.5GHz
BIOS CPU family:                         107
CPU family:                              25
Model:                                   17
Thread(s) per core:                      2
Core(s) per socket:                      24
Socket(s):                               1
Stepping:                                1
Frequency boost:                         enabled
CPU(s) scaling MHz:                      45%
CPU max MHz:                             3707.5371
CPU min MHz:                             1500.0000
BogoMIPS:                                4992.71
Flags:                                   fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm constant_tsc rep_good amd_lbr_v2 nopl nonstop_tsc cpuid extd_apicid aperfmperf rapl pni pclmulqdq monitor ssse3 fma cx16 pcid sse4_1 sse4_2 x2apic movbe popcnt aes xsave avx f16c rdrand lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt tce topoext perfctr_core perfctr_nb bpext perfctr_llc mwaitx cpb cat_l3 cdp_l3 hw_pstate ssbd mba perfmon_v2 ibrs ibpb stibp ibrs_enhanced vmmcall fsgsbase bmi1 avx2 smep bmi2 erms invpcid cqm rdt_a avx512f avx512dq rdseed adx smap avx512ifma clflushopt clwb avx512cd sha_ni avx512bw avx512vl xsaveopt xsavec xgetbv1 xsaves cqm_llc cqm_occup_llc cqm_mbm_total cqm_mbm_local user_shstk avx512_bf16 clzero irperf xsaveerptr rdpru wbnoinvd amd_ppin cppc amd_ibpb_ret arat npt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold avic v_vmsave_vmload vgif x2avic v_spec_ctrl vnmi avx512vbmi umip pku ospke avx512_vbmi2 gfni vaes vpclmulqdq avx512_vnni avx512_bitalg avx512_vpopcntdq la57 rdpid overflow_recov succor smca fsrm flush_l1d debug_swap ibpb_exit_to_user
Virtualization:                          AMD-V
L1d cache:                               768 KiB (24 instances)
L1i cache:                               768 KiB (24 instances)
L2 cache:                                24 MiB (24 instances)
L3 cache:                                64 MiB (4 instances)
NUMA node(s):                            1
NUMA node0 CPU(s):                       0-47
Vulnerability Gather data sampling:      Not affected
Vulnerability Indirect target selection: Not affected
Vulnerability Itlb multihit:             Not affected
Vulnerability L1tf:                      Not affected
Vulnerability Mds:                       Not affected
Vulnerability Meltdown:                  Not affected
Vulnerability Mmio stale data:           Not affected
Vulnerability Reg file data sampling:    Not affected
Vulnerability Retbleed:                  Not affected
Vulnerability Spec rstack overflow:      Mitigation; Safe RET
Vulnerability Spec store bypass:         Mitigation; Speculative Store Bypass disabled via prctl
Vulnerability Spectre v1:                Mitigation; usercopy/swapgs barriers and __user pointer sanitization
Vulnerability Spectre v2:                Mitigation; Enhanced / Automatic IBRS; IBPB conditional; STIBP always-on; PBRSB-eIBRS Not affected; BHI Not affected
Vulnerability Srbds:                     Not affected
Vulnerability Tsa:                       Mitigation; Clear CPU buffers
Vulnerability Tsx async abort:           Not affected
Vulnerability Vmscape:                   Mitigation; IBPB before exit to userspace
```

## MAKITA - GPU

```bash
nvidia-smi
Thu Feb 19 14:31:14 2026       
+-----------------------------------------------------------------------------------------+
| NVIDIA-SMI 580.126.09             Driver Version: 580.126.09     CUDA Version: 13.0     |
+-----------------------------------------+------------------------+----------------------+
| GPU  Name                 Persistence-M | Bus-Id          Disp.A | Volatile Uncorr. ECC |
| Fan  Temp   Perf          Pwr:Usage/Cap |           Memory-Usage | GPU-Util  Compute M. |
|                                         |                        |               MIG M. |
|=========================================+========================+======================|
|   0  NVIDIA RTX PRO 6000 Blac...    Off |   00000000:82:00.0 Off |                    0 |
| N/A   30C    P8             29W /  450W |       0MiB /  97887MiB |      0%      Default |
|                                         |                        |             Disabled |
+-----------------------------------------+------------------------+----------------------+

+-----------------------------------------------------------------------------------------+
| Processes:                                                                              |
|  GPU   GI   CI              PID   Type   Process name                        GPU Memory |
|        ID   ID                                                               Usage      |
|=========================================================================================|
|  No running processes found                                                             |
+-----------------------------------------------------------------------------------------+
```

## MAKITA - Memória

```bash
sudo dmidecode -t memory
# dmidecode 3.5
Getting SMBIOS data from sysfs.
SMBIOS 3.5.0 present.

Handle 0x001B, DMI type 16, 23 bytes
Physical Memory Array
	Location: System Board Or Motherboard
	Use: System Memory
	Error Correction Type: Multi-bit ECC
	Maximum Capacity: 6 TB
	Error Information Handle: 0x001A
	Number Of Devices: 12
```

## MAKITA - Armazenamento

```bash
lsblk -o NAME,SIZE,TYPE,FSTYPE,MOUNTPOINT,MODEL,SERIAL
NAME          SIZE TYPE  FSTYPE            MOUNTPOINT MODEL            SERIAL
sda         894.3G disk                               SAMSUNG MZ7L3960 S6EKNE0WA01336
├─sda1          1G part  vfat                                          
└─sda2      893.2G part  linux_raid_member                             
  └─md0     893.1G raid1                                               
    ├─md0p1     1G part  ext4              /boot                       
    └─md0p2 892.1G part  ext4              /                           
sdb         894.3G disk                               SAMSUNG MZ7L3960 S6EKNE0WA01333
├─sdb1          1G part  vfat              /boot/efi                   
└─sdb2      893.2G part  linux_raid_member                             
  └─md0     893.1G raid1                                               
    ├─md0p1     1G part  ext4              /boot                       
    └─md0p2 892.1G part  ext4              /                           
```

## MAKITA - Rede

```bash
lspci | grep -i ethernet
81:00.0 Ethernet controller: Intel Corporation Ethernet Controller X710 for 10GBASE-T (rev 02)
81:00.1 Ethernet controller: Intel Corporation Ethernet Controller X710 for 10GBASE-T (rev 02)
```

### MAKITA - Rede (ethtool enp129s0f0np0)

```bash
sudo ethtool enp129s0f0np0
Settings for enp129s0f0np0:
	Supported ports: [ TP ]
	Supported link modes:   100baseT/Full
	                        1000baseT/Full
	                        10000baseT/Full
	                        2500baseT/Full
	                        5000baseT/Full
	Supported pause frame use: Symmetric Receive-only
	Supports auto-negotiation: Yes
	Supported FEC modes: Not reported
	Advertised link modes:  100baseT/Full
	                        1000baseT/Full
	                        10000baseT/Full
	                        2500baseT/Full
	                        5000baseT/Full
	Advertised pause frame use: No
	Advertised auto-negotiation: Yes
	Advertised FEC modes: Not reported
	Speed: 1000Mb/s
	Duplex: Full
	Auto-negotiation: on
	Port: Twisted Pair
	PHYAD: 0
	Transceiver: internal
	MDI-X: Unknown
	Supports Wake-on: g
	Wake-on: g
        Current message level: 0x00000007 (7)
                               drv probe link
	Link detected: yes
```

#############################################################################################
