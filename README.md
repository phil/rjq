# rjq
A simple Ruby app to make working with jSON in the command line easy.

## Should I use this?

_Maybe_, it's random software that you've downloaded from the internet, 
but it is open source, and it's only 5 lines of code. Lets face it, if
you're happy downloading scripts, you either know what you're doing, or
you should be thinking hard about weather this is a good idea..

### What can go wrong?

It's untested. It uses Ruby's `eval()` method, so it's running whatever 
arbritary code _you_ type in. If you're happy with this, good on you.

### Why not just use `jq`?

Have _you_ tried to use `jq`? I mean, it's a fantastic tool, fast, and reliable. 
But when you have to re-read the docs everytime you want to just map over a for single key,
and then give up and try and find a cheatsheet that does what you want to do … well, yeah.

## Requirements

- Any OS that runs a bash/zsh like terminal shell.
- Ruby

## Installing

Copy `bin/rjq` to a directory that is in your `$PATH`. make sure you set the file to have executable permissions.

## Using

Simply pipe the JSON file into `rjq` and write ruby script 
as it would be if called on the parsed JSON.

E.g., Get each of the top level keys:

```
~/ curl https://www.gov.uk/bank-holidays.json | rjq ".keys"
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100 15124  100 15124    0     0   162k      0 --:--:-- --:--:-- --:--:--  162k
england-and-wales
scotland
northern-ireland
```

E.g., Get each bank holiday with date, in England and Wales, and show if bunting is required:
```
curl https://www.gov.uk/bank-holidays.json | rjq "['england-and-wales']['events'].map{|e| %(#{e['title']} #{e['date']} #{'🎉' if e['bunting']} ) }"

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
 
 
