# teamredminer v0.4.3

This software is in a beta stage and may be unstable on some hardware.

Download is available in the [releases section](https://github.com/todxx/teamredminer/releases).

GPUs supported and tested:
- RX 580/570/480/470 on windows and linux with rocm or amdgpu-pro drivers
- RX Vega 64/56, Vega FE on windows and linux with rocm or amdgpu-pro/PAL drivers
- RX 560/550 on windows and linux with rocm or amdgpu-pro drivers

GPUs supported and untested:
- Radeon VII on windows and linux with rocm or amdgpu-pro/PAL drivers (currently limited CN performance)

Software Requirements:
- A supported driver version (see GPUs Supported above)
- For cryptonight algos and lyra2rev3 on linux, only amdgpu-pro 18.30 and later drivers are supported.  ROCm is not supported.

This miner currently supports the lyra2z, phi2, cryptonight R, cryptonight v8, cryptonight v8 turtle, cryptonight v8 half, cryptonight v8 double, and cryptonight v8 reverse waltz algorithms. Its configuration is via command line, please run with the --help option will print a short help message for how to use the command line options.

The miner includes a read-only api based on the sgminer-5.5 API.  Both the json and text formats are supported.  For more details, we refer to the sgminer api documentation.  

This miner includes the following dev fees:
- Cryptonight R:            2.5%
- Cryptonight v8 turtle:    2.5%
- Cryptonight v8 half:      2.5%
- Cryptonight v8 double:    2.5%
- Cyrptonight v8 rwz:       2.5%
- Cryptonight v8:           2.5%
- Lyra2rev3:                2.5%
- Lyra2z:                   3%
- Phi2:                     3%

The miner reports GPU hash rates every 30 seconds.  These are the full GPU hash rates before dev fee deduction (your pool hashrate will be slightly lower). 

For reporting bugs and/or for features requests, please open an issue on this project's github [issue tracker](https://github.com/todxx/teamredminer/issues).

Happy hashing ;)

-----------
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
