The crash is caused by huge pages not being properly distributed across NUMA nodes on your EPYC processor. Here's how to fix it:

**Step 1: Check how many NUMA nodes you have**

```bash
ls /sys/devices/system/node/
```

You'll see something like `node0 node1` (or more).

**Step 2: Allocate huge pages on each NUMA node**

Run this for each node:

```bash
echo 1280 | sudo tee /sys/devices/system/node/node0/hugepages/hugepages-2048kB/nr_hugepages
echo 1280 | sudo tee /sys/devices/system/node/node1/hugepages/hugepages-2048kB/nr_hugepages
```

If you have more nodes (node2, node3...), do the same for each one.

**Step 3: Launch the miner normally**

```bash
sudo ./snap-coin-miner-optimized-zen2 (or zen3,4,5 depending on your cpu)
```

No need for `--no-hugepages` anymore. You should get better performance with huge pages enabled.

**To make it persistent across reboots**, add the echo commands to `/etc/rc.local` or create a systemd service.


NOTE:
Some users reported better performance by setting the thread count manually in miner.toml instead of using -1 (auto-detect).

Try setting the exact number of threads in your miner.toml:

[threads]
count = 192

(replace 192 with your actual thread count from nproc)
