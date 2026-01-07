***Bios settings with [scewin](https://github.com/ab3lkaizen/SCEHUB) for AMD***

**Made by scynesthesia**

These settings are gonna be divided in levels of risk so if u dont want to reset cmos and just want an easy performance boost you should only do the low-medium risk, if u want max performance and have time to clear cmos and do benchmarks you should do all the settings.  
Also dont mass apply all these settings, do it by groups of 5 \- 10

Disclaimer: If you play cs2 or valorant you should have:  
TPM State \- Enabled  
TCM State \- Enabled  
NX mode \- Enabled  
Secure Boot \- Enabled  
AMD fTPM switch \- Enabled  
SVM Mode \- Enabled (needed for turning core isolation on)  
If you don't play any of those games you can disable them all

# **Low Risk 🟢**

*Note: Some power-management related options may behave differently on laptops or OEM systems. Test changes incrementally, especially on mobile platforms.*

## **RAM Power-saving**

* **Power Down Enable \- Disabled** (Disables RAM idle power-saving).  
* **DRAM Scrub Time \- Disabled** (Disables periodic RAM error correction)

## **SATA/Storage**

* **Aggresive SATA Device Sleep Port 0/1** \- **Disabled** (Prevents SATA drives from entering deep sleep).  
* **SATA Hot-Removable Support \- Disabled** (Disables hot-swap detection for SATA drives).  
* **SATA D3 Support \- Disabled** (Disables SATA low-power state).  
* **SATA MSI Capability Support \- Enabled** Allows SATA devices to use Message Signaled Interrupts, reducing I/O latency.  
* **Sata Disabled AHCI Prefetch Function \- Disabled** Removes unnecessary prefetching that can cause micro-latencies on the bus.  
* **SATA CLK Mode Option** \- **100MHz**  (Forces a static frequency for the SATA controller clock, preventing variations).  
* **SATA Mode \- AHCI** (Prioritizes performance over IDE compatibility).  
* **SATA MAXGEN2 CAP OPTION \- Disabled** (Forces SATA Gen3 speeds. **Warning:** Disable only if using modern SSDs; can cause boot failure or drive disappearance on old HDDs/cables).

## **Legacy & Connectivity**

* **eMMC/SD Enable \- Disabled** Disables the integrated SD card controller.  
* **ESPI Enable \- Disabled** Disables the Enhanced Serial Peripheral Interface for legacy devices (test for boot stability).  
* **LAN Power Enable \- Disabled** Prevents the network card from entering power-saving states.

## **CPU Power-saving**

* **Global C-state Control \- Disabled** (Disables CPU low-power states).  
* **ACPI \_CST C1 Declaration \- Disabled** (Removes support for CPU C1 sleep state).  
* **DF Cstates \- Disabled** (Disables power-saving for Data Fabric).  
* **PM L1 SS \- Disabled** (Disables PCIe L1 power-saving states).  
* **Core C6 State \- Disabled** (power saving \- may increase heat/power draw)  
* **CC6 Memory Region Encryption \- Disabled** (Disables RAM encryption when CPU cores sleep)  
* **Spread Spectrum \- Disabled** (Disables clock frequency modulation for EMI reduction)  
* **Cool’n’Quiet** \- Disabled (Disables CPU dynamic frequency scaling, only disable it with a static ratio and static voltage)

## **PCIe/GPU Power-saving**

* **Unused GPP Clocks Off \- Disabled** (Keeps PCIe clocks active even if unused).  
* **ASPM Control / ASPM Mode Control  \- Disabled** (Disables PCIe link power management).  
* **Clock Power Management (CLKREQ\#) \- Disabled** (Keeps PCIe clocks active).  
* **LCLK DPM \- Disabled** (Disables PCIe link power management).  
* **LCLK DPM Enhanced PCIe Detection \- Disabled** (Prevents the system from wasting cycles re-detecting PCIe links during state changes).  
* **Isochronous Support \- Disabled** (Related to data stream synchronization; disabling it may reduce micro-stutters).  
* **Socket 0/1 NBIO 0-3 Target DPM Level \- 2** (Forces maximum performance on the CPU's input/output controller).  
* **NBIO DPM Control – Manual** (Allows manual override of Northbridge Dynamic Power Management to prevent clock fluctuations).  
* **NBIO Poison Consumption – Disabled** (Prevents the system from halting when it detects "poisoned" data packets, improving stability during extreme RAM * * tuning).  
* **NBIO RAS Global Control – Manual** (Enables manual control over Reliability, Availability, and Serviceability features).  
* **NBIO RAS Control – Disabled** (Disables hardware-level error reporting and correction to reduce background interrupt overhead).  
* **NBIO SyncFlood Generation – Disabled** (Prevents the CPU from triggering a forced reset during non-fatal Infinity Fabric parity errors).  
* **NBIO SyncFlood Reporting – Disabled** (Stops the firmware from logging fabric errors to reduce management bus traffic).  
* **PCIB Clock Run \- Disabled** (Keeps the PCI bus clock always active for immediate response from devices).  
* **VRM Spread Spectrum / BCLK Spread Spectrum** – **Disabled** (Exists in most AM4/AM5 VRM/Clock menus. Prevents the base clock from oscillating by 0.5%, ensuring a perfectly stable frequency for the CPU and PCIe bus).  
* **PCIe ARI Support** – **Disabled** (Alternative Routing-ID Interpretation; disabling it can reduce bus addressing overhead in single-GPU setups).  
* **Relaxed Ordering** – **Disabled** (Forces strict transaction ordering on the PCIe bus, which can improve consistency at the cost of peak theoretical throughput).  
* **ACS Enable** – **Disabled** (Access Control Services; disabling it reduces virtualization overhead and improves direct hardware communication).

## **Network Functionality**

* **IPv6 HTTP Support \- Disabled**  
* **IPv6 PXE Support \- Disabled**  
* **Network Stack Driver Support \- Disabled** \- Prevents the BIOS from loading network drivers into the POST, speeding up booting.  
* **Onboard PCIE LAN PXE ROM \- Disabled** (Disables the search for operating systems on the local network (PXE boot)).

## **USB/PS2 Power-saving**

* **PS2 Devices Support \- Disabled** (Disables PS/2 port support)  
* **Win7 USB Wake Support \- Disabled** (Prevents USB devices from waking the system from sleep, Windows 7 legacy feature).

## **Hardware Functionality**

* **HD Audio Controller \- Disabled** (Disables the motherboard’s audio jacks, safe if using external/USB/GPU audio)  
* **Integrated Graphics \- Ignore** (as the name says it disable only if u have a gpu)  
* **RGB Fusion (Onboard LED) \- Disabled** (Reduces unnecessary polling rate on the motherboard bus).  
* **Discrete GPU's Audio \- Disabled** (Disables the video card's sound driver; reduces IRQ conflicts if using USB or motherboard audio).  
* **AMD StartUp PWM Enable \- Disabled** (Disables unnecessary PWM power control during startup).  
* **AMD KVM Mouse Protocol \- Simple** (Reduces the complexity of the mouse protocol at the hardware/BIOS level).  
* **UMA Mode \- None** (Ensures that RAM is not reserved for the integrated GPU if you already use a dedicated one).

## **Power-saving**

* **AB Clock Gating \- Disabled** (Disables clock gating for unused components (saves power, minimal performance impact).  
* **ACP CLock Gating \- Disabled** (Disables Audio Co-Processor power saving; prevents micro-latencies on the audio bus).  
* **PCIe Power Gating** – **Disabled** (Keeps PCIe lanes fully powered regardless of activity).  
* **LAN / WLAN Power Gating** – **Disabled** (Ensures the network controllers stay active, avoiding resume-lag).  
* **Thunderbolt / USB4 Power Gating** – **Disabled** (Prevents the USB4 controller from entering sleep states).  
* **ACP Power Gating \-** Disabled (Prevents the Audio Co-Processor from entering power-saving states; eliminates wake-up latency on the audio bus).  
* **Power Loading \- Disabled** (Removes dummy loading for old fonts; Reduces electrical noise in modern sources).  
* **USB Phy Power Down \- Disabled** (Keeps the physical layer of the USB active to avoid "wake-up" latency in peripherals).

## **Miscellaneous**

* **Opcache Control \- Enabled** (Keeps the OpCache active to feed the CPU cores faster; essential for Zen architecture performance).  
* **Lock Legacy Resources \- Disabled** (Frees legacy ISA/IO resource reservations; reduces legacy-device baggage).  
* **MsiDis in HPET \- Enabled** (Exposes MSI capability in HPET register; reduces interrupt overhead)  
* **Bootup NumLock State \- Off** (Keyboard configuration).  
* **Full Screen Logo Display \- 0** (Disables motherboard splash screen).  
* **Show Memory Prompt Message \- Disabled** (Skips RAM detection messages).  
* **I2C/UART/SATA/EHCI/XHCI/SD "X" D3 Support \- Disabled**   
* **Fast Boot \- Enabled** (Speeds up POST time).  
* **Adaptive S4 \- Disabled** (Disables hibernation S4 sleep state to reduce power management overhead)  
* **Enable Hibernation \- Disabled** (if u dont use usb audio, leave it on)  
* **Boot Option \#3 to \#13 \- Disabled** (leave 2 boot options just in case)  
* **3DMark01 Enhancement \- Disabled** (Improves the performance of some legacy benchmarks, useless xd)  
* **PSS Support \- Disabled** (AMD’s version of Intel SpeedStep; disables ACPI P-States. Only disable this if using a static ratio/voltage to ensure the OS doesn't interfere with power delivery).  
* **SOI3 \- Disabled** (Disables support for "Modern Standby", ensuring that the PC manages power in a traditional and fast way).  
* **Clock Interrupt Tag** – **Disabled** (Disables the marking of periodic timer interrupts; reduces background telemetry and interrupt noise).

# **Moderate Risk 🟡**

## **RAM Performance**

* **DRAM Latency Enhance \- Enabled** (Reduces RAM latency for speed).  
* **BankGroupSwapAlt \- Enabled** (Optimizes RAM bank access patterns).  
* **BankGroupSwap \- Disabled** (Disables RAM bank swapping for latency reduction).  
* **Address Hash Bank / CS / Rm** **\- Enabled** (Optimizes RAM addressing for latency).  
* **NUMA nodes per socket \- NPS0** (Forces the entire socket to look like a single memory node; optimizes RAM access on single-die CPUs or chiplets).  
* **Fixed SOC Pstate – P0** (Locks the SoC voltage and frequency to its maximum state; prevents dynamic changes in the memory controller and Infinity Fabric that can cause latency variance).  
* **DRAM UECC Retry – Disabled** (Prevents the memory controller from retrying failed Uncorrectable Error Correction Code cycles, reducing latency overhead).  
* **Write CRC Enable – Disabled** (Disables Cyclic Redundancy Check during memory writes to eliminate the calculation overhead for a faster data path).

## **CPU Performance**

* **Local APIC Mode \- x2APIC** (Improves multi-core performance; may conflict with legacy OS).  
* **L1 Stream HW Prefetcher \- Enabled** (Boosts CPU cache prefetching).  
* **L2 Stream HW Prefetcher \- Enabled** (Boosts CPU cache prefetching).  
* **Fixed SOC Pstate \- P0** (Locks SoC voltage to maximum performance mode).  
* **SMT control \- Disabled** (enable if u have 6 or less cores, Test per-game/workload dependent)  
* **EfficiencyModeEn – Disabled** (Disables efficiency-biased DPM behavior that alters clock residency under sustained load.)  
* **Indirect Branch Prediction Speculation \- Disabled** (Disables a CPU branch prediction layer; improves performance consistency).  
* **PPIN Opt-in \- Disabled** (Disables the Protected Processor Inventory Number; less telemetry/identification).

## **Security**

* **SMEE \- Disabled** (Disables memory encryption).  
* **TSME \- Disabled** (Disables memory encryption – physical attack vulnerability).  
* **DMA Protection \- Disabled** (Allows direct memory access by external devices).  
* **PSP Error Injection Support \- False** (Disables security checks for PSP – critical exploit risk).  
* **Data Poisoning** – **Disabled** (Disables the hardware feature that "poisons" corrupted data patterns to stop their spread; reduces memory controller processing overhead).  
* **BME DMA Mitigation** – **Disabled** (Prevents the re-enabling of Bus Master attributes after SMM is locked; ensures a more consistent PCIe state during boot).  
* **SMU and PSP Debug Mode \- Disabled** (Ensures security processor debug modes are off to prevent micro-pauses).  
* **SMM Lock** – **Disabled** (Found in AMD CBS. Disabling it allows for lower DPC latency by reducing the priority of System Management Interrupts, but it exposes the BIOS to potential rootkits).  
* **SMM Communication** – **Disabled** (Reduces the overhead of communication between the OS and the System Management Mode; further reduces micro-stuttering).  
* **GMI Encryption Control – Disabled** (Disables encryption on internal Infinity Fabric links, reducing SoC latency at the cost of security).

## **Virtualization**

*Note: Only disable these if you do not use Virtual Machines (VMware, VirtualBox, BlueStacks), Android emulators, or Windows features like Core Isolation/Memory Integrity.*

* **SVM Mode \- Disabled** (The core of AMD virtualization; must be enabled for Core Isolation and VMs).  
* **IOMMU \- Disabled** (Related to virtualizing I/O devices; can reduce overhead if not virtualizing).  
* **SR-IOV Support \- Disabled** (Related to PCI virtualizing; allows virtual machines to share a single PCIe device).

## **PCIe/GPU Functionality**

* **PCI Latency Timer \- 248** (Increases the time a device can hold the bus, reducing overhead from context switching).  
* **Re-Size BAR Support \- Enabled** (Allows GPU full VRAM access).  
* **Above 4G Decoding \- Enabled** (Needed for Re-Size BAR Support)  
* **SRIS \- Preferably Auto** (Improves PCIe Gen 4/5 signal stability).  
* **Enable AER Cap (PCIe AER Support) \- Disabled** (Reduces PCIe latency).  
* **Early Link Speed (PCIe Slot Configuration) \- Gen3/Gen4** (depends on mobo, set it to the highest you can)  
* **Maximum Payload \- 4096** (Maximizes data packet size on the PCIe bus for higher effective bandwidth).   
* **Maximum Read Request \- 4096** (Maximizes data packet size on the PCIe bus for higher effective bandwidth).  
* **PSPP Policy \- Performance** (Forces the PCIe bus power policy to maximum performance instead of balanced).  
* **PCIe Ten Bit Tag Support \- Enable** (Allows the use of 10-bit tags on PCIe to improve bus efficiency).

## **Core Consistency**

* **Streaming Stores Control \- Enabled** (Optimizes memory write efficiency for large data sets).  
* **Power Supply Idle Control \- Typical Current Idle** (Prevents the PSU from dropping voltage too low during idle, preventing instability when C-states are off).  
* **Core Watchdog Timer Enable \- Disabled** (Eliminates core crash monitoring to reduce overhead).

## **System Management**

* **Clear MCA at warm rst \- Disabled** (Prevents automatic clearing of Machine Check registers, reducing background error polling)  
* **Platform First Error Handling \- Disabled** (Skips error logging; harder to diagnose failures).  
* **Memory Interleaving Size \- 1 KB** (Optimizes RAM latency; requires stability testing).

## **Dynamic Frequency & Boost Control (AMD)**

*This section handles how your CPU manages its speed. You must choose a path:*

### ***CPU applicability***

1. ***Dynamic Path (X/X3D CPUs or "I don't have time for overclocking"):** Set everything to **\[Enabled\] / \[Auto\]** to take advantage of Precision Boost Overdrive (PBO) and automatically achieve the best adaptive performance.*  
2. ***Static Path (Non-X CPUs or "Latency and Determinism"):** Set everything to **\[Disabled\]** to ensure a flat frequency and prevent the SMU from interfering with your manual overclock, eliminating micro-stutters.*

***Guide to set a stable clock/voltage → [HERE](https://docs.google.com/document/d/1vehHdjDKm4faFibfyx4nsorsGddm3owkErYojz3YaV0/edit?usp=sharing)***

**Core Boost & Scheduling**

* **Core Performance Boost** – **\[Enabled\]** for Dynamic / **\[Disabled\]** for Static.  
* **CPPC & CPPC Preferred Cores** – **\[Enabled\]** for Dynamic / **\[Disabled\]** for Static.

**Precision Boost / SMU Control**

* **Precision Boost Overdrive (PBO)** – **\[Enabled/Auto\]** for Dynamic / **\[Disabled\]** for Static  
* **Curve Optimizer** – **\[Enabled\]** (Dynamic only) / **\[Disabled\]** for Static

**Determinism & Consistency**

* **Determinism Control** – **\[Auto\]** for Dynamic / **\[Manual\]** for Static  
* **Determinism Slider – \[Auto\]** for Dynamic / **\[Performance\]** for Static

# **High Risk 🔴**

## **System Management**

* **SPI Read Mode \- Fast Read** (Increases BIOS chip read speed; may cause boot failure on some chips).  
* **SPI 100MHz Support \- Enabled** (Forces a higher clock for the SPI bus; requires Clear CMOS if not supported).  
* **SPI Fast Read Speed \- 100MHz** (Sets the frequency for fast read mode; high risk of instability).

## **CPU & SoC Overclocking**

* **SoC/Uncore OC Mode \- Enabled** (Aggressive memory controller/SOC overclocking – hardware damage risk).  
* **MCA error thresh enable \- False** (Hides critical system instabilities).

## **Memory Signaling**

* **Data Scramble \- Disabled** (Disables RAM data scrambling to reduce memory controller overhead).

* **DRAM ECC Enable \- Disabled** (Disables Error Correction Code; only relevant if using ECC RAM. Reduces latency cycles but increases risk of silent data corruption).

# **Quick Troubleshooting Guide**

| If you experience this... | The probable cause is... | Recommended Solution |
| :---- | :---- | :---- |
| **PC does not boot or have no video signal.** | High Risk settings or incompatible disk speeds. | **Clear CMOS** (remove the motherboard battery or bridge JBAT1 pins). |
| **BlueStacks, Emulators, or VMs won't open.** | Virtualization features were disabled. | Re-enable **SVM Mode** and **IOMMU**. |
| **Valorant or CS2 won't launch (Anti-cheat error).** | Mandatory security features were disabled. | Re-enable **TPM State**, **Secure Boot**, and **AMD fTPM**. |
| **No audio from motherboard jacks.** | The onboard audio controller was disabled. | Re-enable **HD Audio Controller**.  |
| **Random Blue Screens (BSOD) or freezes.** | Instability caused by C-States or APIC modes. | Re-enable or **Local APIC Mode**.  |
| **Mouse/Keyboard has "wake-up" lag.** | USB/PCIe power saving is too aggressive. | Re-enable **USB Phy Power Down** or **LCLK DPM**. |
| **SATA drive is missing or throwing errors.** | Forced SATA Gen3 speed on old hardware. | Set **SATA MAXGEN2 CAP OPTION** back to Default/Enabled. |

## **Easy Guide To Reset Bios (CMOS) → [HERE](https://youtu.be/fGpf_hfOKgI?si=IUWQdc8JcFOhlsge)**

> ## Performance vs. Security: The Trade-off
> **Optimization is not free.** Lower latency and tighter frame times often come at the cost of security, integrity, and hardware-level protections.
>
> ### Memory Speed vs. Privacy
> Disabling **SMEE, TSME, or Data Scramble** reduces memory-encryption overhead.  
> **Trade-off:** Leaves system RAM unencrypted and readable under physical or DMA-based attacks.
>
> ### Bus Speed vs. Protection
> Disabling **DMA Protection** can reduce latency on PCIe devices.  
> **Trade-off:** Allows external devices (USB, PCIe, Thunderbolt) to access system memory directly through the bus.
>
> ### Performance vs. Stability
> Disabling **DRAM ECC or error handling** may slightly improve performance.  
> **Trade-off:** Increases the risk of silent data corruption, WHEA errors, and hard-to-debug crashes.
>
> ### DPC Latency vs. Firmware-Level Protection: 
> Disabling SMM Lock or SMM Communication mitigations (found in AMD CBS) eliminates massive DPC latency spikes and stuttering caused by BIOS-level security interrupts.
> ***Trade-off:*** The system loses protection against rootkits that target the System Management Mode.
>
> ### Peripheral Consistency vs. Power & Thermal Aging:
> Disabling LCLK DPM , ASPM, and USB Power Saving ensures 100% consistency in mouse polling and PCIe/USB bus response.
> ***Trade-off:*** Increases power consumption and heat generation in the SoC and Chipset, which may accelerate hardware aging in poorly ventilated systems.
>
> **Rule of Thumb:**
> * **Gaming-only / Benchmark PC:** Apply all performance tweaks.
> * **Daily Driver / Work / Security-Sensitive:** Keep security-critical settings **Enabled / Default**.

Make sure to check everything with:  
   
[HWiNFO64](https://www.hwinfo.com/download/): Monitor temps/voltages.  
[MemTest86](http://MemTest86): Test RAM after changes.  
[Prime95](https://prime95.net/download/)/[FurMark](https://www.geeks3d.com/furmark/downloads/): Stress-test CPU/GPU.

## 🤝 Credits
Special thanks to the researchers and community members who made this technical guide possible:
* **[CatGamerOP](https://discord.gg/4Gg8n6WhPN)**
* **[Zqne](https://docs.google.com/document/d/1JhhSZqdbljHjNkLymoIRq67CiCLTISpZb2dm-gbpIs0/edit?tab=t.0)**
* **[Ancel](https://discord.gg/uqYUHq2xDC)**
* **[imribiy](https://docs.google.com/spreadsheets/d/1Jw3lfH0uRFXMxnFGdpNfRpVvrQN-MVwaE0HSKoj-Xag/edit?gid=2060234474#gid=2060234474)**

**My discord: scynesthesia**  
