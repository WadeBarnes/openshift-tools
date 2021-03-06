# OpenShift Monitoring Scripts

This folder contains a set of scripts related to monitoring / checking of OpenShift or OpenShift-deployed resources.

## check_urls

This script dynamically pulls in the set of routes across all projects in OpenShift and checks them.

Requirements:

* python 3+
* requests lib (eg. ```pip install requests```)

To run:

``` bash
./check_urls.sh
```

There will be "false negatives" due to orphaned routes or broken apps, but the purpose of this script is mainly to check whether the router is experiencing problems, not to test specific apps.

Sample output (names, etc. changed to protect the guilty...):

``` bash
=================
Starting a run.
=================
time='2017-01-07 10:08:45.218158',error=Failed with Exception, project=xyz, route_name=xyz, route=https://xyz.gov.bc.ca, exception='('Connection aborted.', RemoteDisconnected('Remote end closed connection without response',))''
time='2017-01-07 10:07:12.953645', error=Failed with bad status, project=pqr, route_name=pqr, route=http://pqr.gov.bc.ca, response_code=503
=================
Run complete... Grabbing a coffee before next run...
=================
```
