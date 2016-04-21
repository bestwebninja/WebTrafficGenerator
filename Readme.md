Web Traffic Generator
=====================

## 1. Description of the software
This tool takes as input a list of web pages and visits them by means of Selenium Web Browser (relying on Firefox).
It produces as output the HARs generated by each page.
HAR is the [HTTP Archive](http://www.softwareishard.com/blog/har-12-spec/), a JSON data structure containing 
information and performance statistics about the webpage download.

For information about this Readme file and this tool please write to [martino.trevisan@polito.it](mailto:martino.trevisan@polito.it)

## 2. Dependencies
You must install Selenium python3 package:
```
sudo pip3 install selenium
```
If you don't have pip3 istalled, you can do it following 
[this](http://stackoverflow.com/questions/6587507/how-to-install-pip-with-python-3) link.

Then, you must install BrowserMob Proxy, available at [this](https://github.com/lightbody/browsermob-proxy/releases) link.
Please download and decompress it.
You must set the location of the BrowserMob Proxy executable in the enviroment variable BROWSERMOBPROXY_BIN;
for example if you decompress in the current folder, type:
```
export BROWSERMOBPROXY_BIN=./browsermob-proxy-2.1.0-beta-5/bin/browsermob-proxy
```
Finally, please install BrowserMob Proxy python3 package
```
sudo pip3 install browsermob-proxy
```

## 3. Usage
To run this tool, you must execute this command line:
```
web_traffic_generator.py [-h] [-b max_backoff] [-t timeout] [--headers]
                                [-s start_page]
                                input_file output_file
```

positional arguments:
*  `input_file`            File where are stored the pages, one per row
*  `output_file`           Output file where HAR structures are saved, one per row

optional arguments:
 *  `-h, --help`            show this help message and exit
 *  `-b max_backoff, --backoff max_backoff`
                        Use real backoff with maximum <max_backoff> threshold
 *  `-t timeout, --timeout timeout`
                        Timeout in seconds after declaring failed a visit.
                        Default is 30.

*  `--headers `      Save headers of HTTP requests and responses in Har
                        structs (e.g., to find referer field)

*  `-s start_page, --start_page start_page`
                        For internal usage, do not use


## 4. Output format
This tool creates an output file where it stores the output HAR of each requested URL.
For each input URL, the corresponding HAR is reported, one line for each HAR structure.
Some HAR could be missing, due to failed downloads (very slow pages, crashed browser ecc...)


