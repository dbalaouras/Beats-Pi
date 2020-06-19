# Beats-Pi
Elastic Beats.  You know, for Pi.

### TEMPORARY SHUTDOWN due to errors...  Beats will be back soon.
Seriously every version update causes some kind of horrendous problem that takes a whole day to solve.  Because why should the same process work twice?!

### Updates 18 Jun 2020
v7.7.1 and v7.8.0 are now available.  Added x-pack support to Filebeat, so please notice that several Filebeat components now fall under the Elastic License instead of the Apache License.  Couldn't get x-pack support to work on Metricbeat, so that's still the OSS version.

### Updates 27 May 2020
By request, v7.6.2 .deb files are posted in an Old-DEBs folder.  In the event the repo doesn't keep the older versions available I'll post them here.  

### Updates 19 May 2020
v7.7.0 of the Auditbeat, Heartbeat, Metricbeat, and Filebeat are now posted.  Enjoy!

### Updates 28 March 2020
Added support for arm64 architecture in case you're running a 64-bit OS on your Pi.

### Updates 17 March 2020
v7.6.1 of all the Beats are now live!  I changed the GPG key, so you'll need to re-download using the instructions below.
ENJOY!

## About this repo
Elastic Beats are lightweight data shippers that collect and send information back to Logstash, your Elasticsearch cluster, or another output of your choosing.  However, Elastic doesn't package them for Raspberry Pi, so even if you connect to Elastic's apt repo, you won't be able to install Beats.

You can build the beats from source if you want, and I go over how to do that in my easyBEATS fork.  However, here I make it easy.  I've packaged the Beats and put them in an apt repo that you can use on your Raspberry Pi.

Let's be perfectly clear: Beats are created by Elastic NV, not me.  All I'm doing here is compiling from source and hanging in a repo.  I didn't develop the Beats and deserve no credit for the whizbangitry they provide.  Most of what you see here is covered under the Apache 2.0 License, but some of the Beats modules are covered under the Elastic License.  For more details and to see which ones, visit https://github.com/elastic/beats/tree/master/x-pack

## Connect to the repo

First you'll need to install the gpg key for this repo.  This helps to ensure that the package hasn't changed between the repo and your Pi.

```
wget -O - https://raw.githubusercontent.com/RaoulDuke-Esq/Beats-Pi/master/beats-pi.gpg.key | sudo apt-key add -
```

Next, add the repo to your apt sources.

```
echo "deb https://raw.githubusercontent.com/RaoulDuke-Esq/Beats-Pi/master buster main" | sudo tee -a /etc/apt/sources.list.d/beats-pi.list
```

That's it!  Pretty easy, right?

## Installing Beats

Now you can update apt with the new packages found in this repo.

```
sudo apt-get update
```

Install whichever Beat you'd like.

```
sudo apt-get install metricbeat
```

## Configuring Beats

If you're not already familiar with how to configure Beats, check out [Elastic's documentation](https://www.elastic.co/guide/index.html).

## Upgrading Beats
If you've previously installed Beats using this repo, don't worry!  When you upgrade you will be prompted on whether to keep or replace your existing beat.yml file.  Just type N to keep your existing version.
