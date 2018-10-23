# Radware Specialist - CLI Commands

#### Default Password

admin:admin -> Force update after factory reset //
user:user

### Factory reset
```sh
/c/sys/access/boot/conf factory
```

### Force service to use management interface (tftp for instance)
```sh
/c/sys/mmgmt/tftp mgmt
```

### Enable a service like SNMP
```sh
/c/sys/access/snmp w
```

### Change prompt
```sh
/c/sys/ssnmp/name "MyName"
/c/sys/hprompt ena
```

### Change idle timeout
```sh
/c/sys/idle 9999
```

### Port-VLAN Binding
```sh
/c/l2/vlan VLAN_NUMBER/add PORT_NUMBER/ena
```

### Turn off Spanning Tree
```sh
/c/l2/stg 1/off
```

### IP-VLAN Binding
```sh
/c/l3/if INTERFACE_NUMBER/addr INTERFACE_IP/mask MASK/vlan VLAN_NUMBER/ena
```

### Add Gateway (default 1)
```sh
/c/l3/gw GATEWAY_NUMBER
addr GATEWAY_IP
ena
```

### Ping (using data interface)
```sh
ping IP
```

### Ping (using management interface)
```sh
ping IP -m
```

### Configuration backup
```sh
/c/ptcfg
CLIENT_IP
Include Private Keys
mansync
```

### Define real server
```sh
/c/slb/real SERVER_ID/rip SERVER_IP/ena
```

### Create a server group
```sh
/c/slb/group GROUP_ID
add SERVER_ID
...
metric ALGORITHM (roundrobin for example)
```

### Add health check to a group
```sh
/c/slb/group GROUP_ID/health CHECK_type (icmp for example)
```

### Create a virtual server
```sh
/c/slb/virt VIR_SERVER_ID
vip VIR_SERVER_IP
ena
```

### Define virtual service
```sh
/c/slb/virt VIR_SERVER_ID/service SERVICE/pip/addr PROXY_IP
```

### Service-Group Binding
```sh
/c/slb/virt VIR_SERVER_ID/service SERVICE/group GROUP_ID
```

### Get info on a server
```sh
/info/slb/real SERVER_ID
```

### Get info on a group
```sh
/info/slb/group GROUP_ID
```

### Get virtual server statistics
```sh
/stat/slb/virt SERVER_ID
```

### Get group statistics
```sh
/stat/slb/group GROUP_ID
```

### Clear virtual server statistics
```sh
/stat/slb/clear
```

### Create a healthcheck
```sh
/stat/slb/advhc/health
HEALTHCHECK_ID
HEALTHCHECK_TYPE (http, ftp ...)
name HEALTHCHECK_NAME
OPTIONAL
dport DPORT
http
path index.htm
```

### Healthcheck-Server Binding
```sh
/c/slb/real REAl_SERVER_ID/health HEALTHCHECK_ID
```

### Remove Healthcheck-Server Binding
```sh
/c/slb/real REAl_SERVER_ID/health inherit
```

### Combine Healthchecks
```sh
/stat/slb/advhc/health HEALTHCHECK_ID
logexp
LOGICAL_EXPRESSION
name HEALTHCHECK_NAME
```

### Apply AppScript++ script on virtual service
```sh
/c/slb/virt VIRTUALSERVICE_ID/service SERVICE_PORT/appshape/add SCRIPT_PRIORITY SCRIPT_ID
```

### Change Group metric
```sh
/c/slb/group GROUP_ID/metric METRIC_NAME (leastcon)
```

### Change Port metric
```sh
/c/slb/group GROUP_ID/rmetric METRIC_NAME (leastcon)
```

### Configure virtual server to use all ports on the server
```sh
/c/slb/virt VIRTUALSERVICE_ID/service SERVICE_PORT/rport 0
```

### Add port to a server
```sh
/c/slb/real SERVER_ID/add PORT/ena
```

### Change server weight
```sh
/c/slb/real SERVER_ID/weight 2
```

### Enable SSL
```sh
/c/slb/ssl/on
```

### Create self signed certificate
```sh
/c/slb/ssl/certs/cert CERTIFICATE_ID
name CERTIFICATE_NAME
generate
COMMON_NAME
```

### Virtual Service-SSL Policy binding
```sh
/c/slb/virt VIRTUALSERVICE_ID/service https
/c/slb/virt VIRTUALSERVICE_ID/service/cert
CERTIFICATE_ID
SSLPOLICY_ID
/c/slb/virt VIRTUALSERVICE_ID/service 443 https/pip
mode address
addr v4 PIP_IP 255.255.255.255 persist disable
```

### Enable Direct Access Module (For persistent SLB)
```sh
/c/slb/adv/direct ena
```

### Change Virtual Server port
```sh
/c/slb/virt VIRTUALSERVICE_ID/service PORT/rport NEW_PORT
```

### Clear session table
```sh
/oper/slb/clear
```

### Enable VIRT on Virtual service
```sh
/c/slb/virt VIRTUALSERVICE_ID/service PORT
pbind
cookie
passive
COOKIE_NAME
disable
```

### Insert session cookie
```sh
/c/slb/virt VIRTUALSERVICE_ID/service PORT
pbind
cookie
insert
COOKIE_NAME
DOMAIN_NAME
```

### Enable forceproxy for a virtual server
```sh
/c/slb/virt VIRTUALSERVICE_ID/service PORT
dbind forceproxy
```

### X-Forwarde-For Header
```sh
/c/slb/virt VIRTUALSERVICE_ID/service PORT
http/xforward ena
```

### Remove server identity
```sh
/c/slb/virt VIRTUALSERVICE_ID/service PORT
http/cloaksrv ena
```

# Radware Specialist - GUI Commands

### Disable VLAN1
* Configuration > Network > Layer2 > VLAN 
* Double click on VLAN1
* Unchecb Enable VLAN

### Port-VLAN Binding
* Configuration > Network > Layer2 > VLAN 
* Click on +

### IP-VLAN Binding
* Configuration > Network > Layer3 > IP Interfaces 
* Click on +

### Configuration backup
* System > Configuration Management > Export Configuration

### Define real server
* Application Delivery > Server Resources > Real Servers

### Create a virtual server
* Configuration > Application Delivery > Virtual Services

### Get info on a server
* Service Status View

### Add an AppShape++ Script
* Application Delivery > AppShape++ scripts
* Click on Import
* Click on Enable
* Enter a script id
* Browse the file

### Enable SSL
* Application Delivery > SSL
* Enable SSL

### Generate Self Signed certificate
* Application Delivery > SSL > Certificate Repository
* Click +
* Setting > Common Name

### Define SSL Policy
* Application Delivery > SSL > SSL Policy
* Click +
* Add new SSL Policy
* Enable SSL Policy
* Policy ID
* Description
* Cipher Suite main

### Virtual Service-SSL Policy binding
* Application Delivery > Virtual Services
* HTTPS Virtual Services
* Client PIP
* Server Certificate
* SSL Policy
