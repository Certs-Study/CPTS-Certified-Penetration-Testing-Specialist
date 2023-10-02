# Crawling

{% code overflow="wrap" %}
```
ffuf -recursion -recursion-depth 1 -u http://192.168.10.10/FUZZ -w /opt/useful/SecLists/Discovery/Web-Content/raft-small-directories-lowercase.txt
```
{% endcode %}

```
cewl -m5 --lowercase -w wordlist.txt http://192.168.10.10
```

{% code overflow="wrap" %}
```
ffuf -recursion -recursion-depth 1 -u http://192.168.10.10/FUZZ -w /opt/useful/SecLists/Discovery/Web-Content/raft-small-directories-lowercase.txt
```
{% endcode %}

{% code overflow="wrap" %}
```
ffuf -w ./folders.txt:FOLDERS,./wordlist.txt:WORDLIST,./extensions.txt:EXTENSIONS -u http://192.168.10.10/FOLDERS/WORDLISTEXTENSIONS
```
{% endcode %}
