# Changelog

### Todo list
- Get lenght and device
- grafana more internal panels and plain numbers
- Stop gathering after few days
### Not planned features
- maybe analys fallback logs

## v2.3.0
- add arm/v7 and arm64/v8 image (see #11 and thanks to @Gyarbij with #12)
- fix timezone issue (Thanks to Im1Random https://www.reddit.com/r/nginxproxymanager/comments/1418ae1/comment/jn0pizn/?)
- create an option to see stats of internal domain-calls (see #14)
  (option INTERNAL_LOGS and MONITORING_LOGS see more in Installation wiki)
- remove HOME_IPS to get IP automatically (see #15)
- added a license
- Grafana dashboard now uses the default bucket as source which gets set during the Grafana Influx datasource setup (see #14)
- Grafana dashboard add Internal IPs , Montioring Ips count and other panels
- Change Latitude and Longitude to latitude and longitude for easier future Grafana panels

## v2.2.1
- add option REDIRECTION_LOGS='ONLY' for only redirection logs analysis
- add version to startup logs
- add an external list of ip's to be excluded for exclusion of monitoring ip's
- move HOME_IPS to internal domain

## v2.2.0
Removes duplicate logs of the same Connection in case of a restart of NpmGrafStats
- add time to influx measurement (see #7)
- convert [30/May/2023:14:16:48 +0000] to 2009-11-10T23:00:00.123456Z RFC 3339
  - Timezone is not converted! Stays UTC

## v2.1.1
- fix redirection logs
- added Redirections and ReverseProxy Dashboard to Grafana
- fix Readme.md
- New Grafana ID 18826 (i accidentally the old one. Sorry)

## v2.1.0
- clean up Dockerfile
- print and set measurment name
- print 'data send' after influx send
- added sendredirectionips.sh for redirection logs (see #5)
- true statement for redirection logs
- removed NPMGRAF_HOME variable
- changed docker naming sheme to version number
- added internal-ip filter
- changed from sh to bash to use regex

## v2.0.0
### Dev info/changes made to original
To the Original Project following changes were made:
- the new log format and only the proxy-host*-access.log from NPM are used
- Domains now allow a "-" in the domain
- no subdomains or subdomains up to 3 levels extra (sub.sub.sub.domain.tld)
- the targeted internal ip is logged
- using influxdb v2

#### Detailed
- args parssed sendips.sh to Getipinfo.py: 1. Outside IP 2. Domain 3. length 4. Target IP
- These Domain only registered for me : .env.de, config.php.com(.de,.org)
- Add Domains to Dashboard
- Did NPM change the log format? -> to access.log
- exclude external Ip
- add apk grep for --line-buffered as not included in bash in busybox -> overflow -> process stopped
- upgrade to influx 2 - see project https://github.com/evijayan2/nginxproxymanagerGraf

