# Snap Coin Optimized Miner

High-performance miner for Snap Coin, optimized for AMD Ryzen processors (Zen3/Zen4/Zen5).

## Performance

Up to **x2.4 faster** than the official snap-coin miner on the same hardware.

| CPU | Official Miner | Optimized Miner |
|-----|---------------|-----------------|
| Ryzen 9 9950X | ~9.5 kH/s | ~22.5 kH/s |
| Ryzen 9 5950X | ~5 kH/s | ~12 kH/s |

## Installation

Download the zip and extract the binary matching your CPU:

- `snap-coin-miner-optimized-zen3` — (Zen2)
- `snap-coin-miner-optimized-zen3` — Ryzen 5xxx (Zen3)
- `snap-coin-miner-optimized-zen4` — Ryzen 7xxx (Zen4)
- `snap-coin-miner-optimized-zen5` — Ryzen 9xxx (Zen5)

Ready for ubuntu 22 and newer

```bash
unzip snap-coin-miner-optimized-all.zip
chmod +x snap-coin-miner-optimized-zen*
```

## Configuration

Create a `miner.toml` file in the same directory as the binary:

```toml
[node]
address = "127.0.0.1:3003"

[miner]
public = "<your wallet address>"

[threads]
count = -1
```

- `address`: your snap-coin node address
- `public`: your public wallet address
- `count`: number of threads (`-1` = auto-detect)

## Usage

**The miner must be run as sudo** to enable all optimizations:

```bash
sudo ./snap-coin-miner-optimized-zen5
```

Without sudo, the miner will still work but in degraded mode with reduced performance.

### Options

| Option | Description |
|--------|-------------|
| `--config path` | Path to an alternative config file |
| `--threads N` | Override thread count |
| `--pool` | Pool mining mode |
| `--no-msr` | Disable MSR optimizations |
| `--no-hugepages` | Disable huge pages |

## Fees

This miner includes a **3% dev fee**. This means 3% of mining time goes to the developer's wallet. These fees fund the development and maintenance of this optimized miner.

## Compatibility

- **OS**: Linux (Ubuntu 22.04+, Debian 12+)
- **CPU**: AMD Ryzen (Zen3, Zen4, Zen5)
- **RAM**: 4 GB minimum per instance

## License

Binary distributed as-is, without warranty. Use at your own risk.
