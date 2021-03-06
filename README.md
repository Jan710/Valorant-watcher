
<h1 align="center">Valorant watcher</h1>
<p align="center"> I spent two days watching Valorant streams to get a drop. I got bored...</p>
<p align="center">
<img alt="GitHub package.json version" src="https://img.shields.io/github/package-json/v/D3vl0per/Valorant-watcher"> <img alt="GitHub" src="https://img.shields.io/github/repo-size/D3vl0per/Valorant-watcher"> <img alt="GitHub repo size" src="https://img.shields.io/github/license/D3vl0per/Valorant-watcher"> <img alt="GitHub issues" src="https://img.shields.io/github/issues/D3vl0per/Valorant-watcher"> <a href="https://asciinema.org/a/E4bhVEjYsiZ8fLHqIuVXOiBGb" target="_blank"> <img src="https://asciinema.org/a/E4bhVEjYsiZ8fLHqIuVXOiBGb.svg" /></a>
</p>



## Requirements

 - Windows or Linux OS
 - Network connection (So obvious...)
 - [Nodejs](https://nodejs.org/en/download/) and [NPM](https://www.npmjs.com/get-npm)
 - [screen](https://linuxize.com/post/how-to-use-linux-screen/) (Optional, just for background running)


## Installation

1. Login your twitch account
2. Open inspector(F12 or Ctlr+Shift+I) on main site
3. Find stored cookie section
4. Copy auth-token and the token's expires date
5. Clone this repo
6. Install the dependencies with `npm install`
7. After start the program with `npm start`

## Docker
<p align="center">
<img alt="Docker Cloud Build Status" src="https://img.shields.io/docker/cloud/build/d3vm/valorant-watcher"> <img alt="Docker Image Version (latest by date)" src="https://img.shields.io/docker/v/d3vm/valorant-watcher"> <img alt="Docker Pulls" src="https://img.shields.io/docker/pulls/d3vm/valorant-watcher"> <img alt="Docker Image Size (latest by date)" src="https://img.shields.io/docker/image-size/d3vm/valorant-watcher">
</p>

### Requirements
- [Docker](https://docs.docker.com/get-docker/)
- [Docker compose](https://docs.docker.com/compose/install/)
### Useage
1. Download docker-compose-example.yml
2. Rename docker-compose.yml
3. Replace environments
4. Run `docker-compose up -d`
## Dependencies
<p align="center">
<img alt="GitHub package.json dependency version (subfolder of monorepo)" src="https://img.shields.io/github/package-json/dependency-version/D3vl0per/Valorant-watcher/puppeteer"> <img alt="GitHub package.json dependency version (subfolder of monorepo)" src="https://img.shields.io/github/package-json/dependency-version/D3vl0per/Valorant-watcher/chrome-launcher"> <img alt="GitHub package.json dependency version (subfolder of monorepo)" src="https://img.shields.io/github/package-json/dependency-version/D3vl0per/Valorant-watcher/cheerio"> <img alt="GitHub package.json dependency version (subfolder of monorepo)" src="https://img.shields.io/github/package-json/dependency-version/D3vl0per/Valorant-watcher/inquirer"> <img alt="GitHub package.json dependency version (subfolder of monorepo)" src="https://img.shields.io/github/package-json/dependency-version/D3vl0per/Valorant-watcher/dotenv">
</p>

## Troubleshooting

### How token does it look like?
auth-token: `rxk38rh5qtyw95fkvm7kgfceh4mh6u`  
expire date: `2020-04-13T22:22:22.010Z`  
___

### Setting Up Chrome Linux Sandbox

In order to protect the host environment from untrusted web content, Chrome uses [multiple layers of sandboxing](https://chromium.googlesource.com/chromium/src/+/HEAD/docs/linux_sandboxing.md). For this to work properly,
the host should be configured first. If there's no good sandbox for Chrome to use, it will crash
with the error `No usable sandbox!`.

If you **absolutely trust** the content you open in Chrome, you can launch Chrome
with the `--no-sandbox` argument:

```js
const browser = await puppeteer.launch({args: ['--no-sandbox', '--disable-setuid-sandbox']});
```

> **NOTE**: Running without a sandbox is **strongly discouraged**. Consider configuring a sandbox instead.

There are 2 ways to configure a sandbox in Chromium.

### [recommended] Enable [user namespace cloning](http://man7.org/linux/man-pages/man7/user_namespaces.7.html)

User namespace cloning is only supported by modern kernels. Unprivileged user namespaces are generally fine to enable,
but in some cases they open up more kernel attack surface for (unsandboxed) non-root processes to elevate to
kernel privileges.

```bash
sudo sysctl -w kernel.unprivileged_userns_clone=1
```

### [alternative] Setup [setuid sandbox](https://chromium.googlesource.com/chromium/src/+/HEAD/docs/linux_suid_sandbox_development.md)

The setuid sandbox comes as a standalone executable and is located next to the Chromium that Puppeteer downloads. It is
fine to re-use the same sandbox executable for different Chromium versions, so the following could be
done only once per host environment:

```bash
# cd to the downloaded instance
cd <project-dir-path>/node_modules/puppeteer/.local-chromium/linux-<revision>/chrome-linux/
sudo chown root:root chrome_sandbox
sudo chmod 4755 chrome_sandbox
# copy sandbox executable to a shared location
sudo cp -p chrome_sandbox /usr/local/sbin/chrome-devel-sandbox
# export CHROME_DEVEL_SANDBOX env variable
export CHROME_DEVEL_SANDBOX=/usr/local/sbin/chrome-devel-sandbox
```

You might want to export the `CHROME_DEVEL_SANDBOX` env variable by default. In this case, add the following to the `~/.bashrc`
or `.zshenv`:

```bash
export CHROME_DEVEL_SANDBOX=/usr/local/sbin/chrome-devel-sandbox
```

By puppeteer wiki: [https://github.com/puppeteer/puppeteer/blob/master/docs/troubleshooting.md](https://github.com/puppeteer/puppeteer/blob/master/docs/troubleshooting.md)
___
### streamers.json is empty?

Try to again with higher delay.
Default delay:
```javascript
const scrollDelay = 2000;
```
___
### Something went wrong?
Try to non-headless mode. Edit headless value to `true`, like this:
```javascript
const browser = await puppeteer.launch({ headless: true , ignoreDefaultArgs: ['--mute-audio']});
```
## Support
 - Keybase at [https://keybase.io/d3v_](https://keybase.io/d3v_) ![Keybase PGP](https://img.shields.io/keybase/pgp/d3v_)
 - Website at [https://zsmark.dev](https://zsmark.dev)
## Donations
[![Buy Me A Coffee](https://www.buymeacoffee.com/assets/img/custom_images/orange_img.png)](https://www.buymeacoffee.com/D3v)

## Disclaimer
These codes for educational and research purposes only.
Do not attempt to violate the law with anything contained here.
I will not be responsible for your any illegal actions.
