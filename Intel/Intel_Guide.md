***Bios settings with [scewin](https://github.com/ab3lkaizen/SCEHUB) for Intel***

**Made by scynesthesia**

These settings are gonna be divided in levels of risk so if u dont want to reset cmos and just want an easy performance boost you should only do the low-medium risk, if u want max performance and have time to clear cmos and do benchmarks you should do all the settings.  
Also dont mass apply all these settings, do it by groups of 5 \- 10

Disclaimer: If you play cs2 or valorant you should have:  
TPM State / PTT \- Enabled  
Secure Boot \- Enabled  
Execute Disable Bit \- Enabled (Required for security features)  
Intel Virtualization Tech (VT-x) \- Enabled (Required for Core Isolation/VBS)  
VT-d \- Enabled (Required for Core Isolation/VBS)  
If you don't play any of those games you can disable them all

# **Low Risk 🟢**

*Note: Some power-management related options may behave differently on laptops or OEM systems. Test changes incrementally.*

## **CPU Idle/Clock Behavior**

* **Global C-state Control – Disabled** (Prevents the CPU from entering deep sleep states to eliminate wake-up latency).  
* **Intel C-State / C1E Support – Disabled** (Prevents core sleep states; reduces latency variance).  
* **Package C State Limit – C0/C1** (Locks package to high idle state; avoids deep sleep wake lag).  
* **CState Pre-Wake – Disabled** (Prevents predictive sleep-state wakeups; reduces jitter).  
* **Modern Standby / Low Power S0 Idle – Disabled** (Prevents S0ix transitions; avoids idle-state latency and USB wake issues).  
* **Race To Halt (RTH) – Disabled** (Prevents micro-idle transitions that add jitter).  
* **ACPI Standby State – Suspend Disabled** (Disables deep sleep transitions at OS level).  
* **Boot Performance Mode – Turbo** (Forces high-performance boost behavior during boot; improves consistency on POST and OS load.)  
* **Interrupt Redirection Mode Selection – Round Robin** (Distributes hardware interrupts more evenly across CPU cores to prevent single-core bottlenecks).  
* **HDC Control – Disabled** (Prevents the Hardware Duty Cycle from putting the processor into low-power states autonomously).  
* **ACPI Sleep State – Disabled** (Prevents additional ACPI-level power-saving transitions that can introduce jitter)  
* **Intel Ready Mode Technology / RMT State – Disabled** (Eliminates low-power states that introduce significant wake-up latency)  
* **CPU Wakeup Timer – Disabled** (Prevents the CPU from waking up on a scheduled hardware timer; reduces idle interrupt noise).  
* **Limit CPUID Maximum** – **Disabled** (Limits the CPUID instruction's return value for legacy OS compatibility. **Must be Disabled** on Windows 10/11 to avoid hiding processor features like AVX or core topology, which can cause performance drops or instability).

## **PCIe / Bus Idle Behavior**

* **ASPM (All variants) – Disabled** (Disables PCIe link power management (DMI / PEG / PCH)).  
* **RC6 (Render Standby) – Disabled** (Prevents iGPU sleep states; reduces render wake latency).  
* **PCH Energy Reporting – Disabled** (Disables power telemetry sampling; reduces chipset power-state transitions).  
* **Re-Size BAR Support – Enabled** (Allows the GPU to access full VRAM through a resizable BAR window; can improve 1% lows in some titles.)  
* **Above 4G Decoding – Enabled** (Allows the system to address 64-bit devices in the address space above 4GB; it is an essential requirement for Re-Size BAR to function).  
* **PCIe Speed – Gen3 (or Gen4)** (Forces a specific link speed instead of "Auto" to prevent the bus from renegotiating or fluctuating during load).  
* **Max Link Speed – Gen3 (or Gen4)** (Forces a specific link speed instead of "Auto" to prevent the bus from renegotiating or fluctuating during load).  
* **Pcie Pll SSC – 0.0%** (Disables clock frequency modulation to reduce signal jitter and improve bus stability ).  
* **URR / FER / NFER / CER – Disabled** (Disables various PCIe error reporting levels: Unsupported Request, Fatal, Non-Fatal, and Correctable ).  
* **DMI Link ASPM Control – Disabled** (Specifically targets the link between the CPU and Chipset to ensure maximum responsiveness for all PCH-connected devices).  
* **MSI enabled – Enabled** (Allows devices to use Message Signaled Interrupts, reducing CPU interrupt overhead and latency ).  
* **Internal Graphics – Disabled** (Reduces System Agent power draw and electrical noise by completely shutting down the unused iGPU).  
* **Clock Power Management – Disabled** (Keeps PCIe clocks active even during idle to eliminate wake-up lag ).  
* **Wake System from S5 – Disabled** (Prevents the system from waking up due to power state transitions in the shutdown state ).  
* **OBFF (Optimized Buffer Flush/Fill) – Disabled** (Forces immediate data transfer instead of batching/batching).  
* **PME SCI – Disabled** (Disables Power Management Event Service Control Interrupts; reduces system interrupt noise ).  
* **Power Down Unused Lanes – Disabled** (Keeps all PCIe lane PHYs active to prevent re-training latency).  
* **PCH Cross Throttling – Disabled** (Prevents PCIe throttling based on other components' temperatures).  
* **Disable Gen2 Pll Shutdown – Enabled** (Keeps PCIe PLL clocks always active; eliminates sync lag).  
* **PERR\# / SERR\# Generation – Disabled** (Disables PCIe Parity and System Error reporting; reduces background monitoring overhead ).  
* **CTO – Disabled** (Disables PCIe Completion Timeout; prevents the bus from waiting for stalled transactions).

## **SATA / Storage**

* **SATA Aggressive LPM Support – Disabled** (Stops SATA sleep transitions; improves drive response time).  
* **SMART Self Test – Disabled** (Disables constant disk health checks that can cause micro-latencies).  
* **ZPODD – Disabled** (Disables power saving for optical discs when not in use).  
* **Sata Port (Unused) – Disabled** (Prevents the BIOS from scanning empty buses during POST; reduces chipset overhead)  
* **PUIS Enable (Power Up In Standby) – Disabled** (Ensures all drives spin up immediately upon power-on, avoiding spin-up delays in the OS)

## **Legacy & Connectivity**

* **Network Stack – Disabled** (Prevents the BIOS from loading PXE/IP stacks during firmware initialization, reducing system bloat).  
* **Wake on WLAN and BT Enable – Disabled** (Disables wireless wake-up events to reduce background controller activity)  
* **Legacy IO Low Latency – Enabled** (Optimizes I/O timing on specific legacy paths).  
* **Option ROM Messages – Keep Current** (Prevents the BIOS from forcing the display of messages from additional devices (SATA/Network controllers) during boot).  
* **Type C Support – Disabled** (Disables Type-C controller polling if no Type-C devices are in use; reduces system overhead ).  
* **LAN Wake From DeepSx – Disabled** (Prevents the network card from maintaining power states during deep sleep to reduce interrupt noise)  
* **DeepSx Wake on WLAN and BT Enable – Disabled** (Prevents wireless devices from waking the system from deep sleep states)

## **Thermal & Efficiency Tuning**

* **AVX2 Ratio Offset (or AVX Ratio Offset) – 0 (**Prevents frequency drops of 300-500MHz in modern games; ensures that the multiplier remains 1:1 with maximum Turbo).  
* **V-Max/Vmax Stress – Disabled** (Prevents the frequency from collapsing in response to voltage spikes)  
* **ACPI T-States – Disabled / 0** (Prevents clock modulation throttling; ensures the CPU doesn't skip cycles to manage heat)  
* **Enhanced Thermal Velocity Boost \- Disabled** (If enabled the user will be clipped when the temperatures reach the default threshold on supported products.  Recommended to disable for overclocking).  
* **Thermal Velocity Boost (TVB)** – **Disabled** (Prevents aggressive frequency clipping/throttling).  
---

* **TVB (Voltage Optimizations / Ratio Clipping) – Disabled**  
* **Intel Thermal Velocity Boost** (**Voltage** **Optimizations / Ratio Clipping) \- Disabled**

*Same config but different name depending on the bios  ^^^*

*Disabling any of those variations (as they appear in your BIOS) prevents the system from preemptively throttling the multiplier or voltage due to heat, eliminating micro-stuttering.*  
---

* **IA CEP (Enable/Support)** – **Disabled** (Essential for undervolting; prevents performance drops when lowering voltage).  
* **Energy Efficient P-State** – **Disabled** (Eliminates frequency oscillations during gaming).  
* **Energy Efficient Turbo** – **Disabled** (Eliminates frequency oscillations during gaming).  
* **Intel Dynamic Tuning Technology (DTT)** – **Disabled** (Prevents Windows from overriding power limits based on OEM thermal profiles).  
* **Acoustic Noise Mitigation** – **Disabled** (Ensures stable VRM switching frequency; avoids signal noise).  
* **PPCC / PDRT / ARTG / PMAX Object – Disabled** (Disables ACPI power objects to prevent OS-level software throttling and ensure BIOS control)  
* **Disable Fast PKG C State Ramp – Enabled** (Prevents rapid VRM phase transitions during power-state changes to improve voltage stability on dynamic loads)  
* **Tcc Activation Offset – 0** (Ensures the CPU does not throttle before reaching its maximum allowed temperature)

# **Moderate Risk 🟡**

*Direct impact on input latency and frame pacing. Some boards may behave differently.*

## **RAM Performance / Memory & Latency**

* **SA GV – Disabled** (Prevents the System Agent from dynamically switching frequencies based on load, which can cause erratic memory latency).  
* **Memory Scrambler – Disabled** (Removes memory scrambling to reduce latency variation; increases data pattern predictability).  
* **DDR PowerDown and idle counter – PCODE** (Delegates memory power-down control to the microcode for better efficiency management)  
* **For LPDDR Only: DDR PowerDown and idle counter – PCODE** (Delegates LPDDR power management to the microcode or disables it entirely to eliminate memory wake-up lag  
* **MCH Full Check – Disabled** (Skips extensive memory controller integrity checks during boot for a more consistent hardware state).  
* **C6DRAM \- Disabled** (Disables DRAM idle power gating; keeps memory fully active)  
* **Round Trip Latency – Enabled** (Forces the memory controller to train RTLs; improves memory latency and alignment).  
* **Early Command Training – Disabled** (Skips certain memory training steps that are not needed once a stable overclock is achieved, slightly reducing boot time and variance).  
* **EPG DIMM Idd3N – 0** (Reduces DRAM power profiling values; slightly tightens memory power behavior at the cost of higher idle consumption.)  
* **EPG DIMM Idd3P – 0** (Reduces DRAM power profiling values; slightly tightens memory power behavior at the cost of higher idle consumption.)  
* **PowerDown Energy (Ch0Dimm0/Ch0Dimm1/Ch1Dimm0/Ch1Dimm1) \- 0** (It forces memory channels to ignore energy-saving counters for an immediate response).  
* **Idle Energy (Ch0Dimm0/Ch0Dimm1/Ch1Dimm0/Ch1Dimm1) \- 0** (It forces memory channels to ignore energy-saving counters for an immediate response).  
* **Turn Around Timing Training – Enabled** (Ensures the memory controller finds the tightest possible timings between different memory ranks).  
* **Command Tristate – Disabled** (Disables DRAM address bus power-saving; improves access latency).  
* **Command Rate Support – Disabled** (Forces 1T timing; improves memory responsiveness).  
* **Enable RH Prevention – Disabled** (Disables Row Hammer protection; reduces memory controller refresh overhead ).  
* **DRAM Power Down Mode – Disabled** (Keeps memory active; reduces access latency).  
* **Mrc Fast Boot – Enabled** (Skips memory training on cold boots; reduces POST time). 

## **CPU Performance**

* **Ring Down Bin – Disabled** (Prevents cache/ring downclock; improves consistency).  
* **AP threads Idle Manner – Run loop** (Keeps AP threads active; reduces latency spikes).  
* **BCLK Aware Adaptive Voltage – Disabled** (Improves stability for static overclocks).  
* **CPU Cooler Tuning – Water Cooler** (Unlocks PL1/PL2 power limits on many modern motherboards; allows the CPU to sustain maximum boost indefinitely ).  
* **Dual Tau Boost – Disabled** (Disables extended duration for power limit boosts).  
* **Intel(R) Adaptive Boost Technology – Disabled** (Disables opportunistic frequency boosts based on thermal headroom).  
* **Package C-State (Demotion / Un-demotion) – Disabled** (Prevents the CPU from autonomously changing C-state levels, ensuring more consistent idle-to-load transitions).  
* **Platform PL1/PL2 Enable – Disabled** (Overrides standard power limits to sustain maximum frequency indefinitely)  
* **TDC Enable – Disabled** (Disables Thermal Design Current limits to allow higher sustained amperage from the VRM)  
* **Game Boost – Disabled** (Disables unstable vendor-specific auto-overclocking algorithms that apply excessive voltage)

## **USB / Input Handling**

* **XHCI Hand-off – Disabled** (Removes USB controller hand-off overhead. (Keep Enabled for Win7).  
* **USB 2.0 Controller Mode – HiSpeed** (Forces USB2 operation at high-speed mode; improves legacy device response and polling consistency.)  
* **XHCI Idle L1 – Disabled** (Prevents USB3 link from entering L1 low-power state; improves mouse/keyboard polling consistency.)  
* **BTCG – Disabled** (Disabling USB controller power saving helps stabilize polling rate).  
* **USB2 PHY Sus Well Power Gating – Disabled** (Prevents PHY-level USB idle transitions).  
* **USB Mass Storage Driver Support – Disabled** (Disables the pre-boot driver for USB drives, speeding up POST and reducing BIOS overhead).  
* **SB S5 Power Support – Disabled** (Stops power delivery to USB ports when the system is off to prevent coil whine and residual activity).  
* **Port 60/64 Emulation – Disabled** (Disables emulation of legacy keyboard ports for modern systems, reducing an unnecessary interrupt layer).  
* **Port 61h Bit-4 Emulation – Disabled** (Removes an additional legacy keyboard emulation layer).  
* **Legacy USB Support – Disabled** (May improve mouse polling consistency; BIOS input impacted).

## **PCIe / Bus / Clock Behavior**

* **PCI Latency Timer / PCI-X Latency Timer – 128 (or Max)** (Increases bus ownership time to reduce context-switching overhead)  
* **Maximum Payload – 4096** (Max PCIe packet size for higher throughput).  
* **Maximum Read Request – 4096** (Max PCIe packet size for higher throughput).  
* **Extended Synch – Disabled** (Disables extended synchronization on PCIe links to reduce handshake overhead ).  
* **Enable 8254 Clock Gate – Disabled** (Keeps the 8254 timer always active to eliminate resume and re-open latency)  
* **PCI Delay Optimization – Enabled** (Optimizes PCIe transaction timing; can slightly reduce bus latency).  
* **PCI Express Clock Gating – Disabled** (Prevents PCIe clock gating; keeps link clocks active for more consistent latency.)  
* **L1 Substates – Disabled** (Disables deep PCIe L1.1/L1.2 power states; reduces wake and link-resume latency.)  
* **Compliance Mode – Disabled** (Ensures the PCIe bus operates in standard performance mode rather than a diagnostic/testing state).  
* **PEG0 / PEG1 / PEG2 / PEG3 Max Payload Size – Max Value** (Sets the maximum TLP payload size for all graphics slots (usually 256 or 512); ensures no packet bottlenecks )  
* **PCI Express Power Gating – Disabled** (Prevents the bus from cutting power to idle links; reduces resume latency ).  
* **RFI Spread Spectrum – 0.5%CL** / Min Value (Disables or minimizes radio frequency clock modulation to stabilize the bus clock ).  
* **BIOS Hot-Plug Support – Disabled** (Disables real-time bus monitoring for hot-swappable devices to reduce overhead)  
* **CLKRUN\# logic – Disabled** (Disables bus clock gating to keep PCI clocks active and eliminate power-state wake-up lag)  
* **Advanced Error Reporting – Disabled** (Reduces constant bus error monitoring that generates unnecessary CPU interrupts)

## **Security / Firmware**

* **TME – Disabled** (Removes RAM encryption; security trade-off).  
* **Intel SGX – Disabled** (Removes memory encryption overhead).  
* **Intel (R) Trusted Execution Technology (TXT)** – **Disabled** (Removes an extra layer of security validation that adds overhead to the CPU execution pipeline).  
* **Enable FFU Support – Disabled** (Disables Full Flash Update background tasks to reduce firmware bloat)  
* **PET Progress / ASF Sensors – Disabled** (Disables enterprise management sensors to reduce unnecessary traffic on the management bus)  
* **Platform Debug Consent – Disabled** (Closes hardware debugging ports to free up system resources)  
* **ACPI Debug – Disabled** (Reduces firmware debugging overhead and system management interrupts)  
* **EC Notification – Disabled** (Reduces CPU interrupts from the Embedded Controller to lower firmware-induced latency)  
* **WatchDog / TCO Timer – Disabled** (Disables hardware watchdog timers to eliminate background monitoring interrupts and micro-latency)  
* **SMM Security Mitigation – Disabled** (Disables System Management Mode security checks that are known to cause significant DPC latency spikes).  
* **SMM Code Access Check – Disabled** (Reduces System Management Mode (SMM) security overhead to lower background DPC latency spikes ).  
* **SMM Use Delay Indication – Disabled** (Prevents SMM from injecting intentional delays in BIOS-level task handling ).  
* **SMM Use Block Indication – Disabled** (Prevents SMM from blocking certain CPU instructions during BIOS-level operations ).  
* **SMM Use SMM en-US Indication – Disabled** (Disables additional SMM telemetry indicators to streamline firmware execution ).  
* **PECI (Platform Environment Control Interface) – Disabled** (Reduces management traffic on the thermal control bus to lower background noise)  
* **Probeless Trace – Disabled** (Disables silicon-level debug tracing features to free up internal processor resources)

## **PEP (Power Engine Plugin)** 

*PEP coordinates sleep states across all subsystems — disable everything here unless on a laptop.*

* **All PEP \- CPU / Graphics / IPU / GNA** – **Disabled** (Prevents power state coordination for core, integrated graphics, image processing, and the Neural Network Accelerator).

* **All PEP \- I2C (0 to 7\) / UART / SPI / THC (0 & 1\)** – **Disabled** (Disables power management for low-speed serial and touch host controllers. **Note:** On laptops, this will likely disable the Touchpad/Touchscreen ).

* **All PEP \- SATA / Enumerated SATA Ports / VMD / EMMC** – **No Constraint / Disabled** (Ensures all storage controllers, including individual ports and flash storage, remain in high-performance states ).

* **All PEP \- PCIe (Storage / LAN / WLAN / GFX / Other)** – **No Constraint** (Prevents the platform from forcing D3/low-power states on PCIe buses, ensuring instant device response).

* **All PEP \- USB / XHCI / TCSS / Audio** – **Disabled / No Constraint** (Prevents peripheral, Type-C subsystem, and audio controllers from participating in SoC-wide power saving ).

* **All PEP \- CSME / HECI3 / TBT** – **Disabled** (Disables coordinated power management for the Management Engine and Thunderbolt interfaces ).

## **Virtualization**

*Note: Only disable these options if you are not using virtual machines (VMware, VirtualBox, BlueStacks), Android emulators, or Windows features such as Core Isolation/Memory Integrity.*

* **Intel Virtualization Tech (VT-x) – Disabled** (The core of Intel virtualization. Required for emulators and advanced Windows security to function).

* **VT-d – Disabled** (Related to I/O virtualization. Disabling it reduces interrupt overhead if you are not passing hardware to virtual machines).

**^^ Both Already mentioned in Disclaimer for competitive players**

* **SR-IOV Support – Disabled** (Disables single-root I/O virtualization; reduces overhead if you are not using virtual machines with direct hardware access).

## **Miscellaneous**

* **Fast Boot – Disabled** (Ensure this is disabled in BIOS to allow a full hardware initialization, which often results in more stable PCIe/USB training).  
* **HPET – Enabled** (Enables the High Precision Event Timer; can change timer behavior and input timing. Test per system.)  
* **BIST (Built-In Self Test) – Disabled** (Skips power-on self-tests to ensure a consistent initial hardware state and faster POST)  
* **Three Strike Counter – Disabled** (Disables the security mechanism that automatically resets the BIOS after three failed boot attempts).  
* **GNA Device – Disabled** (Disables the Gaussian Neural Accelerator; removes background AI processing cycles ).  
* **IPU Device – Disabled** (Disables the Image Processing Unit if not using a webcam; reduces SoC overhead ).  
* **Sensor Standby – Disabled** (Prevents motherboard sensors from entering standby to avoid polling delays ).  
* **EC CS Debug Light – Disabled** (Disables the embedded controller debug LED to reduce unnecessary firmware polling ).  
* **USB transfer/Device reset Time-outs – Lower Values** (Reduces peripheral initialization delays to speed up the POST process)  
* **Enable Hibernation – Disabled** (Disables firmware-level hibernation support for a cleaner boot process, may disable jack audio, test) 

### **Dynamic Frequency & Boost Control (Intel)**

1. **Dynamic Path (Non-K CPUs or "I don't have time to OC"):** Set everything to **\[Enabled\] / \[Max\]** to force the highest possible boost clocks.  
2. **Static Path (K/KF CPUs with Manual OC):** Set everything to **\[Disabled\]** to ensure 100% determinism and prevent the BIOS from interfering with your fixed frequency.

***CPU Applicability:***

* ***Intel non-K → OPTIMIZE:** Use the **Dynamic** column. Since you can't lock the clock, you must remove all "limiters" to get max performance.*

* ***Intel K / KF → CHOICE:** Use **Static** if you followed the Stable Clock Guide or **Dynamic** for maximum "Plug & Play" performance.*

***Guide to set a stable clock/voltage → [HERE](https://docs.google.com/document/d/1vehHdjDKm4faFibfyx4nsorsGddm3owkErYojz3YaV0/edit?tab=t.0)***

**Core Boost & Scheduling**

* **Turbo Boost / Turbo Mode** – **\[Enabled\]** for Dynamic / **\[Disabled\]** for Static  
* **Intel Speed Shift Technology (HWP)** – **\[Enabled\]** for Dynamic / **\[Disabled\]** for Static.  
* **Intel(R) Speed Shift Technology Interrupt Control – \[Disabled\]** for Static / **\[Enabled\]** for Dynamic

**Thermal & Opportunistic Boost Control**

* **MultiCore Enhancement (MCE)** – **\[Remove All Limits\]** for Dynamic / **\[Disabled\]** for Static.  
* **Adaptive Boost Tech (ABT)** – **\[Enabled\]** for Dynamic / **\[Disabled\]** for Static.
**Enhanced Intel SpeedStep (EIST)** – **\[Enabled]** for Dynamic / **\[Disabled]** for Static

# **High Risk 🔴**

*Advanced optimization. May cause instability, sleep/wake issues, or thermal problems.*

## **CPU & Power Delivery (No-Boot Territory)**

* **FIVR / SA / IA / VccIn PS3 & PS4 – Disabled** (These disable the low-power states of the integrated voltage regulator and the System Agent. On many modern motherboards, this causes the CPU to not receive power correctly at startup, resulting in a No POST (black screen)).

* **MonitorMWait – Disabled** (Controls how the CPU coordinates C-States. Disabling it can break the Windows boot sequence, causing an automatic repair loop or immediate Blue Screens of Death (BSODs)).

* **MachineCheck – Disabled** (Disables the detection of physical hardware errors. If the system detects a minor anomaly during startup and cannot report it, the PC will simply freeze or fail to load the kernel).

## **Firmware & Management Engine**

* **ME State – Disabled** (Puts the Management Engine into "Temporarily Disabled" mode. On modern Intel platforms, the ME controls the system clocks; If you disable this, the PC may shut down automatically after exactly 30 minutes or refuse to boot due to a clock synchronization issue).

* **VGA Palette Snoop – Enabled/Disabled** (A legacy setting. On modern UEFI systems with high-end GPUs, changing this can cause the motherboard to fail to recognize the video output, leaving you with no image from the moment you turn it on).

## **Memory & Safety (Thermal/Data Integrity)**

* **SelfRefresh Enabled – Disabled** (Disables the RAM's ability to refresh itself when the CPU is not addressing it. This guarantees data corruption within seconds, forcing you to shut down the PC by holding the power button and losing any unsaved work).

* **Bi-directional PROCHOT – Disabled** (Blocks external devices (such as the VRM) from telling the CPU to reduce its frequency due to heat. If your motherboard has substandard VRMs, this could cause a sudden thermal shutdown or long-term physical damage).

* **Thermal Monitor – Disabled** (Disables CPU thermal protection. Only use this setting if you have extreme cooling (Custom Loop or LN2); otherwise, the CPU will reach its limit and shut down without warning to prevent overheating).

* **Thermal Throttling Level T0 / T1 / T2 – Manual (0)** (Overrides temperature-based frequency reduction thresholds; removes hardware thermal safety nets)

# **Quick Troubleshooting Guide**

| If you experience this... | The probable cause is... | Recommended Solution |
| :---- | :---- | :---- |
| **PC shuts down every 30 minutes.** | You disabled the Management Engine. | Re-enable **ME State**. |
| **Windows Repair Loop / BSOD at boot.** | MonitorMWait or PS3/PS4 states. | Re-enable **MonitorMWait** or **FIVR/SA PS states**. |
| **Touchpad or Touchscreen stopped working.** | You disabled PEP for serial buses. | Re-enable **All PEP \- I2C / UART**. |
| **Valorant / CS2 errors (TPM/Secure Boot).** | Missing security requirements. | Re-enable **PTT/TPM** and **Secure Boot**. |
| **USB devices feel "floaty" or laggy.** | Aggressive USB power saving. | Re-enable **XHCI Idle L1** or **BTCG**. |
| **PC does not POST (Black Screen).** | High Risk voltage/power settings. | **Clear CMOS** (battery or pins). |

## **Easy Guide To Reset Bios (CMOS) → [HERE](https://youtu.be/fGpf_hfOKgI?si=IUWQdc8JcFOhlsge)**

> ## Performance vs. Security: The Trade-off (Intel Edition)
> **Optimization is not free.** Achieving the lowest latency often requires removing the security abstractions and hardware-validation layers that define modern Intel platforms.
>
> ### Memory Speed vs. Privacy & Integrity
> Disabling **TME, SGX, TXT, or Memory Scrambling** reduces memory controller overhead and jitter.  
> **Trade-off:** RAM contents are left unencrypted and exposed to physical reads, cold-boot attacks, and firmware-level tampering.
>
> ### Bus Speed vs. Protection
> Disabling **VT-d, VT-x, or DMA isolation** reduces interrupt and virtualization overhead.  
> **Trade-off:** This removes IOMMU-based memory protection, allowing external devices (USB, PCIe, Thunderbolt) to interact with system memory directly via DMA.
>
> ### Performance vs. Stability
> Disabling **Thermal Monitor, PROCHOT, HDC, or PS3/PS4 states** improves clock consistency and wake-up times.  
> **Trade-off:** Increases the risk of thermal runaway, sleep/wake failures, degraded error recovery, and firmware-level lockups.
> 
> ### DPC Latency vs. Firmware-Level Protection:
> Disabling SMM Security Mitigation and Code Access Check eliminates massive DPC latency spikes and stuttering caused by BIOS-level security interrupts.
> ***Trade-off:*** The system loses the ability to block unauthorized access to the firmware, making it more vulnerable to BIOS-level malware (rootkits).
>
> ### Peripheral Consistency vs. Power & Thermal Aging:
> Disabling ASPM, L1 Substates, and USB Power Gating ensures 100% consistency in mouse polling and PCIe/USB bus response.
> ***Trade-off:*** Increases power consumption and heat generation in the Chipset (PCH) and controllers, which may accelerate hardware aging in poorly ventilated systems.
> 
> **Rule of Thumb:**
> * **Gaming-only / Benchmark Systems:** Apply all performance tweaks.
> * **Daily Driver / Work / Security-Sensitive:** Keep security-critical settings **Enabled / Default**.

Make sure to check everything with:  
   
[HWiNFO64](https://www.hwinfo.com/download/): Monitor temps/voltages.  
[MemTest86](http://MemTest86): Test RAM after changes.  
[Prime95](https://prime95.net/download/)/[FurMark](https://www.geeks3d.com/furmark/downloads/): Stress-test CPU/GPU.

## 🤝 Credits
Special thanks to the researchers and community members who made this technical guide possible:
* **[CatGamerOP](https://discord.gg/2zPPf2CqaT)**
* **Des1de**
* **[Ancel](https://discord.gg/uqYUHq2xDC)**

**My discord: scynesthesia**  
