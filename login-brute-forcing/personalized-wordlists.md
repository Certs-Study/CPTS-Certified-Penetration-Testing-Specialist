# Personalized Wordlists

CUPP

{% embed url="https://github.com/Mebus/cupp" %}

### Password Policy

```
sed -ri '/^.{,7}$/d' william.txt            # remove shorter than 8
sed -ri '/[!-/:-@\[-`\{-~]+/!d' william.txt # remove no special chars
sed -ri '/[0-9]+/!d' william.txt            # remove no numbers
```

### Mangling

Many great tools do word mangling and case permutation quickly and easily, like [rsmangler](https://github.com/digininja/RSMangler) or [The Mentalist](https://github.com/sc0tfree/mentalist.git). These tools have many other options, which can make any small wordlist reach millions of lines long. We should keep these tools in mind because we might need them in other modules and situations.

### Custom Username Wordlist

```shell-session
RFS85@htb[/htb]$ git clone https://github.com/urbanadventurer/username-anarchy.git

Cloning into 'username-anarchy'...
remote: Enumerating objects: 386, done.
remote: Total 386 (delta 0), reused 0 (delta 0), pack-reused 386
Receiving objects: 100% (386/386), 16.76 MiB | 5.38 MiB/s, done.
Resolving deltas: 100% (127/127), done.
```

```
./username-anarchy Bill Gates > bill.txt
```
