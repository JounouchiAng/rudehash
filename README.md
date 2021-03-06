# RudeHash

![RudeHash](https://i.imgur.com/kQO48jP.png "RudeHash")

## About

RudeHash is a wrapper script to mine coins and algos on NVIDIA GPUs, written in PowerShell. Features:

* Easy switching between supported pools, coins, algos and miners
* Automatic download of miners
* Auto-restart upon miner crash
* Earnings and profit estimation, using WhatToMine for coins and pool APIs for algos
* Watchdog to restart mining automatically if hash rate is repeatedly zero
* Interactive first run wizard
* Miner status reporting to RudeHash Monitoring and MPHStats

## Installation

* First you need to modify PowerShell's execution policy, because by default it requires code to be digitally signed. Such a certificate costs about $220 per year, which is currently out of the scope of this project. So find your PowerShell shortcut in the Start Menu, right click on it, then _Run as Administrator_. Issue the following command:

~~~~
Set-ExecutionPolicy Unrestricted
~~~~

* Download and install the latest release of:
  * [NVIDIA Driver](https://www.geforce.com/drivers)
  * [PowerShell Core](https://github.com/PowerShell/PowerShell/releases/latest) (x64 MSI recommended)
  * [Visual C++ 2017 x64 Redistributable](https://go.microsoft.com/fwlink/?LinkId=746572) - for **Excavator**
* Download and extract the [latest release of RudeHash](https://rudehash.org/download/).
  * Alternatively, for the latest features and goodies, download the [development version](https://github.com/gradinkov/rudehash/archive/master.zip), but be warned, this code is less stable, and things might get shaky!
* Finally, create a new shortcut: `pwsh.exe -Command C:\path\to\rudehash\rudehash.ps1`, then start it. The first run wizard will guide you through the options.

**Important:** on Suprnova you need to manually create your workers on the pool website beforehand. Make sure to always set the password to **x**, otherwise authentication will fail!

**Important:** certain antivirus software may randomly delete your miner executables. For this reason, it is recommended to add the main `rudehash` folder to your AV's exclusions.

## Support

### Algos

| Algo | Miner |
|---|---|
| Allium | ccminer-allium |
| Ethash | ethminer, Excavator |
| EquiHash | ccminer-tpruvot, DSTM, Excavator, Zec Miner |
| HSR | ccminer-tpruvot, hsrminer-hsr |
| Keccak-C | ccminer-tpruvot |
| Lyra2REv2 | ccminer-klaust, ccminer-palginmod, ccminer-tpruvot, Excavator, vertminer |
| Lyra2Z | ccminer-palginmod, ccminer-tpruvot |
| NeoScrypt | ccminer-klaust, ccminer-palginmod, ccminer-tpruvot, Excavator, hsrminer-neoscrypt |
| Nist5 | ccminer-klaust, ccminer-palginmod, ccminer-tpruvot, Excavator |
| PHI1612 | ccminer-phi, ccminer-tpruvot |
| Polytimos | ccminer-polytimos, ccminer-tpruvot |
| TimeTravel10 | ccminer-tpruvot |
| X16R | ccminer-rvn |
| Xevan | ccminer-xevan |

### Coins

| Symbol | Name | Algo |
|---|---|---|
| BSD | BitSend | Xevan |
| BTCP | Bitcoin Private | EquiHash |
| BTG | Bitcoin Gold | EquiHash |
| BTX | Bitcore | TimeTravel10 |
| BWK | Bulwark | Nist5 |
| CREA | Creativecoin | Keccak-C |
| CRS | Criptoreal | Lyra2Z |
| ETH | Ethereum | Ethash |
| FLM | Folm Coin | PHI1612 |
| FTC | Feathercoin | NeoScrypt |
| GRLC | Garlicoin | Allium |
| HSR | Hshare | HSR |
| IFX | Infinex | Lyra2Z |
| KREDS | Kreds | Lyra2REv2 |
| LUX | LUXCoin | PHI1612 |
| MONA | Monacoin | Lyra2REv2 |
| POLY | Polytimos | Polytimos |
| PYRO | Pyro | Lyra2Z |
| RVN | Ravencoin | X16R |
| TZC | Trezarcoin | NeoScrypt |
| VTC | Vertcoin | Lyra2REv2 |
| XLR | Solaris | Xevan |
| XZC | Zcoin | Lyra2Z |
| ZCL | ZClassic | EquiHash |
| ZEC | Zcash | EquiHash |
| ZEN | ZenCash | EquiHash |

### Pools

| Pool | Mining modes | Payout to | Wallet currencies |
|---|---|---|---|
| MasterHash | coin | Own wallet | Altcoin |
| Mining Pool Hub | algo, coin | Site balance | N/A |
| NiceHash | algo | Own wallet | Bitcoin |
| Poolr | coin | Own wallet | Altcoin |
| Suprnova | coin | Site balance | N/A |
| TheBSODPool | coin | Own wallet | Altcoin |
| Zergpool | algo, coin | Own wallet | Bitcoin, Altcoin |
| zpool | algo | Own wallet | Bitcoin |

* _Own wallet_ means you mine directly to your wallet. In this case, you can specify a username during the First Run Wizard, but it'll be ignored on this specific pool.
* _Site balance_ means you need to register on the pool's website beforehand. The payments will appear under your pool account, and you can specify the payout address on the site, not in RudeHash. In this case, you can specify a wallet address during the First Run Wizard, but it'll be ignored on this specific pool.

The reason why RudeHash still asks for both information during the First Run Wizard is the fact that you may switch to a different pool later on, which does require the other info. It's just an option, and you can skip entering it by simply pressing `Enter` when RudeHash asks for it. Don't worry, if you skip an option that is mandatory for your setup, RudeHash will let you know and ask you to re-enter.

## Monitoring

### RudeHash Monitoring

One option you have is [RudeHash Monitoring](https://rudehash.org/monitor/), which is based on MultiPoolMiner Monitoring. Enter the key generated by RudeHash, and you're ready to go. If you no longer need a worker, just click 'Delete'.

![RHMon](https://i.imgur.com/E3F3WsC.png "RHMon")

### MPHStats

RudeHash also supports [MPHStats](https://miningpoolhubstats.com/user). You can easily identify your individual rigs and their stats, and it works well even if you mix pools.

![MPHStatsPic](https://i.imgur.com/HT3lwHj.png "MPHStatsPic")

### Pool pages

You can also check the pools' corresponding status pages:

* NiceHash: `https://www.nicehash.com/miner/<wallet>`
* Suprnova: `https://<coin>.suprnova.cc/index.php?page=anondashboard&user=<wallet>`
* zpool: `https://zpool.ca/?address=<wallet>`

## FAQ

* Dev fee?

It's 10 minutes **after** every 24 **straight** hours of your mining time (about 0.7% at the very most).
While most other miners makes sure the dev fees are secured first, and only **then** starts mining for the user, RudeHash takes the opposite approach.
Upon start, I get no dev fee, only after the first 24 hours. If you restart RudeHash before any 24 hour run, I get no dev fee.
If the miner crashes before any 24 hour run, I get no dev fee. I only get dev fee once the currently running miner's uptime reaches 24 hours.
I want full transparency on this, thus during dev mining, the progress is shown in the stats, and it's also indicated clearly on all supported monitoring sites.

* What's the point of this tool? I could mine with just a one line batch file!

That's correct. But when you make your choice, you gotta find the stratum URL, the port number, the algo, the corresponding miner, the miner's specific command line arguments... and once you pick a different mining target, you can start it all over again. On all your rigs. This constant messing around quickly becomes a tedious burden.

With RudeHash, you can forget about all of this. Just edit your config: select pool, algo and miner from a pre-defined, well-tested list, enter your credentials, and start mining!

* Why algo/coin mining? I could increase my profits with a sophisticated algo-switching miner!

Algo-switching is based on the idea of relatively short spikes in exchange rates of a particular coin. It kinda worked for a while on NiceHash, where the pool operates on a PPS scheme, _and_ you are credited in BTC within minutes. On other pools you're usually working in a PPLNS or similar scheme, and your earnings are on exchanges for _several hours_. Which totally defeats the whole purpose, i.e. quickly mining and exchanging a coin while it's hot.

In fact, not even NiceHash' algo-switching works currently, because buyers are constantly manipulating the market with cancelled orders, and so most people end up disabling all but 1 or 2 algos.

* AMD support?

Actually, I'm not certain that RudeHash does _not_ work with AMD hardware. I just don't test it _at all_, because I have zero AMD hardware at hand, and by the look of things it will stay that way.
