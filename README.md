# VPN Ping Test

I’m currently living way across the world from my friends, but we still want to play video games together. I’ve been trying to reduce my ping.
People claim that some ISPs have poor routing or bottlenecks. Thus, using certain VPN may decrease ping because they have better routing (fewer hops).

This is my attempt to get a somewhat scientific answer to this.

### Methodology

1. Using various VPNs, ping Dota US West server 50 times / batch
2. Run 3 batches
3. Find average

`ping -c 50 [eat.valve.net](http://eat.valve.net/) | tail -1| awk '{print $4}' | cut -d '/' -f 2`

**Note:** In-game ping is around ~30ms lower than ping to `eat.valve.net`, but since all the tests are conducted pinging to the same address, they should be scientific enough

### Findings

Generally no improvements when using VPN. But there are exceptions.

Some servers in Singapore consistently reduce ping. It's possible that NordVPN rents servers from different providers. Some providers for whatever reason perform better.

In most cases, the routing isn't more efficient enough to offset speed lost when using VPN. However, I would note the ones that work well and specifically use them.

### Raw data
I ran 6 batches for some of the servers because the results were surprising.

|      Server      |    Batch 1    | Batch 2 | Batch 3 | **Average** |
|:----------------:|:-------------:|---------|---------|-------------|
| Singapore (#474) |       230.977 | 237.737 | 242.314 | **237.009** |
| Singapore (#473) |       246.381 | 241.881 | 252.337 | **246.866** |
| Singapore (#473) |       250.838 | 244.735 | 245.137 | **246.903** |
| No VPN           |       270.553 | 269.953 | 273.921 | **271.476** |
| No VPN           |       269.837 | 272.797 | 283.273 | **275.302** |
| Thailand (???)   |       292.695 | 273.632 | 262.508 | **276.278** |
| Singapore (#468) |       295.019 | 285.459 | 293.917 | **291.465** |
| Thailand (#15)   |       279.005 | 337.851 | 290.532 | **302.463** |
| Singapore (???)  |       389.582 | 394.291 | 382.683 | **388.852** |
| US Seattle       |       506.796 | 539.124 | 518.467 | **521.462** |
