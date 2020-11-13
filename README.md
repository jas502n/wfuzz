<img src="https://github.com/xmendez/wfuzz/blob/master/docs/_static/logo/wfuzz_letters.svg" width="500">

[![Build Status](https://travis-ci.org/xmendez/wfuzz.svg?branch=master)](https://travis-ci.org/xmendez/wfuzz)
<a href="https://pypi.python.org/pypi/wfuzz"><img src="https://img.shields.io/pypi/v/wfuzz.svg"></a>
<a href="https://pypi.python.org/pypi/wfuzz"><img src="https://img.shields.io/pypi/dm/wfuzz"></a>
<a href="https://pypi.python.org/pypi/wfuzz"><img src="https://img.shields.io/pypi/pyversions/wfuzz.svg"></a>
<a href="https://codecov.io/github/xmendez/wfuzz"><img src="https://codecov.io/github/xmendez/wfuzz/coverage.svg?branch=master"></a>

## Example
```
╭─root@Jas502n ~/github/wfuzz ‹master›
╰─# wfuzz

Warning: Pycurl is not compiled against Openssl. Wfuzz might not work correctly when fuzzing SSL sites. Check Wfuzz's documentation for more information.

********************************************************
* Wfuzz 2.4.5 - The Web Fuzzer                         *
*                                                      *
* Version up to 1.4c coded by:                         *
* Christian Martorella (cmartorella@edge-security.com) *
* Carlos del ojo (deepbit@gmail.com)                   *
*                                                      *
* Version 1.4d to 2.4.5 coded by:                      *
* Xavier Mendez (xmendez@edge-security.com)            *
********************************************************

Usage:	wfuzz [options] -z payload,params <url>

	FUZZ, ..., FUZnZ  wherever you put these keywords wfuzz will replace them with the values of the specified payload.
	FUZZ{baseline_value} FUZZ will be replaced by baseline_value. It will be the first request performed and could be used as a base for filtering.


Examples:
	wfuzz -c -z file,users.txt -z file,pass.txt --sc 200 http://www.site.com/log.asp?user=FUZZ&pass=FUZ2Z
	wfuzz -c -z range,1-10 --hc=BBB http://www.site.com/FUZZ{something not there}
	wfuzz --script=robots -z list,robots.txt http://www.webscantest.com/FUZZ

Type wfuzz -h for further information or --help for advanced usage.

```

## help

```
╭─root@Jas502n ~/github/wfuzz ‹master›
╰─# wfuzz --help                                                                                                                                                                                                          1 ↵

Warning: Pycurl is not compiled against Openssl. Wfuzz might not work correctly when fuzzing SSL sites. Check Wfuzz's documentation for more information.

********************************************************
* Wfuzz 2.4.5 - The Web Fuzzer                         *
*                                                      *
* Version up to 1.4c coded by:                         *
* Christian Martorella (cmartorella@edge-security.com) *
* Carlos del ojo (deepbit@gmail.com)                   *
*                                                      *
* Version 1.4d to 2.4.5 coded by:                      *
* Xavier Mendez (xmendez@edge-security.com)            *
********************************************************

Usage:	wfuzz [options] -z payload,params <url>

	FUZZ, ..., FUZnZ  wherever you put these keywords wfuzz will replace them with the values of the specified payload.
	FUZZ{baseline_value} FUZZ will be replaced by baseline_value. It will be the first request performed and could be used as a base for filtering.


Options:
	-h/--help                 : This help
	--help                    : Advanced help
	--filter-help             : Filter language specification
	--version                 : Wfuzz version details
	-e <type>                 : List of available encoders/payloads/iterators/printers/scripts

	--recipe <filename>       : Reads options from a recipe. Repeat for various recipes.
	--dump-recipe <filename>  : Prints current options as a recipe
	--oF <filename>           : Saves fuzz results to a file. These can be consumed later using the wfuzz payload.

	-c                        : Output with colors
	-v                        : Verbose information.
	-f filename,printer       : Store results in the output file using the specified printer (raw printer if omitted).
	-o printer                : Show results using the specified printer.
	--interact                : (beta) If selected,all key presses are captured. This allows you to interact with the program.
	--dry-run                 : Print the results of applying the requests without actually making any HTTP request.
	--prev                    : Print the previous HTTP requests (only when using payloads generating fuzzresults)
	--efield <expr>           : Show the specified language expression together with the current payload
	--field <expr>            : Do not show the payload but only the specified language expression

	-p addr                   : Use Proxy in format ip:port:type. Repeat option for using various proxies.
	                            Where type could be SOCKS4,SOCKS5 or HTTP if omitted.

	-t N                      : Specify the number of concurrent connections (10 default)
	-s N                      : Specify time delay between requests (0 default)
	-R depth                  : Recursive path discovery being depth the maximum recursion level.
	-L,--follow               : Follow HTTP redirections
	--ip host:port            : Specify an IP to connect to instead of the URL's host in the format ip:port
	-Z                        : Scan mode (Connection errors will be ignored).
	--req-delay N             : Sets the maximum time in seconds the request is allowed to take (CURLOPT_TIMEOUT). Default 90.
	--conn-delay N            : Sets the maximum time in seconds the connection phase to the server to take (CURLOPT_CONNECTTIMEOUT). Default 90.

	-A, --AA, --AAA           : Alias for --script=default,verbose,discovery -v -c
	--no-cache                : Disable plugins cache. Every request will be scanned.
	--script=                 : Equivalent to --script=default
	--script=<plugins>        : Runs script's scan. <plugins> is a comma separated list of plugin-files or plugin-categories
	--script-help=<plugins>   : Show help about scripts.
	--script-args n1=v1,...   : Provide arguments to scripts. ie. --script-args grep.regex="<A href=\"(.*?)\">"

	-u url                    : Specify a URL for the request.
	-m iterator               : Specify an iterator for combining payloads (product by default)
	-z payload                : Specify a payload for each FUZZ keyword used in the form of name[,parameter][,encoder].
	                            A list of encoders can be used, ie. md5-sha1. Encoders can be chained, ie. md5@sha1.
	                            Encoders category can be used. ie. url
	                            Use help as a payload to show payload plugin's details (you can filter using --slice)
	--zP <params>             : Arguments for the specified payload (it must be preceded by -z or -w).
	--zD <default>            : Default parameter for the specified payload (it must be preceded by -z or -w).
	--zE <encoder>            : Encoder for the specified payload (it must be preceded by -z or -w).
	--slice <filter>          : Filter payload's elements using the specified expression. It must be preceded by -z.
	-w wordlist               : Specify a wordlist file (alias for -z file,wordlist).
	-V alltype                : All parameters bruteforcing (allvars and allpost). No need for FUZZ keyword.
	-X method                 : Specify an HTTP method for the request, ie. HEAD or FUZZ

	-b cookie                 : Specify a cookie for the requests. Repeat option for various cookies.
	-d postdata               : Use post data (ex: "id=FUZZ&catalogue=1")
	-H header                 : Use header (ex:"Cookie:id=1312321&user=FUZZ"). Repeat option for various headers.
	--basic/ntlm/digest auth  : in format "user:pass" or "FUZZ:FUZZ" or "domain\FUZ2Z:FUZZ"

	--hc/hl/hw/hh N[,N]+      : Hide responses with the specified code/lines/words/chars (Use BBB for taking values from baseline)
	--sc/sl/sw/sh N[,N]+      : Show responses with the specified code/lines/words/chars (Use BBB for taking values from baseline)
	--ss/hs regex             : Show/hide responses with the specified regex within the content
	--filter <filter>         : Show/hide responses using the specified filter expression (Use BBB for taking values from baseline)
	--prefilter <filter>      : Filter items before fuzzing using the specified expression.

╭─root@Jas502n ~/github/wfuzz ‹master›
╰─#
```

# Wfuzz - The Web Fuzzer

`pip install pycurl`

Wfuzz has been created to facilitate the task in web applications assessments and it is based on a simple concept: it replaces any reference to the FUZZ keyword by the value of a given payload.

A payload in Wfuzz is a source of data.

This simple concept allows any input to be injected in any field of an HTTP request, allowing to perform complex web security attacks in different web application components such as: parameters, authentication, forms, directories/files, headers, etc.

Wfuzz is more than a web content scanner:

* Wfuzz could help you to secure your web applications by finding and exploiting web application vulnerabilities. Wfuzz’s web application vulnerability scanner is supported by plugins.

* Wfuzz is a completely modular framework and makes it easy for even the newest of Python developers to contribute. Building plugins is simple and takes little more than a few minutes.

* Wfuzz exposes a simple language interface to the previous HTTP requests/responses performed using Wfuzz or other tools, such as Burp. This allows you to perform manual and semi-automatic tests with full context and understanding of your actions, without relying on a web application scanner underlying implementation.


It was created to facilitate the task in web applications assessments, it's a tool by pentesters for pentesters ;)

## Installation 

To install WFuzz, simply use pip:

```
pip install wfuzz
```

To run Wfuzz from a docker image, run:

```
$ docker run -v $(pwd)/wordlist:/wordlist/ -it ghcr.io/xmendez/wfuzz wfuzz
```

## Documentation

Documentation is available at http://wfuzz.readthedocs.io

## Download 

Check github releases. Latest is available at https://github.com/xmendez/wfuzz/releases/latest
