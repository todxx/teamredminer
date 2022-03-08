# teamredminer v0.9.4.1
This is an optimized miner for AMD GPUs and Xilinx FPGAs created by todxx and kerney666.

**Download is available in the [github releases section](https://github.com/todxx/teamredminer/releases).**

TRM official website: https://www.teamredminer.com

TRM discord server: https://discord.gg/RGykKqB

Below is a list of mining operating systems and management software that have built-in support for teamredminer:
 - [MMPOS](https://mmpos.eu/)
 - [SimpleMining OS](https://simplemining.net/)
 - [Hive OS](https://hiveos.farm/)
 - [Minerstat](https://minerstat.com/)
 - [Awesome Miner](https://www.awesomeminer.com/)
 - [PiMP OS](https://getpimp.org/)
 - [RaveOS](https://raveos.com/)

This miner supports a range of algorithms.  Please see the list below for details.
The miner is configured via command line only, please run with the --help option to print a short help message for how to use the command line options.

## GPU Support

GPUs supported and tested:
- Navi - RX 5700(XT)/5600(XT)/5500(XT) for supported algos in the table below.
- Big Navi - RX 6900XT, RX 6800(XT), RX 6700(XT), RX6600XT - same support as for Navi.
- Vega - RX Vega 64/56, Vega FE, Radeon VII (Vega 2)
- Polaris - RX 580/480/570/470/560/460/550
- Fiji - R9 Fury/Fury X/Nano, MI8 (supported but with very limited testing).
- Tonga/Antigua - R9 285/285X/380/380X, W7100, S7150 (beta support from 0.8.2. Only ethash+kawpow available.)

Supported GPU algorithms and their respective dev fees:

|      GPU Algorithm        |  Fee |
| ------------------------- | ---- |
| Ethash on Polaris GPUs    | 0.75%|
| Ethash on all other GPUs  | 1.0% |
| Kawpow                    | 2.0% |
| Verthash                  | 2.0% |
| Autolykos2                | 2.0% |
| Ton                       | 1.0% |
| Nimiq                     | 2.5% |
| Cryptonight R             | 2.5% |
| Cryptonight v8 upx2       | 2.5% |
| Cryptonight v8 turtle     | 2.5% |
| Cryptonight v8 half       | 2.5% |
| Cryptonight v8 double     | 2.5% |
| Cryptonight v8 rwz        | 2.5% |
| Cryptonight v8            | 2.5% |
| Cryptonight heavy         | 2.5% |
| Cryptonight haven         | 2.5% |
| Cryptonight saber         | 2.5% |
| Cryptonight conceal       | 2.5% |
| Chukwa-512 (Turtlecoin)   | 2.5% |
| Chukwa-1024 (Turtlecoin)  | 2.5% |
| x16r                      | 2.5% |
| x16rv2                    | 2.5% |
| x16s                      | 2.5% |
| x16rt                     | 2.5% |
| MTP                       | 2.5% |
| Cuckatoo31                | 2.5% |
| Cuckarood29               | 2.5% |
| Lyra2rev3                 | 2.5% |
| Lyra2z                    | 3.0% |
| Phi2                      | 3.0% |

Some algorithms are not supported on some GPU architectures and/or drivers.  Below is the compatiblity table:

|                          | Navi | Vega | Polaris | Fiji | Tonga |
| ------------------------ |:----:|:----:|:-------:|:----:|:-----:|
| Ethash                   |  Y   |  Y   |   Y     |   Y  |   Y   |
| Kawpow                   |  Y   |  Y   |   Y     |   Y  |   Y   |
| Verthash                 |  Y   |  Y   |   Y     |   Y  |   N   |
| Autolykos2               |  Y   |  Y   |   Y     |   Y  |   Y   |
| Firopow                  |  Y   |  Y   |   Y     |   Y  |   Y   |
| Ton                      |  Y   |  Y   |   Y     |   Y  |   Y   |
| Nimiq                    |  Y   |  Y   |   Y     |   Y  |   N   |
| Cryptonight R            |  N   |  L   |   L     |   L  |   N   |
| Cryptonight v8 upx2      |  N   |  L   |   L     |   L  |   N   |
| Cryptonight v8 turtle    |  N   |  L   |   L     |   L  |   N   |
| Cryptonight v8 half      |  N   |  L   |   L     |   L  |   N   |
| Cryptonight v8 double    |  N   |  L   |   L     |   L  |   N   |
| Cryptonight v8 rwz       |  N   |  L   |   L     |   L  |   N   |
| Cryptonight v8           |  N   |  L   |   L     |   L  |   N   |
| Cryptonight heavy        |  N   |  L   |   L     |   L  |   N   |
| Cryptonight haven        |  N   |  L   |   L     |   L  |   N   |
| Cryptonight saber        |  N   |  L   |   L     |   L  |   N   |
| Cryptonight conceal      |  N   |  L   |   L     |   L  |   N   |
| Chukwa-512               |  N   |  L   |   L     |   L  |   N   |
| Chukwa-1024              |  N   |  L   |   L     |   L  |   N   |
| x16r                     |  N   |  Y   |   Y     |   Y  |   N   |
| x16rv2                   |  N   |  Y   |   Y     |   Y  |   N   |
| x16s                     |  N   |  Y   |   Y     |   Y  |   N   |
| x16rt                    |  N   |  Y   |   Y     |   Y  |   N   |
| MTP                      |  Y   |  Y   |   Y     |   Y  |   N   |
| Cuckatoo31               |  N   |  Y   |   Y     |   Y  |   N   |
| Cuckarood29              |  N   |  Y   |   Y     |   Y  |   N   |
| Lyra2rev3                |  N   |  L   |   L     |   L  |   N   |
| Lyra2z                   |  N   |  L   |   L     |   L  |   N   |
| Phi2                     |  N   |  L   |   L     |   L  |   N   |

Support legend:
 - Y = Supported
 - N = Not supported
 - L = Limited support: algos are supported on windows and linux with amdgpu-pro drivers, not supported on ROCm drivers.

## FPGA Support

FPGA Devices supported and tested in Linux (Windows is not currently supported):
- Xilinx Varium C1100
- SQRL Forest Kitten 33 - performance limited by product design, see guide for details
- Xilinx/TUL/Osprey U50C/ECU50

Supported FPGA algorithms and their respective dev fees:

|      FPGA Algorithm       |  Fee |
| ------------------------- | ---- |
| Ethash                    | 4.0% |

-----------

The miner reports GPU hash rates every 30 seconds.  These are the full GPU hash rates before dev fee deduction (your pool hashrate will be slightly lower). 

The miner includes a read-only api based on the sgminer-5.5 API.  Both the json and text formats are supported.  For more details, we refer to the sgminer api documentation.
The miner also includes a Claymore miner compatible API with support for a subset of the API.

For reporting bugs and/or for features requests, please open an issue on this project's github [issue tracker](https://github.com/todxx/teamredminer/issues).

For example command lines please see the batch/shell scripts in the miner download packages.
For command line options see the [USAGE.txt](USAGE.txt) file that comes with the miner.

## Release Notes

### v0.9.4.1
#### Changes
- GPU:  Fixed eth+ton issue that could lead to a higher eth shares stale rate. Primarily for large gpus (6800/6900XT) with aggressive tuning.
- GPU:  Internal split of binaries helping some Vegas and Navis with crash issues on ethash from 0.9.2 and forward.
- FPGA: Added initial support for TUL TH53/TH55.

### v0.9.4
#### Changes
- GPU:  Navi/Big Navi rewrite for eth+ton, increased hashrates on both algos and more stable setup.
- GPU:  Navi/Big Navi eth+ton rigs with stale eth issues should be fixed.
- GPU:  Pool outage for dual algo now results in eth mining only instead of pausing. This will reduce crashes.
- GPU:  Fixed a potential deadlock when mining eth+ton. Rigs that have gotten strange "crashes" should upgrade, especially when coupled with a network or pool outage.
- GPU:  Added --dual_tuner_step and --dual_tuner_period to configure the dual tuner accuracy.
- GPU:  Fixed race bug for ethash where gpus could accidentally build a dag for epoch 0 at startup.
- GPU:  RaveOS fix for running the TRM wss proxy for Nimiq and certain TON pools.

### v0.9.3
#### Changes
- GPU:  Added Polaris support for dual ETH+TON (full eth + 600-750 MH/s ton per gpu). All AMD gpus now supported.
- GPU:  Updated DUAL_ETH_MINING.txt with information for all AMD gpus. 
- GPU:  Added support for TON Pool (ton-pool.com). See TON_MINING.txt for details.
- GPU:  Fixed bug that could cause stale shares on gpus disabled for dual mining.

### v0.9.2.1
#### Changes
- GPU:  Fixed a critical bug for Polaris and Vegas on Windows and Linux amdcl2, only reaching 50% poolside hashrate.
- GPU:  Added support for selecting dual algo devices using a "-d x,y,z,..." argument inside the --ton .. -ton_end clause.

### v0.9.2
#### Changes
- GPU:  Added TON algo for single algo mining on all gpu generations (see TON_MINING.txt).
- GPU:  Added dual ETH+TON mining for Navi and Big Navi gpus (see DUAL_ETH_MINING.txt). Vega and Polaris upcoming shortly.
- GPU:  Added dual mining tuner based on scoring weights (see --dual_tuner_weights).
- GPU:  Faster initial ethash tuning on startup.
- FPGA: Added --fpga_max_jtag_mhz for limiting the JTAG communication frequency used.
- FPGA: Fixed DNA for vu35p - now matches Vivado hardware manager and NextJTAG.

### v0.9.1
#### Changes
- FPGA: Updated FPGA_GUIDE.txt with new devices, voltage tuning, and more.
- FPGA: Added U50C/ECU50 FPGA suppport.
- FPGA: Added custom SC firmware for C1100 and U50C.
- FPGA: Added TRM SC firmware programming support, see --fpga_update_fw.
- FPGA: Added voltage control for C1100 and U50C (using new firmware), see --fpga_vcc_int, etc options.
- FPGA: Added support for additional FK33 sensors (hbm voltage, current sensors).
- FPGA: Added support for DNAs in the --fpga_devices option.
- FPGA: Added --fpga_allow_unsafe option for disabling safety limits.
- FPGA: Added timeout for ethash DAG gen on FPGAs.
- GPU:  Added --eth_ignore_abort_fail to disable intensity adjustment due to failed aborts.
- GPU:  Added better handling of dead gpu logging in corner cases that previously didn't mention a specific gpu.

### v0.9.0
#### Changes
- Added initial FPGA ethash support.  See FPGA_GUIDE.txt for details.

### v0.8.7
#### Changes
- General: added offline benchmark mode for (almost) all algos (see --benchmark).
- Network: improved situations with the "Dev pool failed to connect." error message appearing.
           Users in China should preferably run with "--dev_location=cn".
- Network: added experimental support for DNS-over-HTTPS (see --dns_https and --dns_https_sni).

### v0.8.6.3
#### Changes
- Autolykos2: emergency release to support larger pad size from block 614400.  Some GPUs (mainly Vegas) will need higher core clocks to achieve the same performance as previous versions due to larger pads breaking some previous optimizations.  More optimizations to come in future releases.
- Autolykos2: added argument --autolykos_ignore_diff for certain pools that aren't compatible with the ERGO reference miner pool implementation.
- Progpow: fixed wrong --help text for --prog_micro_tune.

### v0.8.6.2
#### Changes
- Firopow/MTP: added a synthetic algo 'mtp_firopow' that will use the correct algo given the system time and shut down the miner at the time of the Firo fork on Oct 26. 
- Ethash/progpow: split the ethash and progpow algos into separate binaries, mainly for some Vegas that ran into stability issues going from 0.8.5 to 0.8.6.
- Autolykos2: added support for Tonga.
- Advanced SSL usage: changed the default SSL behavior to _not_ provide a SNI hostname during handshake. See the updated --help section on the -o argument for how to force a SNI hostname being sent.

### v0.8.6
#### Changes
- Firopow: new algo added for Firo's upcoming fork (see start_firo.sh/bat). Only testnet mining is available before the fork, see start_firo_testnet.sh/bat.
- Firopow/kawpow: rewrote tuning guide (see KAWPOW_FIROPOW_TUNING.txt).
- Firopow/kawpow: slight hashrate improvements, mainly from choosing full gpu tuning by default and adding a micro-tuning mechanism for Polaris gpus (see new argument --prog_micro_tune).
- Autolykos2: added high score support and display of submitted share difficulty.
- General: fixed Radeon VII support on recent win drivers. NOTE: HBCC must be DISABLED for all Vegas.
- General: fixed broken fan control for Navis on some driver versions.
- General: improved Windows compute mode enable with automatic elevation (with --uac) and restart of gpus.
 
### v0.8.5
#### Changes
- General: added Windows clocks/voltage/built-in timings control (beta functionality). See section in --help and CLOCKS_VOLTAGE_CONTROL.txt.
- General: fixed some issues with Windows fan control, mostly for Big Navi gpus.
- General: added mem temp limits (stop/resume), see --mem_temp_limit and --mem_temp_resume.
- Ethash: added support for forcing ethash pool hashrate reports (see --eth_hash_report).
- Ethash: fixed hashrate reports for Crazypool when using failover pools.
- Autolykos2: added extranonce subscription support for e.g. Nicehash.
 
### v0.8.4
#### Changes
- General: Added fix for failure to load GPU kernels on newer drivers, e.g. Big Navi on Adrenalin 21.6.x.
- Emergency patch: fixed Haven mining generating mostly hw errs after the recent hard fork.
 
### v0.8.3
#### Changes
- General: added Autolykos2 algo for ERGO (very good target for Vega 56/64, see the AUTOLYKOS_TUNING.txt guide).
- General: improved and simplified dual ZIL mining for ethash/kawpow/verthash/autolykos2 (see the new DUAL_ZIL_MINING.txt guide).

### v0.8.2.1
#### Changes
- Bugfix: fixed windows issue with intermittently reading zero gpu stats and blasting fans (bug in 0.8.2).
- Verthash: added --verthash_max_uploads=N to control the upload of the verthash table to gpus at startup. Some chipsets get issues running > 4 gpus concurrently. Typical error is that multiple gpus die immediately at startup when running the full rig, but work fine if you only run 3-4 gpus.
- Verthash: fixed support for 550 2GB gpus. 

### v0.8.2

#### Changes
- General: added Verthash algo for Vertcoin.
- General: added Tonga and Antigua support for ethash and kawpow.
- General: extended support to 24 gpus (previously max 16 gpus possible).
- General: better handling of driver issues related to gpu clocks/temps stats.
- General: now showing sensor power in stats output.
- General: fixed device name parsing in ROCm 4.1 and newer win drivers.
- API: added sensor power, jnct temp and mem temp to API output.
- Ethash: added --eth_micro_delay for weaker psus (see help section for details).
- Ethash: fixed watchdog DEAD gpus on small gpus building kawpow DAG.
- Kawpow: now working fully with MiningPoolHub, regardless of bad seedhash values.

### v0.8.1.1
#### Changes
- Patched v0.8.1 with new devices ids for 6700XT support.

### v0.8.1
#### Changes
- General: basic Big Navi support added (ethash, kawpow, mtp, nimiq supported algos).
           See the ETHASH_TUNING_GUIDE.txt for a short section on Big Navis. 
           Driver support missing on Windows for fan control and mem temp.
- Ethash: display gpus now use A-mode by default to prevent failed allocation and low hashrates.
- Stats: handling of negative temperatures under Linux.
- Eth+zil: added new pool strategy 'min_epoch' for dual pool connection switching (see start_zil_eth.bat/.sh example script).

### v0.8.0
#### Notes
Biggest release in a long while with rewritten ethash kernels and new mining modes for all gpu types!

Users are highly(!) recommended to take a few minutes to read the 0.7-to-0.8 [migration guide](https://github.com/todxx/teamredminer/blob/master/doc/ETHASH_FROM_0.7_TO_0.8.txt) and the new [ethash tuning guide](https://github.com/todxx/teamredminer/blob/master/doc/ETHASH_TUNING_GUIDE.txt). Key highlights:

- Polaris: Efficiency and slight hashrate increase. B-mode reintroduced for added hash. B-mode must be enabled with --eth_aggr_mode or --eth_config=Bxxx.
- Vega 56/64: greatly improved base kernel for efficiency. New B-mode that can shave off additional 1-2W on top of the A-mode kernel. B-mode must be enabled manually with --eth_config (--eth_aggr_mode does not apply). Tuning numbers have changed - do NOT keep your old static --eth_config values.
- Radeon VII: huge boost with its new C-mode but requires a special Linux setup. Can now do 100 MH/s on most air cooled VIIs. See tuning guide.
- 5700/5700XT: can shave off as much as 8-9W(!) of power using the new B-mode and dropping core clk+voltage. B-mode now the default mining mode. Unless you retune your core clk+voltage you will see a tiny power draw increase instead and not benefit from the upgrade, so read the migration guide. 
- 5600XT: new B-mode has a much smaller effect. A-mode remains the default mining mode. See new tuning guide for more details.
- The dag cache is NOT compatible with the new B/C-modes. ETH+ZIL switchers have to choose between caching the epoch 0 dag and using the new mining modes.
- Ethash 4GB kernels NOT rewritten in this release, performance remains the same as in 0.7.x.
- See the migration guide for hashrate and power draw comparisons between 0.7.21 and 0.8.0.

#### Changes
- Ethash: VII kernel rewrite and new C-mode with boost feature (see guide).
- Ethash: Navi kernel slight optimization and new B-mode for lower core clock and power.
- Ethash: Vega kernel rewrite and new B-mode for lower core clock and power.
- Ethash: Polaris kernel rewrite and new B-mode for slightly higher perf.
- Ethash: added share processing timeout and default for Binance pool (see --pool_share_limit_ms).
- Claymore API: fixed leak that stopped serving requests after 32k api calls.
- Claymore API: added password support (see --cm_api_password).
- Logging: added log rotation support (see --log_rotate).
- Logging: log files now contain the miner welcome message so the version is stored.
- Kawpow: now mining ok at MiningPoolHub even though their seedhash is broken.
- Fan control: added min/max fan speed range (see --fan_control).
- General: added argument to turn off duplicate pci bus id filtering (see --allow_dup_bus_ids).

### v0.7.22
#### Notes
1) NAVI KERNEL REWRITE! Over the last month we've been working on new kernels. The first one released is for Navi. The main feature is lower power consumption, hashrate will remain about the same but depends somewhat on clocks. NOTE: please let the miner retune any existing --eth_config arguments for all Navi gpus, the new values will be significantly lower.
2) Claymore API now supported, meaning you can use EthMan to monitor TRM rigs. 

#### Changes
- Ethash: Kernel rewrite for Navi.  Should now be more stable and use less power.  Vega/Polaris still in the works.
- General: Slightly reworked init procedure again to address some rigs running better on <= 0.7.18 than >= 0.7.19.
- General: Added Claymore compatible API, see the --cm_api_listen option.

### v0.7.21
#### Notes
Quick release that addresses situations where Ethash with capped DAG on 4GBs would crash after 5-10 mins when running at 4078-4080MB.

#### Changes
- Ethash: improved probability for high (4078-4080MB) ethash 4GB capped allocation running stable over time.

### v0.7.20
#### Notes
ETH is now approaching the start of the 4GB death with the upcoming switch to epoch 382. TRM was the first miner to add support for mining with 4GB gpus with a partial DAG, here called "extended mining". However, it has always required manual configuration. This release adds a default conservative cap at 4072MB for DAG storage on 4GB gpus for out-of-the-box execution of the miner. For maximum performance, miners are still advised to manually tune their rig(s) with the --eth_4g_max_alloc argument. Most rigs runs stable with a higher value than 4072, which makes a significant difference for upcoming ETH epochs. 

For more detailed instructions, our Ethash 4GB guide has also been updated and is available at https://github.com/todxx/teamredminer/blob/master/doc/ETHASH_4GB_HOWTO.txt

#### Changes
- Ethash: added default capped DAG allocation for 4GBs at 4072MB (see --eth_4g_max_alloc).
- Ethash: bugfix for crashes using --eth_dag_cache on 4GB gpus.

### v0.7.19
#### Notes
1) Ethash solo-miner share high-score list added, use --high_score to enable.
2) Ethash single buffer dag for a small power save. Only available on recent drivers and should in theory always be an improvement. It is not verified 100% stable yet and therefore not the default in this version. Enable with --eth_dag_buf=A to test.
3) Miner gpu initialization procedure rewritten. The init procedure should now hopefully be much more stable, especially on Navis in general and even more so for 5600(XT)s.

#### Changes
- General: added adjustable ratio support for quota and load_balance pool strategies (see --pool_ratio).
- General: rewrote the miner init procedure to be more stable in general.
- General: fixed issue where output blocking could cause mining work to stop.
- General: reduced main binary size.
- Ethash: reintroduced single DAG buffer support for recent drivers allowing large single allocations (see --eth_dag_buf).
- Ethash: added high score list of the 15 highest value shares found since start (see --high_score).
- Ethash: small improvements in keeping the gpu busy over epoch switches. 
- Ethash: fixed bug that would cause deadlocks in rare occasions.
- Ethash: bugfix - dag cache wasn't enabled for 4GB gpus.

### v0.7.18
#### Notes
1) Support for the ETC fork added. Run with "-a etchash" for easiest support, see "--eth_variant_mode" in the help for more info.
2) ETH+ZIL miners: add "--eth_dag_cache=0" to use a second dag cache and prebuild epoch 0 immediately at miner start.
3) Ethash miners relying on ramp-up and stagger for stability: the default mode of these tweaks has been changed to off. They now need to be enabled with --eth_ramp_up and --eth_stagger. While helping a number of rigs, these tweaks caused increased instability of others, making the choice of a good default mode difficult.

#### Changes
- Added etchash support (see algo etchash and --eth_variant_mode).
- Added dag cache support, mostly intended for eth+zil mining (see --eth_dag_cache).
- Fixed hex char parsing in enable/disable submenu, can now work with >= 10 gpus.
- Changed the default for ethash ramp-up and staggering to false (see --eth_ramp_up and --eth_stagger).
- Added check for broken win setups with duplicated opencl platforms and/or devices.

### v0.7.17
#### Changes
- BETA: Added fan control, see --help section or USAGE.txt. Enable with --fan_control.
- Fixed deadlock bug that could happen when using multiple pools with the failover strategy.
- Added option for not sending stale shares (see --no_stale_submit).
- Added watchdog check for early gpu init hangs.
- Added example watchdog scripts for win/linux.

### v0.7.16
#### Notes
BETA RELEASE - small fixes for Turtlecoin's new algo chukwa2.

#### Changes
- Chukwa2: fixed kernels loading for Radeon VII gpus.
- Chukwa2: fixed mem footprint for 2GB gpus.

### v0.7.16b
#### Notes
BETA RELEASE - adds Turtlecoin's new algo chukwa2. Not tested as rigorously as other versions. Only use for the Turtlecoin fork.
NOTE: Navi gpus are NOT supported on chukwa2 for now. Support will be added if there's sufficient interest.

#### Changes
- Added algo trtl_chukwa2 for the Turtlecoin fork on 2020-10-22.

### v0.7.15

#### Notes
Small bugfix release.

#### Changes
- Ethash: fixed bug for ZIL (epoch 0) mining on 4GB gpus (bug appeared in 0.7.14).
- Ethash: reverted to v0.7.10 kernels for stability purposes except for ROCm-based rigs.

### v0.7.14
#### Notes
This release wraps up our work for 4GB gpus mining ethash. Linux 4GB are verified to mine up to and including epoch 381 on drivers 18.50/19.30/19.50/20.10. After that, we have added support for extended mining from epoch 382 and up. Extended mining is a trade-off between hashrate and being able to mine at all, gpus will lose additional hashrate for every extra epoch. Please see the Linux section in the ETHASH_4GB_HOWTO.txt for more details and instructions.

#### Changes
- Ethash: verified Linux support for 4GB gpus up to and including epoch 381.
- Ethash: added support for extended 4GB mining from epoch 382 and up.
- Kawpow: cleaned up false hw errs for some block heights.

### v0.7.13
#### Notes
1) Windows user with 4GB rigs - see the new guide ETHASH_4GB_HOWTO.txt for instructions.

#### Changes
- Added better default Windows dag allocation strategy on 4GB gpus.
- Added experimental support for resetting gpus before mining (Windows only).
- Added argument for manual adjustment of 4GB dag allocation (see --eth_4g_alloc_adjust=X,Y,Z,...).
- Added protection against broken dev servers with additional random server selection mechanism.

### v0.7.12
#### Notes
1) Bugfix release: v0.7.11 could crash with rejected ethash shares.

#### Changes
- Fixed print format bug on ethash rejected shares.

### v0.7.11
#### Notes
1) Ethash additions: printing share diff in GH (always enabled), hashrate watchdog (see --eth_hashwatch).
2) Better debug support: --long_timestamps, --pool_debug.
3) We've found certain motherboard/bios combinations that due to kernel and/or driver bugs have issues with the first or last gpu in rigs. If you see excessive hw errors reported on a single gpu, and switching around gpus still always generates errors in the first or last gpu, try using --eth_dag_alloc_patch.

#### Changes
- Added DAG allocation patch under linux for certain mobo/bios combinations (see --eth_dag_alloc_patch).
- Added ethash hashrate watchdog (see --eth_hashwatch).
- Added ethash abort mechanism for Vegas on ROCm (see --eth_direct_abort). Not useful in other contexts.
- Added pool traffic debug (use --pool_debug).
- Added print of share difficulty for ethash family algos. Unit is always GH.
- Added microsec timestamp resolution in logs (use --long_timestamps).
- Regression bug: argon2/chukwa was broken in 0.7.10, now working again.
- Turned off compute mode checks for non-Polaris gpus.

### v0.7.10
#### Notes
1) Ethash 4GB rigs, especially on win, _should_ use --eth_alloc_epoch=N with N being the max epoch that the gpus can allocate. This will avoid DAG reallocation issues.
2) For Navi rigs having issues with eth+zil or Nicehash mining with frequent DAG switching, try using --eth_dag_slowdown=9.

#### Changes
- Added default log filename (trm_<algo>_<yyyymmdd_hhmmss>.log)
- Added ethash forced initial allocated epoch ( --eth_alloc_epoch=N). Note: HIGHLY recommended for 4GB rigs.
- Added ethash family DAG build slowdown configuration (--eth_dag_slowdown=N, default value 4).
- Added ethash family DAG build staggering across gpus (disable with --eth_no_stagger).
- Added ethash family intensity ramp-up (disable with --eth_no_ramp_up).
- Added option for forcing dev fee region (see --dev_location).
- Added MTP for Navi gpus.
- Added MTP ramp-up after pad rebuild.
- Fixed error printouts on failed watchdog script execution on Linux.
- Stats: now shows more clocks and temps, and also adds gpu state in hashrate prints (see --short_stats to disable).
- Added checks for and enabling compute mode and disabling crossfire on Windows (see --enable_compute).

### v0.7.9
#### Changes
- Fixes for mixed rig mining on Linux.
- Added --eth_epoch argument for easier epoch testing.
- Added --eth_aggr_mode for automatic aggressive 'B' mode on Polaris 8GB gpus.
- Added --watchdog_disable argument.

### v0.7.8
#### Changes
- Upgrade for the upcoming Haven hard fork (July 20, 2020).
- Tiny Nimiq optimizations (1-2% max, mostly Vega and Navi).
- Fixed CPU usage issue when redirecting stdin to /dev/null.
- Fixed pool name returned by API for Nimiq.

### v0.7.7
#### Changes
- Added support for Nimiq Polaris/Vega (dumb mode only).
- Integrated a Nimiq node.js network proxy into the miner.
- Fixed Nimiq bug that could lose shares, especially against lower vardiff pools.
- Fixed Nimiq bug that could cause duplicate shares on startup for low-diff pools.
- Fixed regression bug for ethash Nicehash, correct stratum mode now used again.
- Added support for Nimiq Navi.
- Added support for icemining Nimiq solo mining mode (set -p m=solo).

### v0.7.6
#### Changes
- Fixed broken keyboard input in tmux+screen sessions (e.g. Hive OS).
- Added support for 5500(xt).
- Fixed Linux watchdog support for hard driver crashes (script was not executed).
- Fixed kawpow nicehash extranonce support.

### v0.7.5
#### Changes
- Fixed broken optimizations for kawpow in 0.7.4.

### v0.7.4
#### Changes
- Increased ethash support on 4GB GPUs up to epoch 380-383
- Implemented split ethash dag buffers for 8GB GPUs to support DAGs over 4GB
- Kawpow optimizations (Navi +2.25%, Vega +1.25%, Polaris +0.25%)
- Added gpu enable/disable API support.
- Windows TDR detection/handling/warning.
- Monitor detection on Windows/Linux with intensity adjustment.
- Fix for ethash pool hashrate reporting stopping after network outage.

### v0.7.3
#### Changes
- Emergency patch for 4GB cards to handle a few more ETC epochs.
  A more complete patch is coming out shortly.

### v0.7.2
#### Changes
- Fixed kawpow dag build DEAD gpu issue on windows Adrenalin 2020 drivers.
- Fixed Navi 5600(xt) support on windows.
- Fixed mining on Vegas on older amdgpu-pro drivers.
- Fixed ADL reporting of stats on windows for newer cards.

### v0.7.1
#### Changes
- Fixed issue with VII ethash/kawpow on windows.

### v0.7.0
#### Changes
- Added kawpow algo for Ravencoin.
- Added Navi support for kawpow and ethash.
- Changed device ordering to be pcie bus based by default, added --opencl_order option.
- Fixed issue with --list devices not working without other args.
- Reformatted help message to hopefully make it easier to read.
- Added multipool example scripts.
- Removed ssl/tls server name verification (was re-added with TLS SNI fix)
- Fixed an unhandled signal bug that would cause rare crashes.
- Fixed multi-pool API bug.
