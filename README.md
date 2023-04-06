## testnet.kira.network

Release workflow of Notion pages to IPFS

### Overview

1. Our [custom docker base-image](https://github.com/KiraCore/docker) with preinstalled chromedriver is launched
2. Python [Loconotion](https://github.com/leoncvlt/loconotion) tool and its dependencies are installed
3. Loconotion is configured using [config.toml](./config.toml) to scrape public Notion page and save it as HTML in the `./dist/notion` folder
4. Our [custom ipfs-api](https://github.com/KiraCore/tools/tree/main/ipfs-api) tool communicates with pinata to pin the `./dist/notion` folder
5. The `./dist/notion` folder is pushed to the dedicated repository with a prefix `<branch>-release` alongside CID hash in ./ipfs-cid.txt
6. A simple HTML page can now use `<branch>-release/ipfs-cid.txt` to locate the IPFS page and redirect users via much simpler DNS name

### How to use this ?

* Make a commit to `dev` repository
* Push changes
* Await github actions to finalize
* Notion gets deployed to IPFS : ) 
* PR is automatically raised to `master` alongside links to IPFS gateway
* If you are satisfied with the release merge the PR