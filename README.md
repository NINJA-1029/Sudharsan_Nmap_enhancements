# Nmap NSE originals and enhancements

The two original Nmap scripts and their enhanced versions are stored as separate files.

| Original script | Enhanced script |
| --- | --- |
| [banner.nse](banner.nse) | [enhanced_sequential-honeypot-detector.nse](enhanced_sequential-honeypot-detector.nse) |
| [qscan.nse](qscan.nse) | [enhanced_port-flap-detector.nse](enhanced_port-flap-detector.nse) |

The original files are unmodified copies bundled with Nmap 7.99, the version used as the basis for these enhancements. Official documentation and source links: [banner](https://nmap.org/nsedoc/scripts/banner.html) and [qscan](https://nmap.org/nsedoc/scripts/qscan.html). Their author and license notices are retained. The enhanced scripts identify their original authors and SUDHARSAN M as the enhancement author.

The banner enhancement compares service banners across ports. The qscan enhancement adds TCP connection reliability sampling alongside timing analysis.

## Running the enhanced scripts

From this directory, using your own local test services:

```sh
nmap -sT -p 8000-8004 --script ./enhanced_sequential-honeypot-detector.nse --script-args enhanced_sequential-honeypot-detector.sample_size=5 127.0.0.1
nmap -sT -p 8000 --script ./enhanced_port-flap-detector.nse --script-args enhanced_port-flap-detector.mode=connect 127.0.0.1
```

The enhanced filenames now start with `enhanced_`. Because their argument names use Nmap's `SCRIPT_NAME`, use the new filename stem as the argument prefix. The qscan enhancement also retains its existing legacy qscan-prefixed and unprefixed timing arguments. Timing mode requires raw-packet privileges and IPv4.
