# Assest-Discovery-Oneliner
This is made my be to do fast assest discovery. You need to use install some basic tools that are open source. This  is written for very personal, so change according to your need.  

### Related domain

`cat domains.txt | haktrails associateddomains`

host url.com

whatweb url.com

1. [https://bgp.he.net/](https://bgp.he.net/)  2. `whois -h whois.radb.net -- '-i origin` [AS13414](https://bgp.he.net/AS13414)`' | grep -Eo "([0-9.]+){4}/[0-9]+" | head`

### Subdomain

subfinder -d google.com | httpx | tee domains1.txt

`assetfinder [google.com](http://google.com)` | httpx | tee domain.txt

 `cat domains.txt | haktrails subdomains`

`massdns -r lists/resolvers.txt -t AAAA domains.txt > results.txt`

`amass enum --passive -d <DOMAIN>`

`python altdns.py -i input_domains.txt -o ./output/path -w altdns/words.txt`

gospider -d 0 -s "[https://site.com](https://site.com/)" -c 5 -t 100 -d 5 --blacklist jpg,jpeg,gif,css,tif,tiff,png,ttf,woff,woff2,ico,pdf,svg,txt | grep -Eo '(http|https)://[^/"]+' | anew

curl -s "[https://crt.sh/?q=%25.att.com&output=json](https://crt.sh/?q=%25.att.com&output=json)" | jq -r '.[].name_value' | sed 's/\*\.//g' | httpx -title -silent | anew

### URLS

`assetfinder google.com | hakrawler -plain | hakcheckurl | grep -v 404` | tee live_urls.txt

waybackurls [https://twitter.com](https://twitter.com/)

[https://web.archive.org/cdx/search/cdx?url=*.coindcx.com/*&output=text&fl=original&collapse=urlkey](https://web.archive.org/cdx/search/cdx?url=*.coindcx.com/*&output=text&fl=original&collapse=urlkey)

gospider -s "[https://coindcx.com/](https://coindcx.com/)" -o output -c 10 -d 1 | gf sqli

### Wordlist Gen

cat hosts.txt | waybackurls | wordlistgen

cat hosts.txt | wordlistgen -qv > urlComponents.txt

### JavaScript Parser

python [linkfinder.py](http://linkfinder.py/) -i [https://coindcx.com/2-es2015.04cd7d3b5decbdd78e65.js](https://coindcx.com/2-es2015.04cd7d3b5decbdd78e65.js)

### End point discovery

`echo https://google.com | hakrawler`

`cat urls.txt | hakrawler -proxy http://localhost:8080`

feroxbuster -u [https://seek.com.au](https://seek.com.au/)

 

### Directory brute forcing

wfuzz -w wordlist/general/common.txt --hc 404 [http://testphp.vulnweb.com/FUZZ](http://testphp.vulnweb.com/FUZZ)

ffuf -w wordlist -u [https://domain.com/](https://fuzz.findchips.com/signin/)FUZZ/ -mc 200

`python3 dirsearch.py -e php,html,js -u https://target -w /path/to/wordlist` `-t 20`

python3 [dirsearch.py](http://dirsearch.py/) -e php,html,js -u [https://target](https://target/) -r --recursion-depth 3 --recursion-status 200-399 `-t 20`

python3 [dirsearch.py](http://dirsearch.py/) -e php,html,js -u [https://target](https://target/) -r --exclude-subdirs image/,media/,css/ `-t 20`

### Shodan recon

[https://twitter.com/AseemShrey/status/1508059759491964928](https://twitter.com/AseemShrey/status/1508059759491964928)

### Scanner

`nuclei -list urls.txt`

nuclei -l urls.txt -t /home/kali/tools/nuclei-templates/cves

[https://cheatsheet.haax.fr/web-pentest/tools/nuclei/](https://cheatsheet.haax.fr/web-pentest/tools/nuclei/)
