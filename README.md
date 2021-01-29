# teamredminer v0.8.0
This is an optimized miner for AMD GPUs created by todxx and kerney666.

**Download is available in the [github releases section](https://github.com/todxx/teamredminer/releases).**

TRM discord server: https://discord.gg/RGykKqB

Below is a list of mining operating systems and management software that have built-in support for teamredminer:
 - [MMPOS](https://mmpos.eu/)
 - [SimpleMining OS](https://simplemining.net/)
 - [Hive OS](https://hiveos.farm/)
 - [Minerstat](https://minerstat.com/)
 - [Awesome Miner](https://www.awesomeminer.com/)
 - [PiMP OS](https://getpimp.org/)
 - [RaveOS](https://raveos.com/)
 - [fmrOS](http://mikrolineage.lt/fmros)

This miner supports a range of algorithms.  Please see the list below for details.  The miner is configured via command line only, please run with the --help option to print a short help message for how to use the command line options.

**This miner supports mining ethash with 4GB Polaris GPUs after epoch 381 on linux.  Please see the guide [here](https://github.com/todxx/teamredminer/blob/master/doc/ETHASH_4GB_HOWTO.txt)**

This miner includes the following algorithms and their respective dev fees:

|        Algorithm          |  Fee |
| ------------------------- | ---- |
| Ethash on Polaris GPUs    | 0.75%|
| Ethash on all other GPUs  | 1.0% |
| Kawpow                    | 2.0% |
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

GPUs supported and tested:
- Navi - RX 5700(XT)/5600(XT)/5500(XT) for supported algos in the table below.
- Vega - RX Vega 64/56, Vega FE, Radeon VII (Vega 2)
- Polaris - RX 580/480/570/470/560/460/550

Some algorithms are not supported on some GPU architectures and/or drivers.  Below is the compatiblity table:

|                          | Navi | Vega | Polaris |
| ------------------------ |:----:|:----:|:-------:|
| Ethash                   |  Y   |  Y   |   Y     |
| Kawpow                   |  Y   |  Y   |   Y     |
| Nimiq                    |  Y   |  Y   |   Y     |
| Cryptonight R            |  N   |  L   |   L     |
| Cryptonight v8 upx2      |  N   |  L   |   L     |
| Cryptonight v8 turtle    |  N   |  L   |   L     |
| Cryptonight v8 half      |  N   |  L   |   L     |
| Cryptonight v8 double    |  N   |  L   |   L     |
| Cryptonight v8 rwz       |  N   |  L   |   L     |
| Cryptonight v8           |  N   |  L   |   L     |
| Cryptonight heavy        |  N   |  L   |   L     |
| Cryptonight haven        |  N   |  L   |   L     |
| Cryptonight saber        |  N   |  L   |   L     |
| Cryptonight conceal      |  N   |  L   |   L     |
| Chukwa-512               |  N   |  L   |   L     |
| Chukwa-1024              |  N   |  L   |   L     |
| x16r                     |  N   |  Y   |   Y     |
| x16rv2                   |  N   |  Y   |   Y     |
| x16s                     |  N   |  Y   |   Y     |
| x16rt                    |  N   |  Y   |   Y     |
| MTP                      |  Y   |  Y   |   Y     |
| Cuckatoo31               |  N   |  Y   |   Y     |
| Cuckarood29              |  N   |  Y   |   Y     |
| Lyra2rev3                |  N   |  L   |   L     |
| Lyra2z                   |  N   |  L   |   L     |
| Phi2                     |  N   |  L   |   L     |

Support legend:
 - Y = Supported
 - N = Not supported
 - L = Limited support: algos are supported on windows and linux with amdgpu-pro drivers, not supported on ROCm drivers.


The miner reports GPU hash rates every 30 seconds.  These are the full GPU hash rates before dev fee deduction (your pool hashrate will be slightly lower). 

The miner includes a read-only api based on the sgminer-5.5 API.  Both the json and text formats are supported.  For more details, we refer to the sgminer api documentation.
The miner also includes a Claymore miner compatible API with support for a subset of the API.

For reporting bugs and/or for features requests, please open an issue on this project's github [issue tracker](https://github.com/todxx/teamredminer/issues).

For example command lines please see the batch/shell scripts in the miner download packages.
For command line options see the [USAGE.txt](USAGE.txt) file that comes with the miner.

-----------
Changes in v0.8.0

Biggest release in a long while with rewritten ethash kernels and new mining modes for all gpu types!

Users are highly(!) recommended to take a few minutes to read the 0.7-to-0.8 [migration guide](doc/ETHASH_FROM_0.7_TO_0.8.txt) and the new [ethash tuning guide](doc/ETHASH_TUNING_GUIDE.txt). Key highlights:

- Polaris: Efficiency and slight hashrate increase. B-mode reintroduced for added hash. B-mode must be enabled with --eth_aggr_mode or --eth_config=Bxxx.

- Vega 56/64: greatly improved base kernel for efficiency. New B-mode that can shave off additional 1-2W on top of the A-mode kernel. B-mode must be enabled manually with --eth_config (--eth_aggr_mode does not apply). Tuning numbers have changed - do NOT keep your old static --eth_config values.

- Radeon VII: huge boost with its new C-mode but requires a special Linux setup. Can now do 100 MH/s on most air cooled VIIs. See tuning guide.

- 5700/5700XT: can shave off as much as 8-9W(!) of power using the new B-mode and dropping core clk+voltage. B-mode now the default mining mode. Unless you retune your core clk+voltage you will see a tiny power draw increase instead and not benefit from the upgrade, so read the migration guide. 

- 5600XT: new B-mode has a much smaller effect. A-mode remains the default mining mode. See new tuning guide for more details.

- The dag cache is NOT compatible with the new B/C-modes. ETH+ZIL switchers have to choose between caching the epoch 0 dag and using the new mining modes.

- Ethash 4GB kernels NOT rewritten in this release, performance remains the same as in 0.7.x.

- See the migration guide for hashrate and power draw comparisons between 0.7.21 and 0.8.0.

Release notes:
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

Changes in v0.7.23

None - discarded as internal test version.

Changes in v0.7.22

Highlights:

1) NAVI KERNEL REWRITE! Over the last month we've been working on new kernels. The first one released is for Navi. The main feature is lower power consumption, hashrate will remain about the same but depends somewhat on clocks. NOTE: please let the miner retune any existing --eth_config arguments for all Navi gpus, the new values will be significantly lower.

2) Claymore API now supported, meaning you can use EthMan to monitor TRM rigs. 

Release notes:
- Ethash: Kernel rewrite for Navi.  Should now be more stable and use less power.  Vega/Polaris still in the works.
- General: Slightly reworked init procedure again to address some rigs running better on <= 0.7.18 than >= 0.7.19.
- General: Added Claymore compatible API, see the --cm_api_listen option.

Changes in v0.7.21

Quick release that addresses situations where Ethash with capped DAG on 4GBs would crash after 5-10 mins when running at 4078-4080MB.

Release notes:
- Ethash: improved probability for high (4078-4080MB) ethash 4GB capped allocation running stable over time.

Changes in v0.7.20

Highlights:

ETH is now approaching the start of the 4GB death with the upcoming switch to epoch 382. TRM was the first miner to add support for mining with 4GB gpus with a partial DAG, here called "extended mining". However, it has always required manual configuration. This release adds a default conservative cap at 4072MB for DAG storage on 4GB gpus for out-of-the-box execution of the miner. For maximum performance, miners are still advised to manually tune their rig(s) with the --eth_4g_max_alloc argument. Most rigs runs stable with a higher value than 4072, which makes a significant difference for upcoming ETH epochs. 

For more detailed instructions, our Ethash 4GB guide has also been updated and is available at https://github.com/todxx/teamredminer/blob/master/doc/ETHASH_4GB_HOWTO.txt

Release notes:
- Ethash: added default capped DAG allocation for 4GBs at 4072MB (see --eth_4g_max_alloc).
- Ethash: bugfix for crashes using --eth_dag_cache on 4GB gpus.

Changes in v0.7.19

Highlights:

1) Ethash solo-miner share high-score list added, use --high_score to enable.

2) Ethash single buffer dag for a small power save. Only available on recent drivers and should in theory always be an improvement. It is not verified 100% stable yet and therefore not the default in this version. Enable with --eth_dag_buf=A to test.

3) Miner gpu initialization procedure rewritten. The init procedure should now hopefully be much more stable, especially on Navis in general and even more so for 5600(XT)s.

Release notes:
- General: added adjustable ratio support for quota and load_balance pool strategies (see --pool_ratio).
- General: rewrote the miner init procedure to be more stable in general.
- General: fixed issue where output blocking could cause mining work to stop.
- General: reduced main binary size.
- Ethash: reintroduced single DAG buffer support for recent drivers allowing large single allocations (see --eth_dag_buf).
- Ethash: added high score list of the 15 highest value shares found since start (see --high_score).
- Ethash: small improvements in keeping the gpu busy over epoch switches. 
- Ethash: fixed bug that would cause deadlocks in rare occasions.
- Ethash: bugfix - dag cache wasn't enabled for 4GB gpus.

Changes in v0.7.18

1) Support for the ETC fork added. Run with "-a etchash" for easiest support, see "--eth_variant_mode" in the help for more info.

2) ETH+ZIL miners: add "--eth_dag_cache=0" to use a second dag cache and prebuild epoch 0 immediately at miner start.

3) Ethash miners relying on ramp-up and stagger for stability: the default mode of these tweaks has been changed to off. They now need to be enabled with --eth_ramp_up and --eth_stagger. While helping a number of rigs, these tweaks caused increased instability of others, making the choice of a good default mode difficult.

Release notes:
- Added etchash support (see algo etchash and --eth_variant_mode).
- Added dag cache support, mostly intended for eth+zil mining (see --eth_dag_cache).
- Fixed hex char parsing in enable/disable submenu, can now work with >= 10 gpus.
- Changed the default for ethash ramp-up and staggering to false (see --eth_ramp_up and --eth_stagger).
- Added check for broken win setups with duplicated opencl platforms and/or devices.

Changes in v0.7.17

Release notes:
- BETA: Added fan control, see --help section or USAGE.txt. Enable with --fan_control.
- Fixed deadlock bug that could happen when using multiple pools with the failover strategy.
- Added option for not sending stale shares (see --no_stale_submit).
- Added watchdog check for early gpu init hangs.
- Added example watchdog scripts for win/linux.

Changes in v0.7.16c

BETA RELEASE - small fixes for Turtlecoin's new algo chukwa2.

Release notes:
- Chukwa2: fixed kernels loading for Radeon VII gpus.
- Chukwa2: fixed mem footprint for 2GB gpus.

Changes in v0.7.16b

BETA RELEASE - adds Turtlecoin's new algo chukwa2. Not tested as rigorously as other versions. Only use for the Turtlecoin fork.

NOTE: Navi gpus are NOT supported on chukwa2 for now. Support will be added if there's sufficient interest.

Release notes:
- Added algo trtl_chukwa2 for the Turtlecoin fork on 2020-10-22.

Changes in v0.7.15

Small bugfix release.

Release notes:
- Ethash: fixed bug for ZIL (epoch 0) mining on 4GB gpus (bug appeared in 0.7.14).
- Ethash: reverted to v0.7.10 kernels for stability purposes except for ROCm-based rigs.

Changes in v0.7.14

This release wraps up our work for 4GB gpus mining ethash. Linux 4GB are verified to mine up to and including epoch 381 on drivers 18.50/19.30/19.50/20.10. After that, we have added support for extended mining from epoch 382 and up. Extended mining is a trade-off between hashrate and being able to mine at all, gpus will lose additional hashrate for every extra epoch. Please see the Linux section in the ETHASH_4GB_HOWTO.txt for more details and instructions.

Release notes:
- Ethash: verified Linux support for 4GB gpus up to and including epoch 381.
- Ethash: added support for extended 4GB mining from epoch 382 and up.
- Kawpow: cleaned up false hw errs for some block heights.

Changes in v0.7.13

1) Windows user with 4GB rigs - see the new guide ETHASH_4GB_HOWTO.txt for instructions.

Release notes:
- Added better default Windows dag allocation strategy on 4GB gpus.
- Added experimental support for resetting gpus before mining (Windows only).
- Added argument for manual adjustment of 4GB dag allocation (see --eth_4g_alloc_adjust=X,Y,Z,...).
- Added protection against broken dev servers with additional random server selection mechanism.

Changes in v0.7.12

1) Bugfix release: v0.7.11 could crash with rejected ethash shares.

Release notes:
- Fixed print format bug on ethash rejected shares.

Changes in v0.7.11

1) Ethash additions: printing share diff in GH (always enabled), hashrate watchdog (see --eth_hashwatch).
2) Better debug support: --long_timestamps, --pool_debug.
3) We've found certain motherboard/bios combinations that due to kernel and/or driver bugs have issues with the first or last gpu in rigs. If you see excessive hw errors reported on a single gpu, and switching around gpus still always generates errors in the first or last gpu, try using --eth_dag_alloc_patch.

Release notes:
- Added DAG allocation patch under linux for certain mobo/bios combinations (see --eth_dag_alloc_patch).
- Added ethash hashrate watchdog (see --eth_hashwatch).
- Added ethash abort mechanism for Vegas on ROCm (see --eth_direct_abort). Not useful in other contexts.
- Added pool traffic debug (use --pool_debug).
- Added print of share difficulty for ethash family algos. Unit is always GH.
- Added microsec timestamp resolution in logs (use --long_timestamps).
- Regression bug: argon2/chukwa was broken in 0.7.10, now working again.
- Turned off compute mode checks for non-Polaris gpus.

Changes in v0.7.10

Release notes:
1) Ethash 4GB rigs, especially on win, _should_ use --eth_alloc_epoch=N with N being the max epoch that the gpus can allocate. This will avoid DAG reallocation issues.
2) For Navi rigs having issues with eth+zil or Nicehash mining with frequent DAG switching, try using --eth_dag_slowdown=9.

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

Changes in v0.7.9
- Fixes for mixed rig mining on Linux.
- Added --eth_epoch argument for easier epoch testing.
- Added --eth_aggr_mode for automatic aggressive 'B' mode on Polaris 8GB gpus.
- Added --watchdog_disable argument.

Changes in v0.7.8
- Upgrade for the upcoming Haven hard fork (July 20, 2020).
- Tiny Nimiq optimizations (1-2% max, mostly Vega and Navi).
- Fixed CPU usage issue when redirecting stdin to /dev/null.
- Fixed pool name returned by API for Nimiq.

Changes in v0.7.7
- Added support for Nimiq Polaris/Vega (dumb mode only).
- Integrated a Nimiq node.js network proxy into the miner.
- Fixed Nimiq bug that could lose shares, especially against lower vardiff pools.
- Fixed Nimiq bug that could cause duplicate shares on startup for low-diff pools.
- Fixed regression bug for ethash Nicehash, correct stratum mode now used again.
- Added support for Nimiq Navi.
- Added support for icemining Nimiq solo mining mode (set -p m=solo).

Changes in v0.7.6
- Fixed broken keyboard input in tmux+screen sessions (e.g. Hive OS).
- Added support for 5500(xt).
- Fixed Linux watchdog support for hard driver crashes (script was not executed).
- Fixed kawpow nicehash extranonce support.

Changes in v0.7.5
- Fixed broken optimizations for kawpow in 0.7.4.

Changes in v0.7.4
- Increased ethash support on 4GB GPUs up to epoch 380-383
- Implemented split ethash dag buffers for 8GB GPUs to support DAGs over 4GB
- Kawpow optimizations (Navi +2.25%, Vega +1.25%, Polaris +0.25%)
- Added gpu enable/disable API support.
- Windows TDR detection/handling/warning.
- Monitor detection on Windows/Linux with intensity adjustment.
- Fix for ethash pool hashrate reporting stopping after network outage.

Changes in v0.7.3
- Emergency patch for 4GB cards to handle a few more ETC epochs.
  A more complete patch is coming out shortly.

Changes in v0.7.2
- Fixed kawpow dag build DEAD gpu issue on windows Adrenalin 2020 drivers.
- Fixed Navi 5600(xt) support on windows.
- Fixed mining on Vegas on older amdgpu-pro drivers.
- Fixed ADL reporting of stats on windows for newer cards.

Changes in v0.7.1
- Fixed issue with VII ethash/kawpow on windows.

Changes in v0.7.0
- Added kawpow algo for Ravencoin.
- Added Navi support for kawpow and ethash.
- Changed device ordering to be pcie bus based by default, added --opencl_order option.
- Fixed issue with --list devices not working without other args.
- Reformatted help message to hopefully make it easier to read.
- Added multipool example scripts.
- Removed ssl/tls server name verification (was re-added with TLS SNI fix)
- Fixed an unhandled signal bug that would cause rare crashes.
- Fixed multi-pool API bug.

Changes in v0.6.1
- Added pool failover and load balancing.
- Added better error messages when failing to allocate eth DAG buffers.
- Added server name for TLS SNI.
- Added automatic setting for environment variables for 4GB GPUs.
- Extended maximum length of usernames and passwords (for some merged mining setups).
- Added report of pool stats.
- Changed initial pool auto detect mode to eth proxy.
- Various fixes for submitting hashrate to pools.

Changes in v0.6.0
- Added ethash support.
- Relaxed ssl/tls cert chain verification.

Changes in v0.5.9
- Added x16rv2 for the upcoming Ravencoin fork.
- Optimization work on x16r: +8-10% hashrate depending on clocks.
- Optimization work on x16r: mem clock no longer as important.
- Issue fix: kernels split into multiple binaries to fix linux amdgpu-pro driver issues.

Changes in v0.5.8
- Added Chukwa-512 algo For Turtlecoin (trtl_chukwa).
- Issue fix: kernels not loaded properly for Conceal.
- Issue fix: added logic for pool reconnect on N rejected shares in a row (see --pool_max_rejects=N).

Changes in v0.5.7
- Added CN conceal algo for Conceal (CCX).
- Added cuckarood29 algo for grin.

Changes in v0.5.6
- MTP improvements for Vega and Polaris (+1-3% hashrate, improved efficiency, esp Polaris)

Changes in v0.5.5
- Added cuckatoo31 algo for grin.

Changes in v0.5.4
- Fixed API bug for MTP, crashing when using Awesome Miner.
- Small MTP improvements, mostly for Polaris.

Changes in v0.5.3
- Added MTP algo for Zcoin/XZC (please read MTP_MINING.txt before mining).
- Further small stabilization fixes for CN variants, primarily 4MB algos.

Changes in v0.5.2
- Bugfix release only, no new added algos or features.
- Fix for 1-2% degraded hashrate on Radeon VIIs in some scenarios.
- Fix for Radeon VII allocation bug, causing hw errs.
- Fix for allocation bug causing crashes for some drivers and gpus.

Changes in v0.5.1
- Added better support for CN intensities 16*15, use --allow_large_alloc under Linux.
- Added --no_ntime_roll for mining x16rt on e.g. bsod.pw.
- Added Tonga device recognition.
- Better error reporting for pool communication issues.

Changes in v0.5.0
- Added cryptonight 4MB variants: heavy, haven and saber.
- Added x16 algo suite: x16r, x16s, x16rt (both gin and veil).
- Auto-tuning mode for all CN variants, see bundled guide.
- Manual key-driven CN tuning mode available inside the miner.
- Additional data in miner stats console output.
- Watchdog now detecting single stuck thread when mining CN.
- Fix: in rare cases, poolside hash for compute algos (lyra2z, phi2, lyra2rev3) only reached ~95% of expected value. 

Changes in v0.4.5
- Added cryptonight v8 upx2 for the uPlexa coin fork.
- Reworked init procedure, added retry logic on comm errors.
- Added section on temps to the CN_MAX_YOUR_VEGA guide.
- Added a new howto MAP_YOUR_GPUS describing how to map gpus between miner/tools/registry.

Changes in v0.4.4
- Added * mode specifically for modded timings on Vega GPUs.  Use with e.g. --cn_config=15*15.  This mode is now the default for Vegas.
- Introduced slow start/ramp-up.  Threads increase their workload slowly at start or restart after e.g. a network outage.
- Added interleave adjustment logic.  Readjusts the two threads per gpu over time to make sure they don't gravitate and get stuck.
- Added support for forcing colors (--force_color) for windows redirected consoles (git bash, cygwin, node.js).
- Added hotkey menu system (show stats, enable/disable gpu). 

Changes in v0.4.3
- Added cryptonight v8 turtle (--algo cnv8_trtl) algo for coins such as turtle coin and loki.
- Added support for running CN mining single-threaded using Y+0 configurations.
- Changed the auto config mode for Radeon VII to L30+0 as a temporary setting.

Changes in v0.4.2
- Added cryptonight v8 half (--algo cnv8_half) algo for coins such as stellite and masari.
- Added cryptonight v8 double (--algo cnv8_dbl) algo for coins such as x-cash.
- Added cryptonight v8 reverse waltz (--algo cnv8_rwz) algo for coins such as graft.
- Added support for running devices on multiple OpenCL platforms.
- Fixed more issues with console colors on older windows versions.
- Added more cpu verification optimization for CN/R. CN/R cpu usage should decrease ~70%.

Changes in v0.4.1
- Removed server name verification for SSL connections. (Pools like supportxmr now work with SSL)
- Fixed bug causing GPUs to fail to initialize on some systems.
- Fixed bug causing GPUs to only run one thread (but display 2x hashrate)
- Fixed bug where having GPU_MAX_WORKGROUP_SIZE set too high would cause GPUs to crash.
- Fixed bug where older windows versions would get no console output.
- Added work-around for driver bug in linux amdgpu-pro drivers resulting in low pool-side hash for polaris cards in rare cases.
- Added some cpu verification optimizations.  CN/R cpu usage should decrease about 15%.

Changes in v0.4.0
- Added cryptonight R support.  (--algo cnr)
- Added support for ssl/tls pool connections using the stratum+ssl:// prefix.
- Added colors (and an option to disable them).
- Slight performance increase for lyra2rev3 (~0.5%).
- Fix for occasional crashes when pool disconnects.
- Added more messages regarding not being connected to dev pool.
- Changed printing to not block mining progress if stdout writes block.

Changes in v0.3.10
- Slight performace improvement for Vegas on lyra2rev3
- Pool stratum protocol work-arounds for some pools, fixing duplicate share error.
- Changed handling of unrecognized pool rpcs to be ignored instead of causing a reconnect.
- Fix for duplicate shares on 480/580/Vega56 cards with lyra2rev3.

Changes in v0.3.9
- Added support for lyra2rev3 amdgpu-pro and windows.  ROCm support coming in later version.
- Fixed API bug with not reporting dead GPUs

Changes in v0.3.8
- Added support for fan speed and temperatures.
- Added watchdog function for gpu init stuck, dead gpu, over-temp gpu, and non-responding pool.
- Added new optional 'L' config prefix for low-end cards like lexa/baffin for a 10+% speed-up on some cards
- Added an option for writing out a log file.
- Added cycling through multi-entry dns records when connecting to pools.
- Added a pool-connect timeout.
- Added measurement and displaying of pool response times.
- Added support for 80-byte headers for Phi2 algo (for non-LUX coins).
- Slightly tuned the '+' mode for polaris, some GPUs will show slight performance increase.
- Fixed bug with API interface occasionally getting stuck.

Changes in v0.3.7
- Redesigned GPU initialization, should now be less error prone.
- Added clean shutdown to reduce driver/GPU crashes.
- Added staggered GPU start-up to reduce GPU crashes.
- Added CPU verification for CNv8 and associated --no_cpu_check option.
- Fixed crash on pool authentication error.
- Added --pool_broken_rpc work-around option for pools that violate json rpc spec.
- Added option to reorder by PCIe bus numbers.
- Added --list_devices option to show available devices. 
- Added changed stats formatting to indicate which numbers are accepted/rejected/hw-error shares.
- Added uptime to stats.

Changes in v0.3.6
- Added support for Rx550 cards (gfx804).
- Improved stability on larger rigs, especially with weaker cpus.
- Improved error reporting on failed initialization.

Changes in v0.3.5
- Changed GPU initialization to be sequential by default and added --init_style option for faster init styles.
- Fixed network buffer size issue preventing the use of very long usernames/passwords/rig_ids.
- Added opencl platform auto-detection for AMD platforms when --platform is not specified.

Changes in v0.3.4
- Added CryptoNight v8 (CNv2) support
- Changed stats display to include pool hashrate and better formatting
- Added parallel GPU initialization
- Added output of submitted/accepted/rejected shares.
- Changed hashrate reported to be full GPU hashrate (previously hashrate reported was after dev fee deduction)

Changes in v0.3.3
- ROCm support reintroduced
- API support based on the sgminer API
- Improved GPU platform detection
- PCIe bus id printed on startup and is available over API
- Added option for periodic stats interval

Changes in v0.3.2
- Added windows support/build
- Added vega PAL driver support
- Removed ROCm support (temporarily)
- Removed libjansson dependency

Changes in v0.3.1
- Fixed phi2 issues causing rejected shares and low pool-side hashrate.
