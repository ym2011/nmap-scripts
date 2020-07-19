# nmap_vulners

[![Current Release](https://img.shields.io/github/release/vulnersCom/nmap-vulners.svg "Current Release")](https://github.com/vulnersCom/nmap-vulners/releases/latest)
[![Downloads](https://img.shields.io/github/downloads/vulnersCom/nmap-vulners/total.svg "Downloads")](https://github.com/vulnersCom/nmap-vulners/releases) [![PayPal](https://img.shields.io/badge/donate-PayPal-green.svg)](https://paypal.me/videns)

## Description

NSE script using some well-known service to provide info on vulnerabilities.

![Result example](example.png)

## Dependencies:
    nmap libraries:
        http
        json
        string
    http-vulners-regex

The only thing you should always keep in mind is that the script depends on having software versions at hand, so it only works with -sV flag.

**NB:** Now it can actually be run without -sV flag if http-vulners-regex script is run as well.

## Installation
    locate where your nmap scripts are located on your system
        for *nix system it might be  ~/.nmap/scripts/ or $NMAPDIR
        for Mac it might be /usr/local/Cellar/nmap/<version>/share/nmap/scripts/
        for Windows it might be C:\Program Files (x86)\Nmap\scripts
    copy the provided script (vulners.nse) into that directory
    run *nmap --script-updatedb* to update the nmap script DB 

## Usage
    Use it as straightforward as you can:
        nmap -sV --script vulners [--script-args mincvss=<arg_val>] <target>
        
It is KISS after all.

# http-vulners-regex

## Description

NSE script to scan HTTP responses and identify CPEs for the mentioned software. It can therefore boost the efficiency of the main vulners script.

![Result example](simple_regex_example.png)
Or with the paths:
![Result example](paths_regex_example.png)

## Dependencies
    nmap libraries:
        http
        json
        string
        stdnse
        shortport
        table

## Installation
    locate where nmap is located on your system
        for *nix system it might be  ~/.nmap/ or $NMAPDIR
        for Mac it might be /usr/local/Cellar/nmap/<version>/share/nmap/
        for Windows it might be C:\Program Files (x86)\Nmap\
    copy the provided script (http-vulners-regex.nse) into <nmap_dir>/scripts/
    copy the provided json with the regexes to <nmap_dir>/nselib/data/
    copy the provided txt file with the default paths to <nmap_dir>/nselib/data/
        note that you can specify your own file via command line
    run *nmap --script-updatedb* to update the nmap script DB 

## Usage
    As a usual NSE script:
        nmap --script http-vulners-regex.nse [--script-args paths={"/"}] <target> 
