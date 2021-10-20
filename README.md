# how2 - ServiceNow API access
Ref:
https://docs.servicenow.com/bundle/paris-application-development/page/integrate/inbound-rest/concept/c_RESTAPI.html
https://docs.servicenow.com/bundle/paris-application-development/page/integrate/inbound-rest/concept/use-REST-API-Explorer.html#use-REST-API-Explorer

## ServiceNow Studio (Web IDE)
https://dev106682.service-now.com/now/appenginestudio/home

## RestFul API Explorer
https://dev106682.service-now.com/nav_to.do?uri=%2F$restapi.do

## Personal Development area for ServiceNow applications
https://dev106682.service-now.com
Username: admin
Current password: WdFQcR1fn2Tv

# Pre-requisites
## User groups demanded grants
- rest_api_explorer
- web_service_admin roles.

# How to call ServiceNow API by curl

## Useful values

### ServiceNow Sites ([ServiceNow_Site])
eredes  -> Production environment
eredesdev -> Test environment

### PROXY Sites ([Proxy_Site])
http://172.18.236.92:8080

### User name ([USER_NAME])
T-00005 - Production
T-00006 - test environment


## How to query Incidents

### How to grab last day
curl -x [Proxy_Site] 'https://[ServiceNow_Site].service-now.com/api/now/table/incident?sysparm_query=sys_updated_onBETWEENjavascript:gs.dateGenerate(gs.beginningOfYesterday())@javascript:gs.dateGenerate(gs.endOfToday())' -u [USER_NAME]

### How to grab data between two dates
curl -x [Proxy_Site] 'https://[ServiceNow_Site].service-now.com/api/now/table/incident?sysparm_query=sys_updated_onBETWEENjavascript:gs.dateGenerate('2021-01-01','00:00:00')@javascript:gs.dateGenerate('2021-05-20','00:00:00')' -u [USER_NAME]


## How to query Change Requests

### How to grab last day
curl -x [Proxy_Site] 'https://[ServiceNow_Site].service-now.com/api/now/table/change_request?sysparm_query=sys_updated_onBETWEENjavascript:gs.dateGenerate(gs.beginningOfYesterday())@javascript:gs.dateGenerate(gs.endOfToday())' -u [USER_NAME]

### How to grab data between two dates
curl -x [Proxy_Site] 'https://[ServiceNow_Site].service-now.com/api/now/table/change_request?sysparm_query=sys_updated_onBETWEENjavascript:gs.dateGenerate('2021-01-01','00:00:00')@javascript:gs.dateGenerate('2021-05-20','00:00:00')' -u [USER_NAME]
 
