# Fortinet FortiADC Modules
---
### Requirements
* Python requests
* Everything was tested with FortiADC v5.3

---
### Modules
[fadcos_backup_config](#fadcos_backup_config)

[fadcos_system_control](#fadcos_system_control)

[fadcos_interface](#fadcos_interface)

[fadcos_route_static](#fadcos_route_static)

[fadcos_system_setting](#fadcos_system_setting)

[fadcos_admin](#fadcos_admin)

[fadcos_vdom](#fadcos_vdom)

[fadcos_real_server](#fadcos_real_server)

[fadcos_real_server_pool](#fadcos_real_server_pool)

[fadcos_real_server_pool_member](#fadcos_real_server_pool_member)

[fadcos_nat_pool](#fadcos_nat_pool)

[fadcos_nat_pool_member](#fadcos_nat_pool_member)

[fadcos_virtual_server_basic](#fadcos_virtual_server_basic)

[fadcos_virtual_server](#fadcos_virtual_server)

---
## fadcos_backup_config
  * Synopsis
  * Options
  * Examples
#### Synopsis
You use the backup procedure to save a copy of your system configuration. A full backup is a zip file.

#### Options
| parameter     | required    | default  | choices    | comments |
| ------------- |-------------| ---------|----------- |--------- |
|action|yes| |<ul> <li>download</li>  <li>save</li>  <li>list</li> </ul>| |
|configtype|no|local|<ul> <li>local</li>  <li>adc</li> </ul>| |
|path|no| | | |
|password|no| | | |
|name|no|Ansiblebackup| | |

## fadcos_system_control
  * Synopsis
  * Options
  * Examples
#### Synopsis
Reboot: Reboots the operating system.
Shut Down: Shuts down the system. When the system is shut down, it is unavailable to forward traffic.

#### Options
| parameter     | required    | default  | choices    | comments |
| ------------- |-------------| ---------|----------- |--------- |
|action|yes| |<ul> <li>shutdown</li>  <li>reboot</li></ul>| |

## fadcos_interface
  * Synopsis
  * Options
  * Examples
#### Synopsis
You can edit the physical interface configuration. You cannot create or delete a physical interface configuration.

#### Options
| parameter     | required    | default  | choices    | comments |
| ------------- |-------------| ---------|----------- |--------- |
|action|yes| |<ul> <li>add</li>  <li>edit</li>  <li>delete</li>  <li>get</li> </ul>| |
|name|no|no| | |
|status|no|up| |This Status column is not the detected physical link status; it is the administrative status (up/down) that indicates whether you permit the network interface to receive and/or transmit packets.|
|mode|no| |<ul> <li>static</li>  <li>pppoe</li>  </ul>|static: Specify a static IP address. The IP address must be on the same subnet as the network to which the interface connects. Two network interfaces cannot have IP addresses on the same subnet (i.e. overlapping subnets). <br />pppoe: Use PPPoE to retrieve a configuration for the IP address, gateway, and DNS server. For example, if this interface uses a DSL connection to the Internet, your ISP may require this option.|
|IPandMask|no| | |Specify the IP address and CIDR-formatted subnet mask, separated by a forward slash ( / ), such as 192.0.2.5/24. Dotted quad formatted subnet masks are not accepted.|
|IPv6andMask|no| | |Specify the IP address and CIDR-formatted subnet mask, separated by a forward slash ( / ), such as 2001:0db8:85a3:::8a2e:0370:7334/64. Dotted quad formatted subnet masks are not accepted.|
|allowaccess|no| |<ul> <li>http</li>  <li>https</li>  <li>ping</li>  <li>snmp</li>  <li>ssh</li>  <li>telnet</li>  </ul>|Allow inbound service traffic. Specify a space-separated list of the following options|
|mtu|no|1500| |The default is 1500. We recommend you maintain the default.|
|intf_type|no| | |If you are editing the configuration for a physical interface, you cannot set the type.|
|vlanid|no| | |VLAN ID of packets that belong to this VLAN.|
|vdom|no| | |If applicable, select the virtual domain to which the configuration applies.|
|interface|no| | |Physical interface associated with the VLAN; for example, port2.|
|aggregate_algorithm|no| | | |
|aggregate_mode|no| | | |
|default_gw|no|enable| | |
|dhcp_gw_override|no|disable| | |
|dhcp_gw_distance|no|10| | |
|disc_retry_timeout|no| | |Seconds the system waits before it retries to discover the PPPoE server.|
|pppoe_username|no| | |PPPoE account user name.|
|pppoe_passwd|no| | |PPPoE account password|
|floating|no|disable| | |
|floating_ip|no| | | |
|redundant_member|no| | |Specify the physical interfaces that are included in the aggregation.|
|traffic_group|no|default| | |

## fadcos_route_static
  * Synopsis
  * Options
  * Examples
#### Synopsis
Network systems maintain route tables to determine where to forward TCP/IP packets.

#### Options
| parameter     | required    | default  | choices    | comments |
| ------------- |-------------| ---------|----------- |--------- |
|action|yes| |<ul> <li>add</li>  <li>edit</li>  <li>delete</li>  <li>get</li> </ul>| |
|route_id|no| | | |
|desination|no| | |Address/mask notation to match the destination IP in the packet header.<br/>Specify 0.0.0.0/0 or ::/0 to set a default route for all packets.|
|gateway|no| | |Specify the IP address of the gateway router that can route packets to the destination IP address that you have specified.|
|distance|no| | |The default administrative distance is 10, which makes it preferred to OSPF routes that have a default of 110. We recommend you do not change these settings unless your deployment has exceptional requirements.|
|vdom|no| | | |


## fadcos_system_setting
  * Synopsis
  * Options
  * Examples
#### Synopsis
The basic system settings page includes configuration options for the following settings and features:

* Hostname
* Web UI language
* Management service ports
* DNS
* Virtual domain

#### Options
| parameter     | required    | default  | choices    | comments |
| ------------- |-------------| ---------|----------- |--------- |
|idle_timeout|no| | |Log out an idle administrator session. The default is 30 minutes.|
|config_sync|no| | |enable/disable the configuration synchronization feature. This feature is related to the execute config-sync command, not HA synchronization. Disabled by default.|
|intermediate_ca_group|no| | | |
|hostname|no| | |You can configure a hostname to facilitate system management. If you use SNMP, for example, the SNMP system name is derived from the configured hostname. The hostname can be up to 35 characters in length. It can include US-ASCII letters, numbers, hyphens, and underscores, but not spaces and special characters. The System Information widget and the get system status CLI command display the full hostname. If the hostname is longer than 16 characters, the name is truncated and ends with a tilde ( ~ ) to indicate that additional characters exist, but are not displayed.|
|http_port|no| | |Specify the port for the HTTP service. Usually, HTTP uses port 80.|
|https_port|no| | |Specify the port for the HTTPS service. Usually, HTTPS uses port 443.|
|https_server_cert|no| | | |
|ip_primary|no| | | |
|ip_second|no| | | |
|ssh_port|no| | |Specify the port for the SSH service. Usually, SSH uses port 22.|
|sys_global_language|no| | | |
|telnet_port|no| | |Specify the port for the Telnet service. Usually, Telnet uses port 25.|
|vdom|no| | |Enables the virtual domain feature.|

## fadcos_admin
  * Synopsis
  * Options
  * Examples
#### Synopsis
In its factory default configuration, FortiADC has one administrator account named admin. The user of this account has permissions that grant read-write access to all system functions.

Unlike other administrator accounts, this default d admin cannot be deleted. The admin account is similar to a root administrator account. This account always has full permission to view and change all system configuration options, including viewing and changing all other administrator accounts. You cannot alter the name and permissions of this default admin account.

To prevent accidental changes to the configuration, it is best that only network administrators, and if possible, only a single person, use the admin account.

You can use the admin account to configure more administrator accounts for other users. Accounts can be created with different levels of access. If you require such role-based access control (RBAC) restrictions, or if you simply want to harden security or prevent inadvertent changes to other administrators? areas, you can do so using access profiles. For example, you can create an account for a security auditor who must only be able to view the configuration and logs, but not change them.

#### Options
| parameter     | required    | default  | choices    | comments |
| ------------- |-------------| ---------|----------- |--------- |
|action|yes| |<ul> <li>add</li>  <li>edit</li>  <li>delete</li>  <li>get</li> </ul>| |
|name|no| | |Name of the administrator account, such as admin1 or admin@example.com. Do not use spaces or special characters except the ?at? symbol ( @) or dot (.). The maximum length is 35 characters. Note: This is the user name that the administrator must provide when logging in to the CLI or web UI. After you initially save the configuration, you cannot edit the name.|
|trused_hosts|no|0.0.0.0/0 ::/0| | |
|global_admin|no|no| | |
|profile|no|super_admin_prof| |Specify a user-defined or predefined profile. The predefined profile named super_admin_prof is a special access profile used by the admin account. However, specifying this access profile will not confer all permissions of the admin account. For example, the new administrator would not be able to reset lost administrator passwords.|
|vdom|no| | |If you have enabled the virtual domain feature, specify the virtual domain that this administrator can view and manage. Note: You can create multiple VDOMs separated by space.|
|auth_stratgey|no| | |local-Use the local authentication server.<br/>ldap-Use an LDAP authentication server. Select the LDAP server configuration.<br/>radius-Use a RADIUS authentication server.|
|password|no| | |Set a strong password for all administrator accounts. The password should be at least eight characters long, be sufficiently complex, and be changed regularly.|
|radius_server|no| | |If using RADIUS, specify the RADIUS server configuration.|
|ldap_server|no| | |If using LDAP, specify the LDAP server configuration.|
|wildcard|no|disable| |Enable/disable user wildcard for remote server authentication.|

## fadcos_vdom
  * Synopsis
  * Options
  * Examples
#### Synopsis
A virtual domain (VDOM) is a complete FortiADC instance that runs on the FortiADC platform. The VDOM feature supports multi-tenant deployments. To do this, you create a virtual domain configuration object that contains all of the system and feature configuration options of a full FortiADC instance, and you provision an administrator account with privileges to access and manage only that VDOM.

#### Options
| parameter     | required    | default  | choices    | comments |
| ------------- |-------------| ---------|----------- |--------- |
|action|yes| |<ul> <li>add</li>  <li>delete</li>  <li>get</li> </ul>| |
|name|no| | | |

## fadcos_real_server
  * Synopsis
  * Options
  * Examples
#### Synopsis
Real servers are physical servers that are used to form real server pools. These dedicated servers provide clients with services such as HTTP or XML content, streaming audio or video, TFTP/FTP uploads and downloads, etc. You can start configuring a real server by giving it a unique configuration name, setting its status, and specifying its IP address.

#### Options
| parameter     | required    | default  | choices    | comments |
| ------------- |-------------| ---------|----------- |--------- |
|action|yes| |<ul> <li>add</li>  <li>edit</li>  <li>delete</li>  <li>get</li> </ul>| |
|name|no| | | |
|status|no| |<ul> <li>enable</li>  <li>disable</li>  <li>maintain</li> </ul>| |
|ip|no| | |For IPv4 real server, enter the real server's IP address in IPv4 address format.|
|ipv6|no|::| |For IPv6 real server, enter the real server's IP address in IPv6 address format|
|vdom|no| | | |

## fadcos_real_server_pool
  * Synopsis
  * Options
  * Examples
#### Synopsis
Server pools are groups of real servers that host the applications that you load balance.
For create a server pool object.

#### Options
| parameter     | required    | default  | choices    | comments |
| ------------- |-------------| ---------|----------- |--------- |
|action|yes|<ul> <li>add</li>  <li>edit</li>  <li>delete</li>  <li>get</li> </ul>| | |
|name|no| | |Configuration name. Valid characters are A-Z, a-z, 0-9, _ , and -. No spaces.|
|iptype|no| | <ul> <li>ipv4</li>  <li>ipv6</li> </ul>| |
|healthcheck|no|disable| |Enable health checking for the pool. The health check settings at this configuration level are the parent configuration. When you configure the pool members, you can specify whether to inherit or override the parent configuration.|
|health_check_relationship|no|AND| |AND-All of the specified health checks must pass for the server to be considered available.<br/>OR-One of the specified health checks must pass for the server to be considered available.|
|health_check_list|no| | |Specify one or more health check configuration objects.|
|rs_profile|no|NONE| |Specify a real server profile. Real server profiles determine settings for communication between FortiADC and the backend real servers.|
|vdom|no| | | |

## fadcos_real_server_pool_member
  * Synopsis
  * Options
  * Examples
#### Synopsis
Server pools are groups of real servers that host the applications that you load balance.
For add a server pool member

#### Options
| parameter     | required    | default  | choices    | comments |
| ------------- |-------------| ---------|----------- |--------- |
|action|yes| |<ul> <li>add</li>  <li>edit</li>  <li>delete</li>  <li>get</li> </ul>| |
|pool_name|yes| | | |
|member_id|no| | | |
|rs|no| | |select a real server configuration object|
|status|no|enable|<ul> <li>enable</li>  <li>disable</li>  <li>maintain</li> </ul>| |
|port|no|80| |Enter the backend server's listening port (number)|
|recover|no|0| |Seconds to postpone forwarding traffic after downtime, when a health check indicates that this server has become available again. The default is 0 (disabled). The valid range is 1 to 86,400 seconds.|
|rs_profile_inherit|no|enable| |Enable to inherit the real server profile from the pool configuration. Disable to specify the real server profile in this member configuration.|
|rs_profile|no|NONE| |If not configured to inherit the pool setting, specify a real server profile. Real server profiles determine settings for communication between FortiADC and the backend real servers.|
|weight|no|1| |Assigns relative preference among members?higher values are more preferred and are assigned connections more frequently. The default is 1. The valid range is 1 to 256.|
|warmup|no|0| |If the server cannot initially handle full connection load when it begins to respond to health checks (for example, if it begins to respond when startup is not fully complete), indicate how long to forward traffic at a lesser rate. The default is 0 (disabled). The valid range is 1 to 86,400 seconds.|
|warmrate|no|100| |Maximum connection rate while the server is starting up. The default is 10 connections per second. The valid range is 1 to 86,400 connections per second.|
|backup|no|disable| |Server that the ADC directs traffic to only when other servers in the pool are down. The backup server receives connections when all the other pool members fail the health check or you have manually disabled them, for example.|
|connlimit|no|0| |Maximum number of concurrent connections to the backend server. The default is 0 (disabled). The valid range is 1 to 1,048,576 concurrent connections.|
|connection_ratelimit|no|0| |Limit the number of new connections per second to this server. The default is 0 (disabled). The valid range is 1 to 86,400 connections per second. In Layer 4 deployments, you can apply a connection rate limit per real server and per virtual server. Both limits are enforced.|
|cookie|no| | | |
|health_check_inherit|no|enable| |Enable to inherit the health check settings from the parent configuration. Disable to specify health check settings in this member configuration.|
|health_check|no|disable| |Enable health checking for the pool.|
|health_check_list|no| | |Specify one or more health check configuration objects.|
|health_check_relationship|no|AND| |AND-All of the specified health checks must pass for the server to be considered available.<br/>OR-One of the specified health checks must pass for the server to be considered available.|
|mysql_group_id|no|0| | |
|mysql_read_only|no|disable| | |
|vdom|no| | | |

## fadcos_nat_pool
  * Synopsis
  * Options
  * Examples
#### Synopsis
You use the Source Pool page to create configuration objects for source IP addresses used for NAT in Layer 4 virtual server configurations.

#### Options
| parameter     | required    | default  | choices    | comments |
| ------------- |-------------| ---------|----------- |--------- |
|action|yes| |<ul> <li>add</li>  <li>edit</li>  <li>delete</li>  <li>get</li> </ul>| |
|name|no| | | |
|interface|no| | |Interface to receive responses from the backend server. The interface used for the initial client traffic is determined by the virtual server configuration.|
|iptype|no| |<ul> <li>ipv4</li>  <li>ipv6</li> </ul>|IPv4 or IPv6|
|ipstart|no| | |The first address in the address pool.|
|ipend|no| | |The last address in the address pool.|
|vdom|no| | | |

## fadcos_nat_pool_member
  * Synopsis
  * Options
  * Examples
#### Synopsis
Create a node member list to be used in an HA active-active deployment. In an active-active deployment, node interfaces are configured with a list of IP addresses for all nodes in the cluster. You use this configuration to provision SNAT addresses for each of the nodes.

#### Options
| parameter     | required    | default  | choices    | comments |
| ------------- |-------------| ---------|----------- |--------- |
|action|yes| |<ul> <li>add</li>  <li>edit</li>  <li>delete</li>  <li>get</li> </ul>| |
|natpool_name|yes| | | |
|name|no| | | |
|interface|no| | |Interface to receive responses from the backend server. The interface used for the initial client traffic is determined by the virtual server configuration.|
|pooltype|no| |<ul> <li>ipv4</li>  <li>ipv6</li> </ul>|IPv4 or IPv6|
|ipmin|no| | |The first address in the address pool.|
|ipmax|no| | |The last address in the address pool.|
|vdom|no| | | |

## fadcos_virtual_server_basic
  * Synopsis
  * Options
  * Examples
#### Synopsis
FortiADC provides two options for configuring virtual servers?Basic Mode and Advanced Mode.

In Basic Mode, you are required to specify only the basic parameters needed to configure a virtual server. FortiADC automatically configures those advanced parameters using the default values when you click the Save button. The Basic Mode is for less experienced users who may not have the skills required to configure the advanced features on their own.

#### Options
| parameter     | required    | default  | choices    | comments |
| ------------- |-------------| ---------|----------- |--------- |
|name|yes| | |Specify a unique name for the virtual server configuration object. Valid characters are A-Z, a-z, 0-9, _ , and -. No space is allowed.|
|application|yes| | | |
|address|yes| | |IP address provisioned for the virtual server.|
|interface|yes| | |Network interface that receives client traffic for this virtual server.|
|pool|yes| | |Specify a server pool configuration object.|
|port|yes| | |Port number to listen for client requests.|
|ssl|yes|disable| |Applicable to HTTP(S) applications only.|
|ssl_profile|yes| | |Select a client SSL profile|
|vdom|no| | | |

## fadcos_virtual_server
  * Synopsis
  * Options
  * Examples
#### Synopsis
FortiADC provides two options for configuring virtual servers?Basic Mode and Advanced Mode.

The Advanced Mode, on the other hand, is ideal for experienced or "power" users who are knowledgeable and comfortable enough to configure all the advanced features, in addition to the basic ones, on their own.

#### Options
| parameter     | required    | default  | choices    | comments |
| ------------- |-------------| ---------|----------- |--------- |
|action|yes| |<ul> <li>add</li>  <li>edit</li>  <li>delete</li>  <li>get</li> </ul>| |
|name|no| | |Specify a unique name for the virtual server configuration object. Valid characters are A-Z, a-z, 0-9, _ , and -. No space is allowed.|
|status|no| |<ul> <li>enable</li>  <li>disable</li>  <li>maintain</li> </ul>| |
|iptype|no| |<ul> <li>ipv4</li>  <li>ipv6</li> </ul>|IPv4 or IPv6|
|ip|no| | |IP address provisioned for the virtual server.|
|public_ip|no| | |Virtual server public IP address.|
|public_iptype|no|ipv4|<ul> <li>ipv4</li>  <li>ipv6</li> </ul>|IPv4 or IPv6|
|interface|no| | |Network interface that receives client traffic for this virtual server.|
|vstype|no| |<ul> <li>l2-load-balance</li>  <li>l4-load-balance</li>  <li>l7-load-balance</li> </ul>| |
|pool|no| | |Specify a server pool configuration object.|
|port|no|80| |Port number to listen for client requests.|
|profile|no| | |Specify a predefined or user-defined profile configuration object.|
|method|no|LB_METHOD_ROUND_ROBIN| |Specify a predefined or user-defined method configuration object.|
|ssl_mirror|no|disable| |Enable/disable SSL mirroring. When ssl-mirror is enabled, FortiADC will mirror the client HTTPS/TCPS packets traffic by the SSL-mirror-interface port after decrypting the SSL.|
|ssl_mirror_intf|no| | |Specify the outgoing interfaces be ssl-mirror interfaces. You can set up to four outgoing interfaces.|
|traffic_group|no|default| | |
|traffic_log|no|disable| |Enable to record traffic logs for this virtual server.|
|trans_rate_limit|no|0| |Limit the number of HTTP or SIP requests per second. The default is 0 (disabled). The valid range is 1 to 1,048,567 transactions per second.|
|warmrate|no|100| |Maximum connection rate while the virtual server is starting up. The default is 10 connections per second. The valid range is 1 to 86,400 connections per second.|
|warmup|no|0| |If the server cannot initially handle full connection load when it begins to respond to health checks (for example, if it begins to respond when startup is not fully complete), indicate how long to forward traffic at a lesser rate. The default is 0 (disabled). The valid range is 1 to 86,400 seconds.|
|alone|no|enable| |Enable/disable alone mode. Enabled by default.|
|av_profile|no| | | |
|client_ssl_profile|no| | | |
|clone_pool|no| | |Specify the clone-pool.|
|clone_traffic_type|no| | |Specify the clone-traffic-type.|
|connection_limit|no|0| |Limit the number of concurrent connections. The default is 0 (disabled). The valid range is 1 to 1,048,576 concurrent connections.|
|connection_rate_limit|no| | |With all Layer 4 profiles, and with the Layer 2 TCP profile, you can limit the number of new connections per second. The default is 0 (disabled). The valid range is 1 to 86,400 connections per second.|
|content_rewriting|no|disable| |Enable to rewrite HTTP headers.|
|content_rewriting_list|no| | |Specify content rewriting rules.|
|content_routing|no|disable| |Enable to route packets to backend servers based on IP address (Layer 4) or HTTP headers (Layer 7 content).|
|content_routing_list|no| | |Specify content route configuration objects.|
|schedule_list|no|disable| |Enable/disable schedule pool list.|
|schedule_pool_list|no| | |Specify the schedule-pool.|
|scripting_flag|no|disable| | |
|scripting_list|no| | |Specify a scripting policy configuration object. HTTP/HTTPS only.|
|source_pool_list|no| | | |
|waf_profile|no| | | |
|http2https|no| | |Enable/disable redirect HTTP request to HTTPS|
|http2https_port|no| | |HTTP service port list for redirecting HTTP to HTTPS.|
|l2_exception_list|no| | |Specify a user-defined SSL forward proxy exception configuration object.|
|packet_fwd_method|no| | |In Layer 4 virtual server deployments, select one of the following packet forwarding methods:|
|pagespeed|no| | |Set PageSpeed to let FortiADC speed up HTTP responses using its Web Performance Optimization solutions.|
|persistence|no| | |Select a predefined or user-defined persistence configuration object. See Configuring persistence rules.|
|protocol|no| | | |
|adfs_published_service|no| | | |
|error_msg|no|Server-unavailable| |Specify an error page configuration object.|
|error_page|no| | |If you do not use an error page, you can enter an error message to be returned to clients in the event no server is available.|
|fortiview|no|disable| | |
|wccp|no|disable| | |
|comments|no| | | |
|vdom|no| | | |

