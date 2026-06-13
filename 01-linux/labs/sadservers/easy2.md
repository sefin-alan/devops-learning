# Scenario: "Saskatoon": counting IPs.

## Description: There's a web server access log file at /home/admin/access.log. The file consists of one line per HTTP request, with the requester's IP address at the beginning of each line (first column). Find the IP address that has the most requests in this file (there's no tie; the IP is unique). Write the solution into a file /home/admin/highestip.txt

### Method
Print the first column alone as that is where the requesters' IP addresses are, then `sort` into order, placing repeated lines together
```
awk '{print $1}' /home/admin/access.log | sort
```

Give every line a prefix with the number of occurences, and put them in order of numerical value
```
| uniq -c | sort -n
```
The IP Address with the highest number of occurences will be displayed in the bottom line

Because the prefix with the number of occurences was added to each line, the IP Addresses are now in the second column so the second variable needs to be specified
```
| awk '{print $2}' | tail -1 > /home/admin/highestip.txt
```
the bottom line is specified and then redirected to /home/admin/highestip.txt, as requested by the description.

So altogether, the full command will look like this:
```
awk '{print $1}' /home/admin/access.log | sort | uniq -c | sort -n | awk '{print $2}' | tail -1 > /home/admin/access.log
```

**What I learned:** `awk` is similar to `grep` in that it is used to specify patterns in a text file, it was used to print the first column alone or '$1'. `uniq -c` prefixes each unique line in the input with a count of how many times it appeared consecutively.