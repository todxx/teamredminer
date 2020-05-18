# teamredminer v0.7.0

Download is available in the [releases section](https://github.com/todxx/teamredminer/releases).

TRM discord server: https://discord.gg/RGykKqB

GPUs supported and tested:
- RX 5700(XT) for kawpow and ethash only.
- Radeon VII
- RX Vega 64/56, Vega FE
- RX 580/570/480/470
- RX 560/550

Software Requirements:
- For cryptonight algos and lyra2rev3 on linux, only amdgpu-pro 18.30 and later drivers are supported.  ROCm is not supported.

This miner supports a range of algorithms.  Please see the list below for details.  The miner is configured via command line only, please run with the --help option to print a short help message for how to use the command line options.

The miner includes a read-only api based on the sgminer-5.5 API.  Both the json and text formats are supported.  For more details, we refer to the sgminer api documentation.  

This miner includes the following algorithms and respective dev fees:
- Ethash on Polaris GPUs    0.75%
- Ethash on all other GPUs  1.0%
- Kawpow                    2.0%
- Cryptonight R:            2.5%
- Cryptonight v8 upx2:      2.5%
- Cryptonight v8 turtle:    2.5%
- Cryptonight v8 half:      2.5%
- Cryptonight v8 double:    2.5%
- Cryptonight v8 rwz:       2.5%
- Cryptonight v8:           2.5%
- Cryptonight heavy:        2.5%
- Cryptonight haven:        2.5%
- Cryptonight saber:        2.5%
- Cryptonight conceal:      2.5%
- Chukwa-512 (Turtlecoin):  2.5%
- x16r:                     2.5%
- x16rv2:                   2.5%
- x16s:                     2.5%
- x16rt:                    2.5%
- MTP:                      2.5%
- Cuckatoo31:               2.5%
- Cuckarood29:              2.5%
- Lyra2rev3:                2.5%
- Lyra2z:                   3%
- Phi2:                     3%

The miner reports GPU hash rates every 30 seconds.  These are the full GPU hash rates before dev fee deduction (your pool hashrate will be slightly lower). 

For reporting bugs and/or for features requests, please open an issue on this project's github [issue tracker](https://github.com/todxx/teamredminer/issues).

Happy hashing ;)

-----------
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
