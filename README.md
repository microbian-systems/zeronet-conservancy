# zeronet-conservancy

This is a minimalist conservative fork of [ZeroNet](https://github.com/HelloZeroNet/ZeroNet) with tor onion-v3 support (and perhaps more essential/security fixes in the future)

## Why fork?

We need a fork that works with onion-v3 and doesn't depend on trust to one or two people. We need it now. This fork implements minimal changes to [ZeroNet/py3](https://github.com/HelloZeroNet/ZeroNet/tree/py3) branch which are easy to audit yourself.

This fork is intended as temporary measure and will possibly stop being maintained after its original author established there is an alternative active trust-worthy fork.

## Why 0net?

* We believe in open, free, and uncensored networks and communication.
* No single point of failure: Site remains online so long as at least 1 peer is
  serving it.
* No hosting costs: Sites are served by visitors.
* Impossible to shut down: It's nowhere because it's everywhere.
* Fast and works offline: You can access the site even if Internet is
  unavailable.


## Features
 * Real-time updated sites
 * Clone websites in one click
 * Password-less authorization using private/public keys
 * Built-in SQL server with P2P data synchronization: allows easier dynamic site development
 * Anonymity: Tor network support with .onion hidden services (including onion-v3 support)
 * TLS encrypted connections (through clearnet)
 * Automatic uPnP port opening (if opted in)
 * Plugin for multiuser (openproxy) support
 * Works with any browser/OS


## How does it work?

* After starting `zeronet.py` you will be able to visit zeronet sites using
  `http://127.0.0.1:43110/{zeronet_address}` (eg.
  `http://127.0.0.1:43110/1HeLLo4uzjaLetFx6NH3PMwFP3qbRbTf3D`).
* When you visit a new zeronet site, it tries to find peers using the BitTorrent
  network so it can download the site files (html, css, js...) from them.
* Each visited site is also served by you.
* Every site contains a `content.json` file which holds all other files in a sha512 hash
  and a signature generated using the site's private key.
* If the site owner (who has the private key for the site address) modifies the
  site, then he/she signs the new `content.json` and publishes it to the peers.
  Afterwards, the peers verify the `content.json` integrity (using the
  signature), they download the modified files and publish the new content to
  other peers.

Following links relate to original ZeroNet:

- [Slideshow about ZeroNet cryptography, site updates, multi-user sites »](https://docs.google.com/presentation/d/1_2qK1IuOKJ51pgBvllZ9Yu7Au2l551t3XBgyTSvilew/pub?start=false&loop=false&delayms=3000)
- [Frequently asked questions »](https://zeronet.io/docs/faq/)
- [ZeroNet Developer Documentation »](https://zeronet.io/docs/site_development/getting_started/)


## Screenshots

![Screenshot](https://i.imgur.com/H60OAHY.png)
![ZeroTalk](https://zeronet.io/docs/img/zerotalk.png)

#### [More screenshots in ZeroNet docs »](https://zeronet.io/docs/using_zeronet/sample_sites/)


## How to join

### Install from source (recommended)

#### System dependencies

##### Generic unix-like

Install autoconf and other basic development tools, python3 and pip.

##### Apt-based (debian, ubuntu, etc)
 - `sudo apt update`
 - `sudo apt install python3-pip python3-venv`

##### Android/Termux
 - install [Termux](https://termux.com/)
 - in Termux install via `pkg install <package-names>`
 - `pkg update`
 - `pkg install python automake autoconf-dev git` (TODO: check fresh installation whether there are more dependencies to install)

#### Building python dependencies & running
 - clone this repo (NOTE: on Android/Termux you should clone it into "home" folder of Termux, because virtual environment cannot live in `storage/`)
 - `python3 -m venv venv` (make python virtual environment, the last `venv` is just a name, if you use different you should replace it in later commands)
 - `source venv/bin/activate` (activate environment)
 - `python3 -m pip install -r requirements.txt` (install dependencies)
 - `python3 zeronet.py` (**run zeronet-conservancy!**)
 - open the landing page in your browser by navigating to: http://127.0.0.1:43110/
 - to start it again from fresh terminal, you need to navigate to repo directory and:
 - `source venv/bin/activate`
 - `python3 zeronet.py`

## Current limitations

* File transactions are not compressed
* No private sites
* No DHT support
* Centralized elements like zeroid
* No reliable spam protection


## How can I create a ZeroNet site?

 * Click on **⋮** > **"Create new, empty site"** menu item on the site [ZeroHello](http://127.0.0.1:43110/1HeLLo4uzjaLetFx6NH3PMwFP3qbRbTf3D).
 * You will be **redirected** to a completely new site that is only modifiable by you!
 * You can find and modify your site's content in **data/[yoursiteaddress]** directory
 * After the modifications open your site, drag the topright "0" button to the left, then press **sign** and **publish** buttons on the bottom

Next steps: [ZeroNet Developer Documentation](https://zeronet.io/docs/site_development/getting_started/)

## Help this project stay alive

### Become a maintainer

We need more maintainers! Become one today! Seriously, there's not going to be
that much new code to audit and auditing new code is the only requirement.

### Use it and spread the word

Make sure to tell people why do you use 0net and this fork in particular! People
need to know their alternatives.

### Financially support maintainers

Currently the only maintainer of this fork is @caryoscelus. You can see ways to
donate to them on https://caryoscelus.github.io/donate/

If you want to make sure your donation is recognized as donation for this
project, there is a dedicated bitcoin address for that, too:
1Kjuw3reZvxRVNs27Gen7jPJYCn6LY7Fg6

If you want to donate in a different way, feel free to contact maintainer or
create an issue
