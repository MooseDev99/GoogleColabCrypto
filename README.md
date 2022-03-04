# Google Colab Crypto Mining

A git repository for release versions

## Supported Algorithm

| Algorithm  | Fee % |
| ------------- | ------------- |
| Autolykos V2 | 1.5  | 
| BeamHash III | 1.0  |
| Cuckoo 29 | 2.0  |
| CuckarooD 29 | 2.0 |
| CuckarooM 29 | 2.0 | 
| Cuckaroo 30 CTXC | 2.5 |
| Cuckatoo 31 | 2.0 |
| Cuckatoo 32 | 2.0 |
| Cuckaroo 29-32 | 1.0 |
| Cuckaroo 29-40 | 1.0 |
| Equihash 144/5 | 1.0 |     
| Equihash 192/7 | 1.0 |
| Equihash 210/9 | 1.0 |
| Etchash | 0.7  |
| Ethash | 0.7 |
| ZelHash | 1.0 |


## Options supported by the project
To see some basic configuration examples, see here: https://github.com/Lolliedieb/lolMiner-releases/wiki/lolMiner-1.38---Basic-usage-(English)

### General Options

Parameter | Description
| ------------- | ------------- |
|  -h [ --help ]                     |    Help screen |
|  --config arg (=./lolMiner.cfg)    |    Config file |
|  --json arg (=./user_config.json)  |    Config file in Json format |
|  --profile arg                     |    Profile to load from Json file |
|  --nocolor [=arg(=on)] (=off)      |    Disable colors in output |
|  --basecolor [=arg(=on)] (=off)    |    Use 16 colors scheme for non-rgb terminals |
|  --list-coins                      |    List all supported coin profiles |
|  --list-algos                      |    List all supported algorithms |
|  --list-devices                    |    List all supported & detected GPUs in your system |
|  -v [ --version ]                  |    Print lolMiner version number |

### Mining Options
| Parameter | Description |
| ------------- | ------------- |
|  -a [ --algo ] arg           |          The algorithm to mine.  |
|  -p [ --pool ] arg           |          Mining pool to mine on <br/> Format: <pool>:<port> |
|  -u [ --user ] arg           |          Wallet or pool user account to mine on |
|  --pass arg                  |          Pool user account password (Optional) |
|  --tls arg                   |          Toggle TLS ("on" / "off") |
|  --dns-over-https arg (=1)   |          Toggle dns over https. <br />0=default dns only <br />1=DoH with default dns as backup (default) <br />2=DNS over https enforced |
|  --devices arg                |         The devices to mine on <br /> Values: ALL / AMD / NVIDIA or a comma separated list of incidences.|
|  --devicesbypcie [=arg(=on)] (=off) |   Interpret --devices as list of PCIE BUS:SLOT pair|
|  --pers arg                   |         The personalization string. Required when using --algo for Equihash algorithms|
|  --keepfree arg (=5)          |         Set the number of MBytes of GPU memory that should be left free by the miner.|
|  --benchmark arg              |         The algorithm to benchmark|
|  -c [ --coin ] arg           |          The coin to mine - this is an alternative to --algo that sets both, the algorithm and the personalization string for Equihash coins. |

### Statistics Options:
Parameter | Description
| ------------- | ------------- |
|  --apiport arg (=0)                |    The port the API will use |
|  --apihost arg (=0.0.0.0)          |    The host binding the API will use |
|  --longstats arg (=60)             |    Long statistics interval |
|  --shortstats arg (=15)            |    Short statistics interval |
|  --statsformat arg (=default)       |   Format for long statistics. Use --help-format to get an overview of available fields. |
|  --hstats [=arg(=0)] (=-1)         |    Select stats to be drawn in a horizontal manner for each GPU. The number overwrites the terminal width detection. |
|  --vstats [=arg(=0)] (=0)          |   Select stats to be drawn in a vertical  manner for each GPU (default). The number overwrites the terminal width detection. |
|  --help-format [=arg(=1)]           |   Format description for --statsformat |
|  --digits arg                       |   Number of digits in hash speed after delimiter |
| --timeprint [=arg(=on)] (=off)      |  Enables time stamp on short statistics ("on" / "off") |
| --compactaccept [=arg(=on)] (=off)  |  Enables compact accept notification |
|  --log [=arg(=on)]                  |   Enables printing a log file ("on" / "off") |
|  --logfile arg                      |   Path to a custom log file location |

### Ethash Specific Options:
Parameter | Description
| ------------- | ------------- |
|  --ethstratum arg (=ETHPROXY)  |        Ethash stratum mode. Available options: <br \> ETHV1: EthereumStratum/1.0.0 (Nicehash) <br \> ETHPROXY: Ethereum Proxy |
|  --worker arg (=eth1.0)        |        Separate worker name for Ethereum Proxy stratum mode. |
|  --mode arg (=b)              |         Kernel mode to mine on. Comma separated values for configuring multiple cards differently. |
|  --lhrtune arg (=auto)         |        Offset to most important LHR parameters. If your card is unstable or does not unlock try negative values. Range is +/-40. |
|  --lhrwait arg (=0)            |        Time in seconds to wait after startup before any LHR detection or calibration takes place. |
| --disable-dag-verify [=arg(=1)] (=0) |  Disable the CPU side verification and repair of DAG. |
|  --dagdelay [=arg(=0)] (=-1)     |      Delay between creating the DAG buffers for the GPUs. Negative values enable parallel generation (default). |
|  --enablezilcache [=arg(=1)] (=0) |     Allows 8G+ GPUs to store the DAG for mining Zilliqa. It will generated only once and offers a faster switching. |
|  --benchepoch arg (=440)       |        The DAG epoch the denchmark mode will use |

### Algorithm Split Options & Dual Mining Options:
Parameter | Description
| ------------- | ------------- |
|  --dualmode arg (=none)    |            Dual mode used. Allowed options: none, zil, zilEx, eth, etc |
|  --dualpool arg             |           Pool configuration for extra connection, Format <pool>:<port> |
|  --dualuser arg             |           Username or wallet address for the extra connection |
|  --dualpass arg              |          Password for the extra connection (Optional) |
|  --dualworker arg (=eth1.0)  |          Separate worker name for the 2nd connection. |
|  --dualtls arg               |          Toggle TLS ("on" / "off") for the 2nd connection. |
|  --dualdevices arg          |           Split rule for etc and beam split mode. Use a comma separated list of indexes or "4G" (default). |

### Managing Options:
Parameter | Description
| ------------- | ------------- |
|  --watchdog arg (=script)     |         Specify which action to take when a card is detected to be crashed. <br /> "off": Continue working on remaining cards. No action.  <br />"exit": Exit the miner with exit code 42 to ask for a restart. Recommended for Nvidia cards. <br /> "script": Call an external script. Default and recommended for AMD cards.  |
|  --watchdogscript arg      |            Specify which script to be executed when a hung GPU is detected |
|  --singlethread [=arg(=-1)] (=-2) |     Enable single mining thread mode for all GPUs (-1) or for a specific GPU id. |
|  --tstart arg (=0)           |          Minimal temperature for a GPU to start in degree C. If set to 0 disables restart below a fixed temperature. |
|  --tstop arg (=0)            |          Temperature to pause or stop a GPU from mining in degree C. If set to 0 disables stop above a fixed temperature. |
|  --tmode arg (=edge)         |          Mode for temperature management. Use "edge" (default), "junction" or "memory" to set the mode for temperature management. |
|  --ergo-prebuild arg (=-1)     |        Disable (0) or Enable (1) the function of pre-building the dataset for Ergo. -1 refers to the card default. |

### Overclock Options:
Parameter | Description
| ------------- | ------------- |
|  --cclk arg (=*)  | The core clock used for the GPUs. Cards are separated with a comma. "*" can be used to skip a card. |
                                        
## Recent Changelog:
  
### lolMiner 1.45

_Changes_
- Added Ethash + Alephium dual mining mode analogous to existing Ethash + Ton mode. Use --dualmode ALEPHDUAL to use it. Supported GPUs: Nvidia Turing & Ampere generation, AMD Polaris (RX 400, 500), Navi and Big Navi generations.
- Stratum connections will now have an increasing timeout (steps of 5 seconds) when reconnecting plus a small random time of 1 second in order to not overload the target pool in case of recovering from a network outtake. 
- lolMiner API now has new page /gui, which allows you to watch your rig mining in a web browser. Navigate to `http://<ip of your rig>:<apiport>/gui` in your brower doing so. 
- Added experimental (at the moment a bit slow) Ethash kernels for new AMD BC-250 APUs
- In dual mining the algorithm that mined a share will now be shown in command line output
- --ton-mode 6 stratum mode will now obey the prefix send to it on the first bytes of the nonce (request from other pools that want to use this scheme)
- Startup time of dual mining on non-LHR cards is now reduced to 30 seconds after DAG build
- Removed --ton-mode 2 from automatic detection (you still can request it explicitly) - ton-pool.com will instead use mode 1 for existing and mode 6 for upcoming new stratum servers. 

_Fixes_
- Fixed multiple stratum bugs - mostly crash fixes when running web socket based connections
- Windows: clicking into the miner Window will no longer halt the miner completely

### lolMiner 1.44
  
_Features_
- Added experimental Ethash + Ton dual mining kernels for Nvidia Pascal generation GPUs.
- Setting the parameter --maxdualimpact to 0 will now completely disable dual mining on this card. 
- Setting the parameter **--dualdevices** can now be used to make GPUs mine **Ton only in Eth+Ton dual mode**. In combination with **--maxdualimpact** this means one can choose for every card which algorithm to mine. (See example below)
- Automatic tuning for dual mining will now always make sure the parameter is adjusted so the GPUs start on both algorithms if --maxdualimpact is not set. Manually setting --maxdualimpact will disable automatic parameter stretching.
- Windows: Adjusted LHR parameters a bit for more stable operation.
- icemining.ca Ton stratum now can use the --pass or --dualpass parameter to apply pool settings.

_Fixes_
- Windows: fixed a bug that caused abnormal high stale rates on Ethash and Ethash / Ton dual mining on Nvidia cards.
- Windows: fixed a bug that made the miner crash when a https connection tried to re-connect (mostly Ton).
- Linux: fixed a bug that might cause a SIGSEV or SIGPIPE crash on some Linux platforms when reconnecting.
- Fixed a bug that caused the miner to enter re-connect routine when one endpoint of a Ton - pool did not work, although other endpoints did connect well (That in combination with the previous one was root cause for most Ton errors in Windows we recently had).
- Fixed a bug with icemining.ca Ton stratum not sending correct job id when dual mining on AMD cards.
- Fixed a bug with json style configuration not working with dual mining in 1.43 release version.
- Temporarily disabled the ZIL cache function on AMD GPUs, because it sometimes did not swap clearly. We will bring this back as soon as possible.

Example for --dualdevices and --maxdualimpact
Consider a 6 card rig with --dualdevices 4,5 --maxdualimpact `0,0,*,*,*,*`
This rig will mine: 
- Eth only on GPUs 0 & 1      (ton dual mining disabled by maxdualimpact)
- Eth + Ton on GPUs 2 & 3
- Ton only on GPUs 4 & 5     (eth mining disabled by dualdevices)

  
### lolMiner 1.38
_Changes_
- Added DNS over HTTPS name resolving for establishing your pool connection. This has advantages when your normal DNS resolving might be blocked or modified by a firewall. You can control its behavior with the parameter **--dns-over-https value** with the values 0: turns DNS over HTTPS off; 1: DNS over HTTPS is enabled, fallback to normal DNS resolving is possible (default); 2: enforcing DNS over HTTPS, normal DNS is completely disables  (1)
- Updated internal libraries for TLS connection handling
- Moved more fee pools to use TLS connection. When mining Ethash, Etchash (both +ZIL), Ergo and Beam the fee connection is now always encrypted (TLS 1.2) and mining data packages can not be identified as such.  
- Changed LHR kernel defaults for RTX 3060 and RTX 3070, because the default ones had an issue with defect shares at high oc.  

(1) A big kudos to Flexpool for helping out with this
 
  ### lolMiner 1.37
  
  _Feature Changes_

- Improved Ethash performance on Turing based graphic cards (GTX 16 series, RTX 20 series, lower tier CMP cards) by about 0.4 to 0.7%.
- Improvement of Ethash performance (up to 1%) and reduction of stale share rate for Maxwell and Pascal (GTX 10) based GPUs.
- Changes LHR tuning algorithm to minimize the number of locks & time for finding a stable value: The tuning might be improved by the miner later once stable for long enough time.
- Improved LHR performance for 3060 V1 (GA106-300-A1) on older drivers (460.39 and earlier)
- Added Ergo kernels for RX 6700XT and RX 6600 (XT) on newer AMD drivers.
- Ethereum stratum code will now print the pool difficulty in better human readable number
- The miner will now print the ip of the connected pool - to be able to detect e.g. faulty DNS entries
- Added parameters --dualtls and --dualworker to toggle TLS and the worker name for the dual connection. To be used as with the parameters for the standard connection. 
- **--statsformat** can now distinguish between the number of LHR locks "lhrlks" and the current --lhrtune parameter "lhrparam" 
- Added a parameter **--vstats <number>** to modify the terminal width in number of characters to overwrite the automatic detection, which sometimes does not work with some terminal emulators like putty.
- Added a parameter **--hstats <optional number>**. Given this parameter will switch the statistics to a way such that the statistics write a horizontal line per GPU instead of the default vertical (see screenshot below). When the automatic read terminal width is reached, the remaining entries will be printed to a 2nd set of lines. The vertical statistics can be combined with the usual --statsformat patterns to customize the displayed values per card. The optional number overwrites the the automatic screen width detection. To fit all values of **--statsformat extended** into one line we need **--hstats 150** or higher (recommended setting this value manually when accessing the rig via terminal emulator).


_Fixes_
- Fixed 3060 V1 (GA106-300-A1) internal parameters for drivers 460.39 and below, stabilizing the hash rate (they pretty much did not work stably unlocked in 1.36)
- Fixed a bug causing a wavy hash-rate report in some FHR rigs
- Fixed a bug causing **--mode a** kernels to be defect for Ampere and Turing GPUs in 1.36(a) releases
- Fixed a bug causing a segmentation fault when trying to mine EXCC.


### lolMiner 1.36

_Feature updates_
- Improved Ethash & Etchash performance on all Nvidia Turing & Ampere GPUs by **0.3 to 0.7%** depending on card & system.
- Decreased rate of stales on Nvidia Turing & Ampere GPUs.
- Modified LHR auto tuning to use finer steps (0.2 instead of 1). Also when the miner is more then 2 hours stable on its current settings and a lock appears, the card will unlock again, but the tuning will not be reduced. 
- New parameter: **--lhrwait n** will set the miner to wait n seconds, until the LHR detection and calibration gets active. Allows to wait for systems with delayed memory overclock settings.

_Fixes_
- Fixed a potential crash between switching between cached Eth and Zil dag on Nvidia cards
- Fixed a bug: Worker name got lost on ezil.me mining pool (since 1.34)  
- Fixed a bug causing rare defect shares on LHR cards
- 1.36a: Fixed a bug causing no LHR unlock to normal speed after epoch change
- 1.36a: Reverted some LHR kernels to a specification more similar to what was in 1.35. These are default in Windows and on RTX 3080 on Linux, other cards can request this kernels by using --lhrtune wauto or wTuneNumber in case the default is unstable.

### lolMiner 1.35

_Feature changes_

- Ergo: Adjusted all codes mining Autolykos v2 to be ready for the epoch 1 and higher, starting Sunday Nov 7th ~8 am UTC. To continue mining Ergo, please update to this version. (1)
- Ergo: Added ability for all AMD cards to pre-build the next Ergo data set while mining. This is at a cost of slightly slower mining directly after a height change, but generally improves poolside performance. In case you find it unstable the pre-building can be deactivated by using parameter --ergo-prebuild -1 / 0 / 1. Here -1 stands for the cards default, 0 is off, 1 is on. Default is on for all AMD GPUs except GCN1 and Vega generations - those were more stable with the option turned off. The value can be set per card by using a comma separated list of values.
- Ergo: Improved performance of AMD Hawaii generation of chips by about 2%.
- Ethash: Added error correcting tables to check the DAG integrity up to epoch 499 (Early June 2022)
- Ethash: Added option to use the version 1.33 semi-unlocker style - this was more performant for some GDDR6X cards. Use --lhrtune xauto to activate the 1.33 solver style auto tuning and use --lhrtune x to set a predetermined tune value. The 1.33 style solver can be mixed with 1.34+ style solvers by using a comma separated list of values.

_Bug fixes_
- Ethash: Fixed a bug some crashed Nvidia cards did not trigger the watchdog
- Ethash: Fixed a bug causing the worker name not to be correctly passed to the pool in some cases in 1.34(a)


(1) The new Ergo epochs will increase the size of the data set used for mining by 5% every ~75 days. Some cards might need a bit more core clock to achieve the used performance. Also 2G cards in zombie mode will see a significant reduction in speed, because the data set is more then 2150 MBytes in size now. 


### lolMiner 1.34a

_Fixes_
- Added further epochs to the dag correction detection / table. This can resolve issues with defect shares that appeared in 1.34 or earlier with start of epoch 450.
- Slightly changes internal LHR parameters of 3070 ti & 3080 - we hope to improve stability by this plus a small speedup.

Note: this is a Linux only release and also of rather temporary character. The added epochs will minimum last until the 1.35 release. After that an update should be made.

### lolMiner 1.34

**Rework of LHR semi-unlocker (again)**
- Improved performance of RTX 3060 and RTX 3060 Ti by up to 2%, generally allowing a bit less core clock
- Auto tuning will now be quicker to reasonable hashrates
- Improved stability on found parameters
- Found parameters that are hard coded with **--lhrtune** are now applied within 30 seconds after dag build
- **--lhrtune** now understands the parameter "off" to disable any kind of LHR handling - this is useful for cards that sometimes trigger the lhr detection although they are non-LHR.
- Improved compatibility with many current drivers. Still on Linux we recommend 470.74 and on Windows 472.12 for LHR v2 cards. The 460 series drivers might perform up to 0.5% worse. For 3060 LHR V1 use either 460.39 or earlier driver (Linux) or the full unlock with 470.05 Beta in Windows. 

_Feature updates_
- The parameter **--workmulti** now has effect on Nvidia GPUs on Ethash. Default value is 192, lower values will improve stale count, higher values will reduce CPU load (and can be a tiny bit quicker, although only very tiny).
- Added support of RTX A6000 / RTX A5000 /  RTX A4000 (and future RTX A2000) Nvidia workstation GPUs
- Reduced RAM usage of Nvidia Ethash solver (some 10+ card rigs got issues with 1.33 when they only had 4G of memory)
- **--statsformat** now understands the string "lhrinfo" to print the --lhrtune parameter and the lock count in custom set up statistics. 

_Fixes_
- Fixed a bug with **--tstop** or a lost stratum connection triggering a LHR GPU to lock
- Fixed a bug that RTX 3070Ti only triggered the lock detector on rather low memory clock. 
- Fixed a bug with invalid shares in Pitcairn Ergo Zombie mode
- Improved stability of Ethash stratum and statistics module - fixed minor issues that might rarely cause a miner crash in them.

###  lolMiner 1.33

**Core Feature: Complete rework of LHR semi-unlock feature**
- Better performance of LHR semi-unlock, about 70%+ on GDDR6x cards (3070 Ti & 3080 (Ti) ), about 71-72%+ on GDDR6 (3060 (Ti) & 3070), 81%+ on 3060 LHR V1 with the right drivers (earlier then 460.39). Recommended driver for LHR v2: 470.74 (Linux), 472.12 (Windows)
**Important hint:** We saw some calibration bugs with 460.93 driver (Linux). **Please do not use it!**
- Less performance difference between low and high core clock then earlier versions
- Cards are automatically detected if they are LHR - **no more --mode switch required** 
- In the beginning the miner will calibrate to your exact core & memory clocks. The total process takes 3-4 minutes total, one with rather low speed and the remaining time with speed closer to the final value. **Try not to change any overclock after or during calibration**, else the performance might be lower then expected!
- **--lhrtune** has now default value of **auto** for an automatic tuning. Results of automatic tuning will be displayed in stats after calibration is completed. Note: **re-tuning of values used in 1.32a is required!**

_Other feature changes_
- Default --shortstats interval lowered to 15 seconds, default --longstats interval lowered to 60 seconds
- More stable displayed hashrate on Nvidia cards when mining Eth
- Changes in Api: On supported algorithms the miner now exposes the number of stale shares in API (stales and defect shares are no longer collapsed into one value)

_Fixes:_
- Fixed a bug with processing old style --dualmode etc dualmine settings
- Fixed some minor bugs of the API
- Fixed a bug causing a non-realistic high hash rate to be displayed on LHR cards when overclocked after start

### lolMiner 1.32a
- **Beta Feature:** Added RTX 3000 series semi-unlock for LHR v2 cards giving up to 30% more performance then in locked state. Use --mode LHR2 to call it (and --mode LHR1 for 3060 LHR1 cards). Also added a low power LHR mode for V2 cards (--mode LHRLP). See below for more details. **Recommended drivers** for LHR2 and LHRLP: **470.63.01 or 465.31** - others could be more unstable. Most tests were done in Linux.  Use **--lhrtune** to improve either performance or stability. Read the guide for configuring here:  https://github.com/Lolliedieb/lolMiner-releases/wiki/Nvidia-Mode-Switch-&-LHR-Semi-Unlock  (2)
- Improved performance of RTX 3060 LHR v1 semi-unlock by 2-3% depending on configuration - at same low consumption!
- Added detection of the "fan glitch" for RTX 3000 LHR cards. When the glitch is detected, the GPUs will leave the special LHR modes automatically.
- Significantly improved Ergo performance on GCN Gen 1 GPUs (e.g. HD 7970, R9 280, R7 370)
- Added Ergo kernels for Pitcairn GPUs.
- New **configuration scheme** for Et(c)hash + Zil dual mining with dual stratum! See documentation here: https://github.com/Lolliedieb/lolMiner-releases/wiki/Dual-Mining-from-1.32. When using json configuration style use "DPOOLS" with same format as "POOLS" currently.
- When a pool requests a re-connection, the miner will now do so immediately instead of waiting 1 second and no longer say the connection got "lost". 
- Added support for extra nonce subscription on Ergo stratum - this will cause less reconnects on Nicehash

_Fixes_
- Fixed an issue causing "invalid" shares on Ethash when the pool makes intensive use of variable difficulty (e.g. HiveOn, Nicehash...) (1)
- Fixed an issue that might cause the epoch to update too late when doing Eth + Zil dual stratum
- Fixed an issue causing too much stale or very late shares in Ergo
- Fixed partially defect .bat example files
- Updated complete network stack to newer libraries - for more stability.
- A lot of internal re-structuring and fixes.
- 1.32a: Fixed --mode LHR1 not starting in unlocked state on many systems.
- 1.32a: Fixed 3060 LHR V1 not starting in semi-unlock when the right drivers are detected.

(1) Thanks to my Spanish mining community for letting me know and the help to track down this issue. 
(2) Feel free to discuss good tuning values in the discussion section of this release page.


### lolMiner 1.31

_Fixes_ (compared to 1.30)
- Fixed a bug with Ethash Nicehash protocol reporting "conversion of data to type 'b' failed" on new jobs.
- Linux: Slightly adjusted parameters for RTX 3060 (LHR V1) semi-unlock to be more resilient over different configurations. 
- Windows: Re-Worked GPU detection mechanism fixing the bug that miner fails to start up on some systems without any error message. 

_Known issues:_
- Pitcairn GPUs (HD 7850, R9 270, R9 270) still need a new kernel for Ergo. This is work in progress. 


### lolMiner 1.3(RG)0
Note: Windows version will follow in a few days. Sorting out driver issues ;)

- Added **Autolykos V2 mining (ERGO)** use --algo AUTOLYKOS2 to select it (a)
- fee: 1.5%
- Cuda solver: Supports Nvidia Maxwell (GTX 900 series) and newer GPUs with at least 3G of VRAM
- OpenCL solver: Supports AMD GCN1 (Radeon HD 7950) and newer (b) with at least 3G of VRAM 
- Linux: Experimental zombie mode for AMD GPUs with 2G of memory (like HD 7870, RX 550, ...) (c)

_Further feature changes_
- Improved performance of RTX 3060 semi-unlocker in Linux
- Reduced power draw of RX 3060 semi-unlocker in Linux

_Fixes:_
- Significantly improved DAG repair process on all Nvidia GPUs. Even at high OC now the DAG should be created successfully withing a short time. 
- Fixed a bug with 3060 semi-unlocker not unlocking after DAG rebuild
- Fixed a bug in Ethash stratum when mining with Nicehash protocol on some pools not sticking 100% close to protocol.
- Some minor fixes

_Notes:_
(a) General tuning tip: The dataset generation of Ergo is more core heavy then e.g. for Ethash. Please allow more core clock and accordingly voltage! The mining phase of Autolykos V2 instead is not very power hungry. So the average consumption can still expected to be rather low.  
(b) Optimization target were AMD GCN 3 cards with 4G of memory like RX 470, 560, ...
(c) In case the miner does not start on older cards, try to increase --keepfree slightly. 
Personal note: I am aware many would like to mine Ergo+Zil ... this will be possible in future versions, but before I am changing some things how ZIL mining works internally - to make it more flexible to be added to other x + Zil configs :) 

### lolMiner 1.29
*This is a Linux only release*

Added the **Nvidia 3060 "Unlocker" for Linux**. This new mode mode allows to mine at a speed about 3/4 of the maximum speed of this cards. Differences to popular Windows solution:

 - Works with Linux
 - Does not fully unlock card, but partially (~3/4 of max performance, +40-45% over locked card)
 - Allows using risers
 - Allows multiple GPUs in one system
 - Needs Nvidia Linux driver between **455.45.01** and **460.39**, **460.39** is the recommended. Other driver versions will run at locked speed. 

Read the wiki page about more information and how to install this drivers on your favorite mining OS: 
https://github.com/Lolliedieb/lolMiner-releases/wiki/3060-Booster

### lolMiner 1.28a

- Significantly improved / speed up DAG repair function. The miner now should produce a valid DAG also at high overclock.
- Emergency temperature stop (--tmode, --tstart, --stop) now also working for Nvidia GPUs using CUDA.

_Fixes_

- Zombie mode GPUs no longer crash during DAG verify.
- When one Nvidia GPU stops because of a recoverable error (e.g. not enough memory for DAG or temperature limit reached), this will no longer crash all other Nvidia GPUs.
- The parameter --disable-dag-verify was not working for OpenCL fired cards. Not it does.
- Fixed overzealous reconnection on Ethash connections when not receiving new work within 30 seconds (now limit is 150 seconds). This caused problems, especially on ETC+ZIL.
- Fixed 3G Nvidia card not starting on ETC mining


### lolMiner 1.27

- Added verify routine for Ethash dag epochs 400 to 450. In case the miner will detect defect entries, the CPU will try to fix this. Mining will be paused until the repair is completed. Use --disable-dag-verify to disable the verify & repair mechanism routine.
- Re-worked default Ethash kernels for Pascal GPUs - improved their performance
- Added Ethash kernels for Fermi and Kepler GPUs. Most of them will only work for small epoch Eth forks.
- Nvidia cards on Ethash now pause when the stratum reports no current work (e.g. when connection was lost).
- Added a split DAG mode for Nvidia GPUs in case that the memory allocation fails on the primary kernels. This will be a bit slower, but improve compatibility, especially for 5G GPUs. Use --mode s to force it.
- Added parameter --cclk to fix the core clock of Nvidia Turing and newer GPUs without using external tools. Use a comma separated list to give different values to cards, use * to skip over cards. Needs super user or administrator privileges to work. See a detailed description here: https://github.com/Lolliedieb/lolMiner-releases/wiki/Fix-Clock-Nvidia-for-Cuda-by-lolMiner-(English)
- Added new dualmode zilEx. This works like --dualmode zil but with the ability to use --dualdevices to exclude GPUs from switching to ZIL. They will continue on the secondary connection and do not switch.
- Added new dualmode eth. This will allow to point different GPUs to different pools.
- Added parameter --statsformat to use custom format for the bigger statistic box. The expected values are either compact or default or extended or a comma separated list of values. Use --help-format to get a list with accepted entries. The list is also documented at https://github.com/Lolliedieb/lolMiner-releases/wiki/Stats-Format-(English)
- Added reading of current core and memory clocks for AMD and Nvidia GPUs

_Fixes_

Fixed a stratum error, that caused the "all shares stale" bug when too many reconnect attempts in a row did fail
Fixed a crash on Nvidia GPUs when mixing ethproxy and Nicehash stratum modes in dualmodes.
Fixed zombie tune values not applied when using json format for configuring
Fixed displayed names of RX 6000 generation of cards and RTX 3060 in 460.x drivers.

_Deprecation notice_

This will be the last release that allows to use the Zombie-Mode in Windows. This is because the current implementation will start throwing invalid shares at some point and also going too slow to be worth using it any more.
Furthermore Cuckaroo-29 with 48 cycle length - originally planned for Italocoin - got removed because of the lack of use.

### lolMiner 1.26

- Slightly improved performance of Ethash on Pascal / Turing & Ampere GPUs (about +0.1 - 0.2 mh per card)
- Further reduced internal latency in Ethash Cuda back end (less stale shares & CPU load)
- Added experimental Grin-C32 kernel for Radeon 6700

_Fixes_
- Fixed a bug in Cuda back-end to crash with a segfault on Epoch change (introduced in 1.25)
- Fixed a bug that Nvidia-GPUs did not start when Cuda Toolkit was not installed (It reported "No OpenCL devices found ..." - which was complete nonsense)
- Fixed some (rare) potential faults in Beam stratum
- Windows: Fixed message about Light Cache build time was missing (introduced in 1.25)


### lolMiner 1.25 goes CUDA!
Added a real Cuda back-end for better Nvidia GPU support on Ethash. Features:
- Supports Maxwell to Ampere GPU generations.
- Two different mining kernels. Use --mode a (faster) --mode b (better energy efficiency) to select between the two. The selection can be done per card via a comma separated list. In mixed system select 'a' for skipping over the AMD cards. 
- Both kernel modes need less energy and perform better then in 1.24a
- Reduced internal latency for less stale shares
- Reduced CPU load when mining with Nvidia cards
- lolMiner works now without OpenCL driver installed
- In case of mixed rigs AMD GPUs will use OpenCL while Nvidia cards use Cuda
- ZIL cache feature fully supported (and stable)
- Temperature stop & Zombie mode is currently not supported

_Further Changes (over 1.24a)_
- Added Ethash, Beam Hash III, Grin Cuckatoo 32 and Cortex kernels for RX 6700
- The Ethash stratum interface will now try to run up to three attempts of reconnecting before switching the stratum mode

_Bug fixes_
- Fixed "Warning: index out of bounds" error when switching from ETHPROXY to ETHV1 stratum mode. This might solve problems with some pools on connection loss. 

_Recommendations for Cuda backend_
- Recommendation: When using lolMiner on Nvidia cards only use "--watchdog exit" mode and run the miner in a script that will automatically restart it on closing. 
- For ideal efficiency fix the core clock, do not use the offset functionality. Recommended values for selected GPUs:

| GPU        | Range       | 
| ------------- |:-------------:| 
| 2070 | 1000 - 1050 |
| 2080 | 1110 - 1160 |
| 3060 (1) | 1070 - 1120 |
| 3060ti | 1300 - 1350 |
| 3070 | 750 - 800 |
| 3080 | 1010 - 1060 |

(1) Using Windows and Nvidia Driver 470.05 Beta

### lolMiner 1.24a
lolMiner 1.22 - 1.24 are **Linux only** releases that targets improvements of the performance of the zombie mode in the Linux specific code. Therefore the yesterday released version **1.21 will remain the recent release for Windows**. Miners that do not have a card using the zombie mode can safely ignore this update - it will behave identical to 1.21.
- Added (tunable) zombie mode kernels for R9 290(x) and  R9 295 GPUs - on a popular request.

_Bug Fixes_
- Fixed a bug, that often caused the amdgpu driver to report a VM_CONTEXT1_PROTECTION_FAULT_STATUS on startup
- Fixed defect shares and wrong reported has hrate when started with fixed --zombie-tune parameters directly
- Fixed a bug with Baffin (RX 450,460, 550, 560) and Tonga (R9 380(X) ) GPUs showing too high hashrate and producing invalids in 1.23 zombie mode.
- Fixed a bug with ETC mining not starting up when more then two 4G GPUs  in 1.23.

_Personal release notes_
I received quite some requests with problems about Nvidia cards and also if I can add in zombie mode kernels for 4G Nvidias and RX 5500. I need to say I tried, but there are some hurdles that prevented it. I will do better Nvidia codes in the future, but preparing it takes time. 
That said the Navi cards somehow to not like to zombie tuning at all, that is why they only feature the standard zombie mode. Currently I also can not recommend mixing them into rigs where RX 4xx and 5xx cards run in zombie mode, because that seems to cause stuck systems from time to time.  Mixing with 8G cards and do normal mining seems not to be an issue though. 


### lolMiner 1.23
lolMiner 1.22 & 1.23 are **Linux only** releases that targets improvements of the performance of the zombie mode in the Linux specific code. Therefore the yesterday released version **1.21 will remain the recent release for Windows**. Miners that do not have a card using the zombie mode can safely ignore this update - it will behave identical to 1.21.

### lolMiner 1.22
lolMiner 1.22 is a **Linux only** release that targets improvements of the performance of the zombie mode in the Linux specific code. Therefore the yesterday released version **1.21 will remain the recent release for Windows**. Miners that do not have a card using the zombie mode can safely ignore this update - it will behave identical to 1.21.

- Significantly improved the performance of zombie mode on RX 400 and RX 500 GPUs in Linux, especially for low zombie tune values between 0 and 4 and rather high epochs. Performance increases by 7-11% on epoch 393 (--4g-alloc-size 4080 on a RX 580. 4G) and 15-20% on epoch 400. Re-tuning using the auto-tune is recommended. Also this version might draw a bit more power, but with approximately same total efficiency.

### lolMiner 1.21
- slightly improved the performance of Linux zombie mode on Polaris GPUs on medium tune stages (needs re-tuning from previous settings)
- increased range of accepted zombie tune parameter for GPUs with high interconnect bandwidth
- slightly decreased GPU load of Polaris GPUs during DAG build
- Added more control about handling cards that are detected to be non-working any more. Use parameter **--watchdog off/exit/script** to turn off any action, exit the miner with a specific exit code or to run an external script. See detail description on the 1.21 release page
- Nvidia cards that experienced a OpenCL driver error (e.g. "CL_OUT_OF_RESOURCES" will now also trigger the watchdog with the configured effect.
- The **--ethstratum** parameter can now take two options separated by a ',' to give different options in case the dual or split mining mode is used.
- The dns resolving and the connection attempt can now timeout (after 10 seconds each) and will re-try to connect afterwards. This fixes an issue when a pool went offline and the following connection attempt takes indefinitely much time. Each timeout event contributes to the counter that will trigger switching to fail-over pools.
- New option **--apihost** (default 0.0.0.0) which controls to which host address the api binds. Use 127.0.0.1 to restrict api access to only your computer, 0.0.0.0 is equivalent to everyone can access when rig is reachable on the used apiport. IPV6 ip addresses should be supported, but is untested. 


_Fixes_
- Fixed a issue that might cause the rig to drop to 0 hash rate on epoch changes - including changes with activated ZIL caching
- Fixed the pool hash rate reporting not working correctly in dual & split stratum modes
- Fixed the dual stratum connection not picking up the correct worker name when --worker is used
- Fixed miner not loading Ethash / Etchash kernels on Tahiti and Hawaii GPUs when using older then end 2017 drivers. 



_Note on Watchdog use_
There are different reasons why a card might crash and drop to 0 mh/s or g/s or sol/s. Often this happens when the card is slightly too much undervolted, but other problems like heat are possible. Additionally the OpenCL driver of Nvidia cards sometimes crashes with a CL_OUT_OF_RESOURCE error - this is rather a software then a hardware thing and will be fixed soon. 
Anyways: Once a card is crashed some cards - mostly AMD cards - need a system reboot to get the faults card working again. Other cards - mostly Nvidia - just need a closing of the miner program - a few seconds wait time - and then are fine to get going again.
Therefore the crashed card detection now allows three different options to proceed with a crashed card or driver:

**--watchdog off**
This will do nothing except for printing a message. If only a single card did crash and not the whole driver this means the other cards will continue mining.

**--watchdog exit**
This will close the miner with a exit code of 42. This can be picked up by the .sh or .bat script that did start the miner (an example is provided in mine_eth.sh and mine_eth.bat) so the miner will restart after some seconds of pause. This is recommended option for Nvidia cards.

**--watchdog script** 
With this option the miner will call an external script (default path is current working directory and there emergency.sh / .bat), which can be configured with --watchdogscript. The moment the script is called the miner itself will exit. The script needs to take care about rebooting the rig or informing the OS what to do. Since this was the default behavior in previous versions it also is the default. In case the script can not be found, an error will be printed and the miner will continue as with --watchdog off.

### lolMiner 1.20
- Significantly improved **Ethash** mining speed on **R9 390** (+6 mh/s on stock settings compared to 1.19) and **Etchash** speed on **R9 290**. 
- Added new **split & dual mining** options. This allows more freedom or better latency and stability on ETH+ZIL dual mining as well as split mining, i.e. let some cards mine ETH while other (3 and 4G) cards mine ETC. Read instructions on usage here: 
https://github.com/Lolliedieb/lolMiner-releases/blob/master/dual_and_split_mining.md
- The archives for ZIL example files now contain examples how to bypass the ZIL pools. Also an example configuration for ETH / ETC card split is provided.

_Bug Fixes_
- Fixed a bug with 4G cards crash on mining ETC when trying to falsely enter zombie-tune. 
- Fixed R9 380 cards not start mining Beam
- Fixed "Address already in use" API bug in Linux (that incidentally got introduced in 1.19)

_About the split mining_
There are two new splitting modes. Read here for configuration: 
https://github.com/Lolliedieb/lolMiner-releases/blob/master/dual_and_split_mining.md

a) For ETH+ZIL or ETC+ZIL:  
Usually when mining ZIL you need to mine ETH on the same pool or you need to rely on a pool proxy forwarding mechanism implemented by the pool. The first case restricts restricts your mining to a single pool while the latter might have the disadvantage of a worse ETH mining latency or pool forwarding instabilities. lolMiner 1.20 and up allow to bypass the situation by adding a second stratum connection that will pick up your ETH (or ETC) shares and bring them directly to the pool you like, while the ZIL shares will be send during the ZIL shard epochs to the ZIL pool.

b) For mining an other algorithm with your 4G cards:
Usually miners allow using only one algorithm at a time. With lolMiner 1.20 the miner starts supporting to create two connections to your favorite pools and mine two algorithms within the same miner instance. Concretely this mode was build to mine ETCHASH on some GPUS while others stay on ETH.

![grafik](https://user-images.githubusercontent.com/40234439/105478542-98540580-5ca3-11eb-9347-76aa7e85b78a.png)


### lolMiner 1.19
- Added automatic tuning mode for --zombie-tune. This is **default on**, so just run the miner with --4g-alloc-size set only to run the zombie mode automatic tuning. At the end it will report the configuration in case you want to use the configuration again. 
You can also exclude cards from tuning or set their value manually, e.g. --zombie-tune 2,auto,0,auto will run the automatic tuning on the 2nd and 4th GPU while using fixed number 2 for first card and 0 for the 3rd one.
The tuning will need about 30 seconds per card in the rig to show first results. The next two phases take about 1 minute per card and followed by a approximately 1.5 minutes fine tune phase. 

- Ethash stratum connection will now reconnect after three pool rejected shares in a row that did pass own CPU verify before. This solves issues with unstable proxy forwarding e.g. in some ZIL pools. Also helps to get quicker to a failover pool if configured.

_Fixed bugs_
- Miner did not start up when "DEVICES" was configured in as a vector in json file, e.g. in some ETHOS configurations. #110 


### lolMiner 1.18a
- Improved linux zombie mode power draw & speed Polaris GPUs (R9 380, RX Fury, RX 4x0 and RX 5x0). Depending on configuration, the zombie mode now uses 0.5 to 1W less energy and is 0.2 to 0.4 mh/s faster.
- Added --zombie-tune <number> parameter for Polaris GPUs. This will increase the performance of zombie mode (further up on the general improvement) by an other 5-15%, depending on parameter and epoch (later epochs profit more). Default value is 0 (off), for most cards the value of 2 is optimal. If you see cards getting slower then before, set to 0 or 1. Note: you either can give one value for the whole rig or provide a comma separated list for each card individually. Cards not running zombie mode ignore the parameter.
- The parameter --4g-alloc-size can now also be set for each card individually
- Slight rework of Beam Hash III back end. Improves poolside hash rate by approx 0.2 to 0.3% - displayed hashrate and power consume kept equal. 
- Added a 4G_Ethash_Linux_Readme.txt file to the Linux release, giving guidance how to configure for ideal zombie mode performance.
See online version: https://github.com/Lolliedieb/lolMiner-releases/blob/master/4G_Ethash_Linux_Readme.md

_Bug fixes_
- Fixed: segmentation fault when the dns resolve of a pool fails #109 
- Fixed: miner does not restart after connection loss. #108 
- Applied potential fix for "address or port already in use" bug.

_Compatibility note:_
The new zombie-tune parameter has only been tested with amdgpu-pro 20.30 and 20.40. Other drivers might cause issues. 
Also make sure your mining rig is configured to use PCIe-gen 2 connection to your GPUs.

_Example effect of --zombie-tune parameter on the hash rate in Zombie Mode_
Note: it may be needed to tune each card individually. Tune value of 2 works for most cards, but some do not like the mode, especially when on PCIe-gen1 riser. 
![ztune](https://user-images.githubusercontent.com/40234439/103769382-6d6f7d80-5024-11eb-9022-c63a40651672.png)


### lolMiner 1.17
- Significantly reduced Ethash power draw on Navi GPUs, Slightly improved performance of 6800 (XT) / 6900
- Added Cuckoo-29, Cuckaroo-30 CTX, Cuckatoo-31 (MWC) and Cuckatoo-32 (Grin) for RX 6800 family of GPUs
- Reduced number of stale shares on Cortex algorithm. This will result in a minimally lower displayed hash rate, but higher pool side hash.
- Added a basic temperature protection mechanism. See notes below for usage.
- Added parameter **--singlethread** to work with Ethash and Equihash algorithm. This will disable the 2nd mining thread and slightly reduce performance of the involved cards. Use this option to reduce stumbles when a card does graphic output in parallel. Use **--singlethread** (equivalent to **--singlethread -1**) to enable single thread mode for all GPUs, use **--singlethread <gpu id>** to set the mode for one single card.
- Added reading of junction temperature on AMD GPUs.
- The API is now bound to the local host, causing less issues with firewalls.
- Windows: use **--computemode** to automatically enable the compute mode on all detected AMD GPUs. Requires higher privileges and a driver restart, see example files.
- lolMiner.exe Windows executable is now digitally signed.

_Fixed bugs:_
- Ethash Ethproxy stratum mode some times loosing worker name.
- Beam Hash III not starting up in Linux on RX 5000 & RX 6000 series card on amdgpu-pro 20.45 driver.
- Ethash & Beam not starting up on Radeon R9 380 
- Ethash not starting up on some 6G Nvidia cards
- Ethash mining frequently trying to start up a card if there was an error during mining. 
- "DEVICES" parameter not working when configuring the miner from json file.
 
_Known issues:_
- ETC mining is currently not working for Nvidia GTX cards with 3G of memory. 
- On some Linux kernels there is a memory leak in the GPU driver component that effects lolMiner quite hard when mining with Navi cards. Keep system updated. (Note that this bug also affected earlier versions of lolMiner - so if it worked fine in last version it can be expected to do so further.)

_Basic temperature management / overheating protection. _
Use **--tstop <number>** to stop any mining operation on a GPU at the given temperature. Use **--tstart <number>** to allow a restart of the card below a lower temperature. Further you can use **--tmode edge/junction/memory** to apply the scheme to edge (chip), junction (hotspot) or memory temperature. If a GPU does not have the required sensors the chip temperature will be used as a back up - if no sensors are available at all the parameters will be ignored. 

Note that at the moment the miner has no fan control module and also no throttling to keep a target temperature. This may be included in a future version. Thus you should put the limit high enough so the operation system or the driver has a chance to ramp up the fan speed itself. Currently tstop is supposed to be a overheat protection to prevent hardware damage in extreme cases, e.g. broken fans.

### lolMiner 1.16a
- Fixed performance regression on Nvidia cards
- Added support of Ethash and Beam Hash III for RX 6000 generation of GPUs
- All supported algorithms now show the share difficulty and have best share statistics. 
- New feature: use **--rebuild-defect _n_** to trigger a rebuild of DAG if a GPU produced _n_ defect shares on the current one. Default is 3, use 0 to deactivate this feature. 
- New feature: Use **--workmulti _n_** to modify the amount of Ethash work a GPU does per batch. Higher values will cause less CPU load but more stale shares, lower values will give less stale shares but higher CPU load. Performance may vary for different values. Default is 128.  
- New feature: if Ethash pool disconnects within 2 seconds from connection attempt (immediate reconnect), then the other stratum mode is tested to login.
- New feature: AMD Vega and newer cards now display memory temperature in statistics & api (only visible if there is at least one such GPU in the rig). 
- Default ethstratum changed from ETHV1 to ETHPROXY for better pool compatibility. 
- Stratum pool addresses now understand "stratum+tcp://", "stratum+ssl://" and "ssl://" prefixes (turning on or of ssl / tls automatically) for better compatibility with existing configurations.   
- Slightly reduced CPU load when mining Ethash
- New coloring scheme with more friendly colors. For terminals that do not have rgb colors (e.g. shellinabox) use **--basecolor** to restrict to a simpler set. Use **--nocolor** to deactivate coloring completely. 
- Fixed bug: Cards may crash when switching from ZIL cache back to normal mining.
- Fixed bug: Wavy hashrate - especially for rigs with many AMD Navi GPUs.
- Fixed bug: (Linux:) Watchdog not called when a GPU is stuck & extremely high CPU load on crashed GPU. (1)
- Fixed bug: Hashrate reporting not working on some pools (e.g. sparkpool)
- Fixed bug: Miner can crash after trying to reconnect to same pool over 5 minutes. 
- Fixed bug: Miner crashes when mixing TLS and non-TLS pools for fail-over. 

(1) Note on watchdog use: When the watchdog script is called the miner will stop working on the other cards. If this is not wished use --disablewatchdog. Please make sure the script can be executed with the current user rights / does password-less operations. 

### lolMiner 1.15
- Fixed bug: Miner causing invalid shares on 4G cards on some systems (mostly Linux)
- Fixed bug: Miner hangs up when changing epoch when using the ZIL cache feature
- Fixed bug: Miner sometimes produces invalid shares when a new job with different epoch arrives while the miner is currently creating the DAG file for an earlier job.
- Fixed bug: Miner not calling the default emergency scripts when a GPU was hung up (it only worked with custom scripts)
- Improved Ethash efficiency on Nvidia GPUs
- ZIL cache now can be used by cards with less then 8G when enough memory is available (e.g. 6G cards or when mining e.g. ETP + ZIL)
- General stability improvements (resolved many potential miner hangs up causes)
- Changed color scheme in Windows for Ethash mining (new jobs are now white, accepted shares green)

### lolMiner 1.14
- Added Ethash Zombie mode for 4G Nvidia GPUs. Use --4g-alloc-size to calibrate the number of MBytes the GPUs are allowed to use. 
- Fixed a segmentation fault on Nvidia & mixed rigs when starting Ethash mining

### lolMiner 1.13
- Ethash: Reduced power draw significantly on  non-zombie mode for Rx Fury & Rx 470 - 590, slight reduction for Vega &  Navi
- Ethash: Slightly improved performance on Vega, Navi and Nvidia GPUs. Significantly improved performance on R9 390. (1)
- Added (Linux) Zombie mode for RX 5300XT & RX 5500 4G cards. Windows users can try it by using "--win4galloc off --4g-alloc-size 4008". (Vary the last number to find out sweet spot)
- Added ETCHash support for Radeon HD 79x0 / R9 280 (X) & RX 5300 3G. On Linux will be good for ETCHash till epoch ~250 (about July 2022) 
- Added caching of last 5 used light caches. This will reduce the switching time for Nicehash & ZIL dual mining significantly. 
- Added support for extranonce subscription on  EthereumStratum/1.0.0 (Nicehash) format - this will stop the miner from frequently reconnecting to Nicehash
- Added detection of pool not accepting worker name in <wallet.workerName> format when using ETHPROXY stratum. Miner will reconnect with worker name copied into --worker in this case. 
- Added experimental workaround for mining epoch 385+ with RX 470 - 590 and Linux kernel 5.6.x: Note this fix will deactivate the ZIL cache ability and force the miner to create DAG a bit slower. Deactivate it with --disableLinux56fix . Other Linux kernel versions and other GPUs are unchanged.
- Fixed bug: "conversion of data to type "b" failed" when using ETHPROXY stratum mode on some pools.
- Fixed potential issue causing GPUs to freeze when a GPU needs to reboot, e.g. epoch change or connection loss.
- Fixed benchmark mode for ETCHash. Use --benchmark ETCHASH --benchepoch 390 to benchmark performance post fork.
- Fixed benchmark mode not starting up when called from json type configuration.

(1)  (its still not perfect, but way better)


### lolMiner 1.12
- Added support for ETCHash (Ethereum Classic dag size reduction planned for end November). Use --algo ETCHASH to activate it. (See note on release page).
- Reworked Ethash codes for late epochs on Windows. See 4G_Windows_Readme.txt for configuring it.
- Slightly improved Ethash efficiency for GCN 3 (R9 Fury, 470 - 590) & Navi cards
- Added experimental support for Ethash on Nvidia GPUs (See note on release page)
- Added new parameter: --4g-alloc-size <MByte> to define the memory allowed for Ethash on 4G cards. Maxing out will give more epochs of mining & better Zombie mode performance, lower values may improve compatibility. Suggested values: Linux: 4076, Windows 4008 - 4024
- Added new parameter: --worker <Name> to set the worker in ETHPROXY stratum mode (improves pool compatibility)
- Overall new Ethash host size back end - hopefully improving stability of mining
- Fixed bug: Zombie mode generates defect shares in Windows
- Fixed bug: Logs were not written when "LOG" : 1 was set in json style config file



### lolMiner 1.0

- lolMiner got a restructure how to configure it and also features a 2nd, more simple config file format.
  Use lolMiner -h to get a list of new supported parameters or visit the new [online manual](https://github.com/Lolliedieb/lolMiner-releases/wiki)
- Added optimizes solvers for Beam Hash III for AMD & Nvidia cards. Use *--coin BEAM* to auto switch from BeamHash II to BeamHash III on fork (approx June 28th, requires 8G card) or select Beam Hash III solver manually with *--algo BEAM-III* (requires 6G card)
- Added performance improved (+ >10%) GRIN-C29M solver for 8G GPUs
- Added Cuckaroo-30 solver to mine Cortex Ai (*--coin CTXC* or *--algo C30CTX*) for all 8G and higher GPUs
- Added support for non-integer difficulty on Grin
- Reactivated support for Beam Hash I including support for personalization strings. 
- AMD Navi does now work on all supported algorithms
- Removed Grin Auto-Switcher (C31 is obsolete now and the switcher would not work on next Grin fork)
- Removed support for MNX (Minex Coin project is dead / abandoned by developers)  
- Added temperature, consumption and fan speed readings in API and long statistics
- Internal bug fixes

### lolMiner 0.9.8
- Improved GRIN-C29M solver, Better performance (+7-12% depending on card) and smaller memory use (fits 6G now)
- Added support for Radeon 5500 (XT) and 5600 (XT) on all Grin algorithms 
- Added BEAM support for Radeon 5500, 5600 and 5700 series (Needing 19.30 and newer driver)
- Fixed driver incompatibilities with some newer driver versions (e.g. Linux 19.50) 
- Renamed GRIN-AD29 to MWC-C29D to mine cuckarood-29
- Added a small penalty to C32 in auto switcher - it seems the solver has not perfect fidelity and the penalty will make it switch a bit later to cover this. Will hopefully be fixed in next version
- Removed 14 cycle fidelity from overview - new C29M solver does not output it properly.

### lolMiner 0.9.6
- Significant improvement on GRIN-C29M performance (+6-7% on 580 and Vega cards, +10% on Navi)
- Significant improvement on GRIN-C31 and GRIN-C32 solver (~ +6% on all AMD cards)
- Added a 16G GRIN-C32 solver (Approx 20% faster on Radeon VII, Vega FE and 570 16G)

### lolMiner 0.9.5
- Added support for Grin CuckarooM-29 (hard fork on Jan 16th) on 8G AMD GPUs, use --coin GRIN-C29M to mine with it.
- Improved C31 performance on 8G cards by ~5% (Windows: relatively to 0.9.3, Linux: relatively to 0.9.4)
- Navi on Windows now runs same kernels as in Linux
- Slightly lowered energy use of C31 / C32 solver
- Added aliases GRIN-C31 and GRIN-C32 for the Cuckatoo solvers (the old names still exist and continue to work)

### lolMiner 0.9.4
- New GRIN-AT31 performance code for Vega (+7%) and Navi (+12%). Requires amdgpu-pro 18.50 or newer or ROCm 2.10 driver
- Experimental support for Cuckatoo-32 (use --coin GRIN-AT32) on 8G AMD cards (see further notes on releases page)
- Windows release postponed due to incompatibilities with the new performance codes. 

### lolMiner 0.9.3
- Extended GRIN-AT31 compatibility to older drivers (18.x +) 
- Improved GRIN-AT31 performance on ROCm (RX 470/480/570/580/Vega/VII)
- Introduced early job cancellation for GRIN-AT31+ (improves hash on pool side, see further release notes on releases page)
- Deeply reworked kernel scheduler
- Fixed GRIN-AT31 kernel bugs (improving stability and fidelity)
- Fixed Bug: Vega FE loading 8G instead of 16G GRIN-AT31 solver in Windows
- Fixed Bug: Watchdog did not call right file in Windows
- Added --disablewatchdog 1 parameter to disable the 0 sol/s  /  0 g/s detection

### lolMiner 0.9.2
- Significant performance improvement of GRIN-AT31 on 8 / 16G cards (+5% on Polaris & Vega, +10 on Navi)
- Experimental support for GRIN-AT31 and Polaris, Vega and VII using AMD ROCm drivers
- Added range checks to GRIN-AT31 code (improves better stability) 
- Added function to call external watchdog scripts in case a GPU fails during mining (see release notes)

### Usage of Watchdog Script
In case the miner detects no action of a GPU for at least a minute it will call the included scripts "reboot.sh" (Linux) or "reboot.bat" (Windows) and display a warning message in red. Afterwards the counters are reset. The scripts can be used to trigger a reboot of the rig or to call any other watchdog actions. The miner itself will take no further action and continue operation on the remaining cards.


### lolMiner 0.9.1
- Added GRIN-AT31 solver for 16G AMD cards (Better performance on Radeon Vega FE, Radeon VII and Sapphire RX 570 16G) 
- Updated GRIN-AT31 solver for 4G AMD cards (Better performance on Fiji based GPUs, Polaris 10 4G)
- Fixed a bug causing too low pool hash on GRIN-AT31
- Added experimental GRIN-AT31 support for AMD Navi (8G), ~~AMD Fiji (4G)~~ and AMD Hawaii (4G / 8G) GPUs

Edit: support for Fiji was broken, A fix can be found here: 
https://github.com/Lolliedieb/lolMiner-preview/releases/tag/0.9.1hotfix

### lolMiner 0.9
- Significant performance improvement for GRIN-AT31 on 8G AMD cards (+22% on Polaris to 30% on Radeon VII)
- Disabled 16G solver for GRIN-AT31 (the 8G is faster at the moment)
- Reduced Grin stale shares
- In command line lolMiner now accepts --pool address:port pattern
- Fixed a bug with the API crashing when accessed by Chrome based browsers
- Fixed a bug in EXCC stratum not passing number of submitted shares to the API


### lolMiner 0.8.7
- Added support for Beam Hash II on older AMD cards (R 9 200 / 300 4 & 8G cards;  R9 280(X), HD 79x0 with 3G). Note that the auto-switcher is only working with at least 4G, for the 3G cards please use --coin BEAM-II manually on fork height.
- Fixed an issue with Genesis Network (GENX) missing in lolMiner 0.8.x

### lolMiner 0.8.6
- Added support the BEAM hard fork on block 321321 (approx Aug15th).
- Fixed a bug with the BEAM stratum back end in case of formatted job descriptions (e.g. new Nicehash platform)

### lolMiner 0.8.4
- Fixed a 0 sol/s issue for Zelcash
- Reduced Zelcash memory usage to 2.9 GBytes
- Fixed a bug with the stratum for 125/4, 144/5, 192/7 and 96/5 in case the pool sends a very low job id.

### lolMiner 0.8.3
- Added 16 GByte solver for Cuckatoo-31 (GRIN). Better performance and less energy use for Radeon VII, Radeon Pro Duo Polaris, Vega Frontier and RX 570 16GByte

### lolMiner 0.8.2
- Added support for ZelHash (EquihashR 125/4/0) for the hard fork (July 2nd)

### lolMiner 0.8.1
- Added support for NiceHash on Grin
- Fixed a bug with some pool software (e.g. grinmint.com)
- Reduced number of stale shares submitted 

### lolMiner 0.8
- Added support for Grin (Cuckatoo-31) for 4G (Slean) and 8G cards. The parameter is "--coin GRIN-AT31"
- Grin cycle finding is completely done on GPU, the miner has almost 0 CPU load (on AMD, Nvidia has some due to OpenCL back end)
- Stratum bug fixes (NiceHash) for 144/5, 192/7 and  96/5
- Fixed AUTO192_7 configuration
- Improved general stability 
- Added a distinct 1G / 3&4G / 6&8G kernel for mining MNX (Windows, Linux had this in 0.7.1)


### lolMiner 0.7
- Added support for Beam (BEAM, modified Equihash 150/5), only tuned for AMD cards
- Added TLS support for stratum. The default is off for all coins except Beam but on for Beam. This adds a new parameter --tls to control TLS on / off (see manual on usage)
- Some bugfixes and reworks in the stratum code. It is more stable now
- Complete rework of the mining back end. Lower CPU load for AMD graphic cards.
- GPU sorting changed. Its now sorted by PCIE bus address. This addresses are also shown at startup and in API.
- Integrated all kernel files to the executable
- Lowered fee of ALL algorithms / coins to 1%
- Added --help parameter (needs formating)
- API update interval is now fixed to 10 seconds
- API now smooths the performance data over approx one minute 

Coin specific changes:
- Removed workbatch parameter for MNX, its obsolete now
- Removed 96/5 Nvidia specific kernel
- Changed Safecoin (SAFE) from Equihash 144/5 to 192/7
- Added Vidulum (VDL), Equihash 192/7
