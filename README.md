# MITM Adblock

An adblocker that runs as a proxy server! (And works on HTTPS connections.)

Use this to block ads on your mobile device, or just monitor its traffic.

**DO NOT MERGE** - this branch is being used for subtree integration

## Installation

 1. Install [mitmproxy](http://mitmproxy.org/)
 2. Install required python modules:

```
$ pip install 'Cython>=0.29.19,<1.0'  # for pyre2
$ pip install -r requirements.txt
```

 3. Run `./bin/update-blocklists.sh` to download some blocklists
 4. Run `./bin/proxy-runner.sh` to start the proxy server on port 8080 (or run `./bin/proxy-runner.sh -c` for a curses interface which lets you inspect the requests/responses, or run `./bin/proxy-runner.sh -d` to dump all flows to the 'flows/' directory)
 5. Do a quick test to make sure it's working: `curl --proxy localhost:8080 -L -k https://slashdot.org/`
 6. Setup your browser/phone to use `localhost:8080` or `lan-ip-address:8080` as an HTTP proxy server; then, visit http://mitm.it on that device to install the MITM SSL certificate so that your machine won't throw security warnings whenever the proxy server intercepts your secure connections.
 7. Alternately, you can use `./bin/install-cert.sh` to install the proxy-generated cert; see the script for details.

If you'd like to change any of the mitmproxy settings (like port, and where/whether it logs your connections), edit the `proxy-runner.sh` script.

