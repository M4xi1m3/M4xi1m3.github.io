---
layout: post
title: "Micmost: how a .git folder can get your consumers' data leaked."
comments: true
---

This isn't the kind of things I generally do on here, but it will be fun. A month ago, I was checking a TrackMania host called Micmost because I needed a TMNF server for a short period and I wasn't confident enough to set it up myself... First thing I did was to check their security, and...

## First reflex : nmap

I started by using nmap on their main web server, [https://micmost.net/](https://micmost.net/), which lead to nothing. I discovered a subdomain, [https://tmpanel.micmost.net/](https://tmpanel.micmost.net/), which was very interesting:

```
$ nmap tmpanel.micmost.net -p443 --script=http-enum
Starting Nmap 7.80 ( https://nmap.org ) at 2020-09-17 16:49 CEST
Nmap scan report for tmpanel.micmost.net (136.243.173.150)
Host is up (0.057s latency).
rDNS record for 136.243.173.150: static.150.173.243.136.clients.your-server.de

PORT    STATE SERVICE
443/tcp open  https
| http-enum: 
|   /.git/HEAD: Git folder
|   /phpmyadmin/: phpMyAdmin (401 Unauthorized)
|_  /manual/: Potentially interesting folder

Nmap done: 1 IP address (1 host up) scanned in 9.86 seconds
```

This should **IMMEDIATLY** ring a bell. There was a .git folder right at the root of the site, and whilst directory listing was disabled, I could still access the content of files inside.

I also did a port scan, to know what else was avaliable on the server :

```
$ nmap tmpanel.micmost.net
Starting Nmap 7.80 ( https://nmap.org ) at 2020-09-17 16:49 CEST
Nmap scan report for tmpanel.micmost.net (136.243.173.150)
Host is up (0.062s latency).
rDNS record for 136.243.173.150: static.150.173.243.136.clients.your-server.de
Not shown: 992 closed ports
PORT     STATE    SERVICE
21/tcp   open     ftp
22/tcp   open     ssh
80/tcp   open     http
443/tcp  open     https
554/tcp  open     rtsp
1723/tcp open     pptp
2366/tcp open     qip-login
3306/tcp filtered mysql

Nmap done: 1 IP address (1 host up) scanned in 6.76 seconds
```

We can see alot of things, but the most interesting thing is the open mysql server.

## What could possibly go wrong?

I won't go into details, but I used [git-dumper](https://github.com/arthaud/git-dumper) to download the raw source code of their website. It is kinda messy, but evey complicated PHP website end up like that at some point. From there, I got the user and password of their DB and dumped it. In there were users details such as name, billing details and password (md5 + salt at the beginning and at the end).

## Now, what?

Something I forgot to do at the time was to disclose the vulnerability to haveibeenpwned, and I can't do it now, as I got rid of every single files I dumped from their website (including the DB). I disclosed the vulnerability to micmost. Their reaction was what I would consider a good reaction, willing to patch the vuln. I helped them fix it and told them that I'll let them a month before releasing an article here.

I obviously didn't use the data for anything malicious, as this wasn't my goal.

## Moral of the story

Don't put .git directories in public. Don't open your DB to the internet. Don't be a dick to intruders if they are nice with you, and everything will be fine.

## EDIT: Well, I was wrong.

I had an agreement with them. They let me disclose the vulnerability, but without deteriorating their band image, which I did. As a counterpart, I asked them to let me publish the article on their discord, and publicly. Well, 30s after putting the link on their discord, I got banned. No explainations, straight off banned. So, I'll go full on with them.

The PHP code of their panel is one of the worst thing I've seen in my life. Nothing is protected, and their way of handling starting and stopping the servers can be exploited really easilly.

When I explained to them why slated md5 was a bad choice, they were like "nah, it's ok.". In the end, they didn't disclose that to their constumers, and didn't bother switching hashing algorythm.

Legally speaking, Micmo is **nothing**, not a single information about a company on their website. This is completly illegal, as French laws (yes they are French) require corporations to put informations about the corp itself, like the addresse of the headquarter and the SIRET number.

If you got a server on there, **run away**.



