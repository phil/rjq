# rjq
A simple ruby app to make working with jSON in the command line easy.

## Requirements

Any OS that runs a bash/zsh like terminal shell.

## Installing

Copy `bin/rjq` to a directory that is in your `$PATH`

## Using

Simply pipe the JSON file into `rjq` and write ruby script as it would be if called on the parsed JSON.

E.g., Get each of the top level keys:

```
~/ curl https://www.gov.uk/bank-holidays.json | rj ".keys"
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100 15124  100 15124    0     0   162k      0 --:--:-- --:--:-- --:--:--  162k
england-and-wales
scotland
northern-ireland
```

E.g., Get each bank holiday with date, in England and Wales, and show if bunting is required:
```
curl https://www.gov.uk/bank-holidays.json | rj "['england-and-wales']['events'].map{|e| %(#{e['title']} #{e['date']} #{'🎉' if e['bunting']} ) }"

  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100 15124  100 15124    0     0   136k      0 --:--:-- --:--:-- --:--:--  136k
New Year’s Day 2016-01-01 🎉
Good Friday 2016-03-25
Easter Monday 2016-03-28 🎉
Early May bank holiday 2016-05-02 🎉
Spring bank holiday 2016-05-30 🎉
Summer bank holiday 2016-08-29 🎉
Boxing Day 2016-12-26 🎉
Christmas Day 2016-12-27 🎉
New Year’s Day 2017-01-02 🎉
Good Friday 2017-04-14
Easter Monday 2017-04-17 🎉
Early May bank holiday 2017-05-01 🎉
Spring bank holiday 2017-05-29 🎉
```
 
 
