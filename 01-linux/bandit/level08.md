# Level 8-9: The password is stored in the file data.txt and is the only line of text that occurs only once

## Password
4CKMh1JI91bUIZZPXDqGanal4xvAg0JM
## Method
Group all the lines with 'sort', then use 'uniq' to filter duplicate lines, with the '-u' flag to only print lines that appear once
```
sort data.txt | uniq -u
```
**What I learned:** [[sort] data.txt](../notes/02-Commands.md) sorts all the lines into alphabetical order, grouping identical lines together -> [uniq] filters out duplicate lines -> [-u] option only prints lines that appear once