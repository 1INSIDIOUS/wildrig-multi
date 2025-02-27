# WildRig Multi
multi algo miner for AMD & NVIDIA

# KNOWN ISSUES
- rejected shares on Vega gpu's for progpow family of algorithms if use kernel 2(kernel 1 works fine)
- broken mtp algorithm under Linux, miner can't find any share
- not all algorithms working on NVIDIA gpu's right now, and not all of them are optimized(see Release Notes)
- broken honeycomb algoithm, last working version is **0.17.6**
- "Duplicate share" error on some pools for progpowz
- any report is welcome! :)

# SUPPORTED GPU's
## AMD:
- **GCN 2nd gen**: R7 260, R9 290, R9 295X2, R7 360, R9 390
- **GCN 3rd gen**: R9 285, R9 380, R9 Fury, R9 Nano
- **GCN 4th gen**: RX460, RX470, RX480, RX550, RX560, RX570, RX580, RX590
- **GCN 5th gen**: Vega 11, Vega 56, Vega 64, Radeon VII
- **RDNA 1st gen**: Radeon 5500XT, Radeon 5600XT, Radeon 5700, Radeon 5700XT
- **RDNA 2nd gen**: Radeon 6500XT, Radeon 6600XT, Radeon 6700 XT, Radeon 6800XT, Radeon 6900 XT

## NVIDIA:
- All gpu's with Compute Capabilities >=5.0 should work
- also specific gpu can be supported via use of --ptx-version parameter(like --ptx-version 71 for sm_86, more ptx version is [here](https://docs.nvidia.com/cuda/parallel-thread-execution/#release-notes))

# SUPPORTED ALGORITHMS
- aergo, anime
- bcd, bitcore, blake2b-btcc, blake2b-glt, blake2s, bmw512
- c11
- dedal
- exosis
- geek, ghostrider, glt-astralhash, glt-globalhash, glt-jeonghash, glt-padihash, glt-pawelhash
- heavyhash, hex, hmq1725, honeycomb
- kawpow
- lyra2tdc, lyra2v2, lyra2v3, lyra2vc0ban
- megabtx, megamec, minotaur, mtp, mtp-tcr
- nist5
- phi, phi5, polytimos, progpowz, progpow-ethercore, progpow-sero, progpow-veil
- quark, quibit
- renesis
- sha256, sha256csm, sha256d, sha256q, sha256t, skein2, skunkhash, sonoa
- timetravel, tribus
- vprogpow
- wildkeccak
- x11, x11k, x12, x13, x14, x15, x16r, x16rv2, x16s, x17, x17,r x18, x20r, x21s, x22i, x25x, x33, xevan

# DEV-FEE:
- by default is 1%
- lyra2TDC, megabtx, phi5, sha256csm, x17r and wildkeccak algorithms are 2%
- minotaur is 5%

# OPTIONS
```
  -a, --algo=ALGO               specify the hash algorithm to use

      --benchmark               run offline benchmark
      --benchmark-hashorder     run offline benchmark and/or set hash order for benchmark
      --benchmark-epoch         run offline benchmark and/or set epoch for benchmark
      --benchmark-block         run offline benchmark and/or set block for benchmark
      --benchmark-timeout       run offline benchmark and/or set how long to run benchmark in seconds(default: 0)

  -o, --url=URL                 URL of mining server
  -O, --userpass=U:P            username:password pair for mining server
  -u, --user=USERNAME           username for mining server
  -p, --pass=PASSWORD           password for mining server
  -w, --worker=WORKERNAME       worker name(progpow variants only)
  -r, --retries=N               number of times to retry before switch to backup server (default: 1)
  -R, --retry-pause=N           time to pause between retries (default: 5)
      --max-rejects=N           number of one by one rejects before switch to backup server (default: 5)
      --max-difficulty=N        maximum difficulty to accept from pool(unit: M), otherwise reconnect (default: 0)

      --send-stale              send stale shares
      --diff-factor=N           difficulty factor to use instead of algo default(default: 0)
      --no-extranonce           disable exranonce subscription
      --protocol=PROTOCOL       set stratum protocol(ethproxy, ethstratum, stratum, stratum1, stratum2, ufo, ufo2)

      --watchdog                enable checking how long videocards are running OpenCL kernel(terminate if more than 30 sec.)
      --strategy=N              strategy of feeding videocards with job(default: 0)
      --split-job=N             set amount of gpu's(or threads of it, keep this in mind) solving one job

      --scratchpad-url=URL      where miner can download scratchpad for wildkeccak algo 
      --scratchpad-file=FILE    where to save scratchpad(including file name)
      --scratchpad-safe-update  use safe scratchpad update, can be useful for avoiding N/A on big rigs
      --scratchpad-full-update  use full scratchpad update

      --opencl-platforms=N      list of OpenCL platforms to use(also possible to set amd or nvidia; default: all)
  -d, --opencl-devices=N        list of OpenCL devices to use(default: all)
      --opencl-threads=N        amount of threads per OpenCL device(default: auto)
      --opencl-launch=IxW       list of launch config, intensity and worksize(default: auto)
      --opencl-affinity=N       affine GPU threads to a CPU
      --ptx-version=N           specify what PTX ISA version to use(numbers should be without dot, e.g. 50, 63, 70 and so on)
      --progpow-kernel          depends on drivers values 1 or 2 can provide better hashrate for ProgPow(default: 0)
      --no-dag-split            disable splitting DAG on two parts(have sense only if AMD fix this problem in their drivers)
      --print-platforms         print available OpenCL platforms and exit
      --print-devices           print available OpenCL devices and exit

      --no-adl                  disable monitoring via ADL
      --no-nvml                 disable monitoring via NVML
      --no-sysfs                disable monitoring via sysfs
      --gpu-temp-limit=N        set temperature at which gpu will stop mining(default: 85)
      --gpu-temp-resume=N       set temperature at which gpu will resume mining(default: 60)

      --multiple-instance       allow multiple instances running at one time
      --user-agent=AGENT        set custom user-agent string for pool
  -l, --log-file=FILE           log all output to a file

      --no-color                disable colored output
      --print-time=N            print hashrate report every N seconds
      --print-full              print hashrate for each videocard
      --print-statistics        print additional statistics
      --print-debug             print debug information
      --print-power             print power consumption per GPU chip

      --api-port=N              port for API
      --api-worker-id=ID        custom worker-id for API

      --donate-level=N          donate level(default: 1%%, 1 minute in 100 minutes)
  -h, --help                    display this help and exit
  -V, --version                 output version information and exit
```
