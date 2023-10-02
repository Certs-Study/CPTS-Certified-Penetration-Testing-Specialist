---
description: Save nmap result in different formats.
---

# 🟢 Saving the Results

### Different Formats

While we run various scans, we should always save the results. We can use these later to examine the differences between the different scanning methods we have used. `Nmap` can save the results in 3 different formats.

* Normal output (`-oN`) with the `.nmap` file extension
* Grepable output (`-oG`) with the `.gnmap` file extension
* XML output (`-oX`) with the `.xml` file extension

### Style sheets

With the XML output, we can easily create HTML reports that are easy to read, even for non-technical people. This is later very useful for documentation, as it presents our results in a detailed and clear way. To convert the stored results from XML format to HTML, we can use the tool `xsltproc`.

&#x20; XML Output

```shell-session
xsltproc target.xml -o target.html
```
