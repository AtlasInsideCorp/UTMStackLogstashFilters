## V9 files reference
Lists all files present in this version and some relevant documentation about it

### Filter´s table
| File path | dataType | Tests | Supported Input format | Example |
|--------|--------|--------|--------|--------|
|antivirus\esmc-eset.conf|antivirus-esmc-eset|Local, SIEM|Syslog+JSON|679 <12>1 2022-04-11T10:41:05.300Z esmc ERAServer 11804 - - {"event_type":"FirewallAggregated_Event","ipv4":"x.x.x.x","hostname":"archivos","source_uuid":"c252c742-22e4-4b4c-af89-6216dc200276","occured":"11-Apr-2022 10:45:38","severity":"Warning",...}|
|antivirus\kaspersky.conf|antivirus-kaspersky|Local|Syslog+CEF|677 <12>1 2021-10-22 13:12:19.014 localhost=127.0.0.1 14 CEF: 0(Pipe)Kaspersky(Pipe)Kaspersky Endpoint Security for Windows(Pipe)10.2.5.3201(Pipe)GNRL_EV_SUSPICIOUS_OBJECT_FOUND(Pipe)Probably infected object detected(Pipe)Very-High(Pipe) eventId=168010884486 externalId=1907735613 msg=Result: Detected: not-a-virus:HEUR:RemoteAdmin.Win32.DameWare.gen|
|antivirus\sentinel-one.conf| antivirus-sentinel-one|Local, SIEM|Syslog, Syslog+CEF|1. <38>1 2022-05-02T15:53:10.288601Z x.x.x.x SentinelOne f37ae7e9fe1441b49021b4f9f1b4b331 1411618095558471028 [fileName@53163 fileName="ryuk.bin"][deviceAddress@53163 deviceAddress="x.x.x.x"]...<br>2. <14>2022-04-26 16:17:22,750 sentinel - CEF:0(Pipe)SentinelOne(Pipe)Mgmt(Pipe)deviceAddress=x.x.x.x deviceHostFqdn=userx-001.sentinelone.net deviceHostName=userx-001.sentinelone.net notificationScope=SITE...|
|antivirus\sophos_av.conf|antivirus-sophos|Local, SIEM|JSON|{"tenant": "Sophos","global": {"type": "logx","analysed": 1},"logx": {"type":"sophos","sophos": {"created_at": "2022-05-05T19:56:08.389Z","customer_id": "82446241-0870-4810-8e60-87cdfba980f3","endpoint_id": "7d4c29e9-ed9d-4d50-9a17-c326e6fe22a8","endpoint_type": "computer","group": "MALWARE","id": "f7f4bdf5-555a-4970-870c-6547a533cb53","location": "host","name": "Malware cleaned up: 'EICAR-AV-Test' at 'C:\\eicar_com (1).zip'","origin": null,"severity": "low","source": "testsource","source_info": {"ip": "x.x.x.x"}}}}|
|aws\aws.conf|aws|Local|JSON|-|
|azure\azure-eventhub.conf|azure|Local, SIEM|JSON, JSON Array|{"subject":"/subscriptions/32ed728b-18b4-40c4-a447-4c9fef913fa7/resourcegroups/demo_group/providers/Microsoft.Compute/virtualMachines/demo-test","type":"azure","eventType":"Microsoft.Resources.ResourceActionSuccess",...}|
|cisco\asa.conf|firewall-cisco-asa|Local, PNB|Syslog|<166>Jan 31 2022 14:45:42 PC-host : %ASA-6-113008: AAA transaction status ACCEPT : user = tsan|
|cisco\firepower.conf|firewall-cisco-firepower|Local|Syslog|<166>Jan 31 2022 14:45:42 PC-host : %FTD-6-113008: AAA transaction status ACCEPT : user = tsan|
|cisco\meraki.conf|firewall-meraki|Local|Syslog|1. <166>Jan 31 2022 15:05:50 PC-host : Dec 6 08:45:24 192.168.1.1 1 1386337535.803931423 MX84 events failover to wan1 <br>2. <166>Jan 31 2022 15:05:50 PC-host : 1374543986.038687615 MX84 flows src=192.168.1.186 dst=8.8.8.8 mac=58:1F:AA:CE:61:F2 protocol=tcp/ip sport=55719 dport=53 pattern: allow all <br>3. <166>Jan 31 2022 15:05:50 PC-host : 1578426208.829677788 labs_Z1 events Site-to-site VPN: failed to get sainfo|
|filebeat\apache_module.conf|apache or apache2|Local|Filebeat (beats) with:<br>1. fileset: access = Syslog <br>2. fileset: error = Syslog|1. 192.168.1.25 - - [14/Feb/2022:15:38:07 -0500] "GET / HTTP/1.1" 200 11450 <br>2. [Wed Oct 11 14:32:52 2000] [error] [client 127.0.0.1] client denied by server configuration: /export/home/live/ap/htdocs/test|
|filebeat\auditd_module.conf|auditd|Local|Filebeat (beats) with:<br>1. fileset: log = plain text|type=CWD msg=audit(1364481363.243:24287):  cwd="/home/shadowman"|
|filebeat\elasticsearch_module.conf|elasticsearch|Local|Filebeat (beats) from <i>++elasticsearch 7++++</i> with:<br>1. fileset: server = (log4j appenders) json<br>2. fileset: audit = (log4j appenders) json<br>3. fileset: deprecation = (log4j appenders) json<br>4. fileset: slowlog = (log4j appenders) json<br>5. fileset: gc = plain text|1. {"type": "server", "timestamp": "2022-02-22T11:18:13,271-05:00", "level": "INFO", "component": "o.e.n.Node", "cluster.name": "elasticsearch", "node.name": "MyHost", "message": "version[7.14.1], pid[12300], OS[Windows 10/10.0/amd64], JVM[Eclipse Adoptium/OpenJDK 64-Bit Server VM/11.0.13/11.0.13+8]" } <br>2. {"type":"audit", "timestamp":"2022-02-23T15:25:12,005-0500", "event.type":"transport", "event.action":"access_granted", "request.name":"StartJoinRequest"} <br>3. {"type": "deprecation", "timestamp": "2022-02-16T11:38:56,446-05:00", "level": "DEPRECATION", "component": "o.e.d.c.s.Settings", "cluster.name": "elasticsearch", "node.name": "MyHost", "message": "[node.max_local_storage_nodes] setting was deprecated in Elasticsearch and will be removed in a future release!"} <br>4. {"type": "index_search_slowlog", "timestamp": "2022-02-22T09:59:37,427-05:00", "level": "WARN", "component": "i.s.s.query", "cluster.name": "elasticsearch", "node.name": "MyHost", "message": "[anexo1_plant_admon][0]", "took": "41.4ms", "took_millis": "41", "total_hits": "0 hits", "types": "[]", "stats": "[]",...} <br>5. [2022-01-21T03:29:52.878+0000][6780][gc] Using Concurrent Mark Sweep|
|filebeat\kafka_module.conf|kafka|Local|Filebeat (beats) from <i>++Apache Kafka kafka_2.13-3.1.0++</i> with:<br>1. fileset: (log: any kind of kafka logs, like: server, controller, log-cleaner and so on) = (log4j appenders) plain text|1. [2022-03-03 22:29:48,486] INFO Reading configuration from: zookeeper.properties (org.apache.zookeeper.server.quorum.QuorumPeerConfig)|
|filebeat\kibana_module.conf|kibana|Local|Filebeat (beats) from <i>++kibana++</i> with:<br>1. fileset: log = (log4j appenders) json<br>2. fileset: audit = (log4j  appenders) json|1. {"ecs":{"version":"1.9.0"},"@timestamp":"2022-02-23T22:32:07.121-05:00","message":"Marking config path as handled: path","log":{"level":"DEBUG","logger":"config"},"process":{"pid":12028}} <br>2. {"type":"audit", "timestamp":"2022-01-25T09:40:38,604-0500", "event.action":"access_granted", "user.name":"thom", "user.roles":["superuser"], "request.id":"YCx8wxs...", "action":"cluster:admin/xpack/security/user/authenticate", "request.name":"AuthenticateRequest", "opaque_id":"818cbf3..."}|
|filebeat\logstash_module.conf|logstash|Local|Filebeat (beats) from <i>++logstash (executed with param - -log.format=json)++</i> with:<br>1. fileset: log = json<br>2. fileset: slowlog = json|1. {"level":"INFO","loggerName":"logstash.javapipeline","timeMillis":1645656556918,"thread":"[main]-pipeline-manager","logEvent":{"message":"Pipeline terminated","pipeline.id":"main"}}<br> 2. {"level":"WARN","loggerName":"slowlog.logstash.filters.mutate","timeMillis":1645802911751,"thread":"[main]>worker0","logEvent":{"message":"event processing time",...}...}|
|filebeat\mongodb_module.conf|mongodb|Local|Filebeat (beats) from <i>++MongoDB 4.4++++</i> with:<br>1. fileset: log = json|1. {"t":{"$date":"2020-05-18T20:18:12.724+00:00"},"s":"I",  "c":"CONTROL",  "id":23285,   "ctx":"main","msg":"Automatically disabling TLS 1.0, to force-enable TLS 1.0 specify --sslDisabledProtocols 'none'"}|
|filebeat\mysql_module.conf|mysql|Local|Filebeat (beats) from <i>++MySQL++</i> with:<br>1. fileset: error = (MySQL 8.0++) json <br>2. fileset: error = (Older versions) plain text <br>3. fileset: slowlog = plain text|1. {"prio": 0,"err_code": 10052,"source_line": 561,"source_file": "event_scheduler.cc","function": "run","msg": "Event Scheduler: scheduler thread started with id 5","time": "2020-08-06T14:25:03.109022Z","ts": 1596724012005,"thread": 5,"err_symbol": "ER_SCHEDULER_STARTED","SQL_state": "HY000","subsystem": "Server","buffered": 1596723903109022}<br>2. 2022-02-28 10:17:57 18912 [Note] Plugin 'FEDERATED' is disabled.<br>3. c:\xampp\mysql\bin\mysqld.exe, Version: 5.6.21-log (MySQL Community Server (GPL)). started with: TCP Port: 3306, Named Pipe: C:/xampp/mysql/mysql.sock Time Id Command Argument|
|filebeat\nginx_module.conf|nginx|Local|Filebeat (beats) from <i>++nginx 1.21.6++</i> with:<br>1. fileset: access = plain text <br>2. fileset: error = plain text <br>3. fileset: ingress-controller = plain text|1. 127.0.0.1 - - [28/Feb/2022:18:00:25 -0500] "GET / HTTP/1.1" 200 615 "-" "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/98.0.4758.102 Safari/537.36" <br>2. 2022/02/28 17:47:34 [error] 17876#21856: CreateFile() "D:\INSTALL\WINDOWS\nginx-1.21.6\nginx-1.21.6/logs/nginx.pid" failed (2: El sistema no puede encontrar el archivo especificado)|
|filebeat\osquery_module.conf|osquery|Local|Filebeat (beats) from <i>++osquery 5.2.2++++</i> with:<br>1. fileset: result = json|1. {"name":"system_info","hostIdentifier":"MyHost","calendarTime":"Sat Mar  5 01:33:29 2022 UTC","unixTime":1646444009,"epoch":0,"counter":0,"numerics":false,"decorations":{"host_uuid":"4C4C4544-0039-4710-805A-B6C04F4D3332","username":"user1"},"columns":{"cpu_brand":"Intel(R) Core(TM) i5-4310M CPU @ 2.70GHz","hostname":"MyHost","physical_memory":"8589934592"},"action":"added"}|
|filebeat\postgresql_module.conf|postgresql|Local|Filebeat (beats) from <i>++PostgreSQL 14.2++++</i> with:<br>1. fileset: log = plain text|1. 2022-02-15 19:43:52.364 UTC [25] LOG:  database system was shut down at 2022-02-11 20:01:30 UTC <br> 2. Mar 24 14:58:08 webappsecure postgres[7694]: [10-2] 42701 530b5e00.1e0e STATEMENT: ALTER TABLE sessiongroup ADD COLUMN requests bigint|
|filebeat\redis_module.conf|redis|Local|Filebeat (beats) from <i>++redis (Supports older 2.x log versions to latter 6.2.6)++</i> with:<br>1. fileset: log = plain text <br>2. fileset: slowlog = plain text|1. 1:C 07 Mar 2022 20:35:06.345 . oO0OoO0OoO0Oo Redis is starting oO0OoO0OoO0Oo <br>2. [4018] 14 Nov 07:01:22.119 * Background saving terminated with success|
|filebeat\system_linux_module.conf|linux|Local|Filebeat (beats) from <i>++linux++</i> with:<br>1. fileset: syslog = plain text <br>2. fileset: auth = plain text|<30>Apr  6 10:38:00 gateway1 filebeat[53008]: 2022-04-06T10:38:00.802Z#011INFO#011[monitoring]#011log/log.go:184#011Non-zero metrics in the last 30s#011{"monitoring": {"metrics": {"beat":{"cgroup":{"cpuacct":{"total":{"ns":808966516}}},"cpu":{"system":{"ticks":2616400,"time":{"ms":49}},"total":{"ticks":54651200,"time":{"ms":807},"value":54651200},"user":{"ticks":52034800,"time":{"ms":758}}},"handles":{"limit":{"hard":524288,"soft":1024},"open":24},"info":{"ephemeral_id":"d8454b34-75e8-45c6-b2bc-756b12768489","uptime":{"ms":1773063104},"version":"7.17.1"},"memstats":{"gc_next":63152992,"memory_alloc":34813544,"memory_total":2612752313136,"rss":83849216},"runtime":{"goroutines":101}},"filebeat":{"harvester":{"open_files":12,"running":8}},"libbeat":{"config":{"module":{"running":2}},"output":{"events":{"active":0,"batches":23,"failed":47104,"total":47104},"read":{"errors":3}}}}}}}|
|fortinet\fortinet.conf|firewall-fortigate-traffic|Local, ENB|Syslog|<190>date=2022-04-06 time=22:42:40 devname="estb-miam01fl-200d-1" devid="FG200D3913805254" logid="0101039943" type="event" subtype="vpn" level="information" vd="root" eventtime=1649281360 logdesc="SSL VPN new connection" action="ssl-new-con" tunneltype="ssl" tunnelid=0 remip=13.88.28.180 user="N/A" group="N/A" dst_host="N/A" reason="N/A" msg="SSL new connection"|
|google\google-logstash.conf|google|Local, SIEM|JSON|1. {"insertId":"1fc9ikwg2sx8lyp","jsonPayload":{"localTimestamp":"2021-09-27T17:48:41.8074Z","message":"Instance ID changed, running first-boot actions"},"logName":"projects/formidable-byte-326819/logs/GCEGuestAgent","receiveTimestamp":"2021-09-27T17:48:42.255430762Z","resource":{"labels":{"instance_id":"3109684401449975050","project_id":"formidable-byte-326819","zone":"us-central1-a"},"type":"gcp"},"severity":"INFO","sourceLocation":{"file":"instance_setup.go","function":"main.agentInit","line":"179"},"timestamp":"2021-09-27T17:48:41.807512691Z"}|
|hids\hids-wazuh.conf|hids|-|JSON|-|
|netflow\netflow.conf|netflow|SIEM|JSON|-|
|nids\nids-ids.conf|nids|Local, SIEM|JSON (Suricata 7.0.0)|1. {"timestamp":"2022-04-11T15:54:05.263088+0000","flow_id":182732858393520,"in_iface":"ens3","event_type":"dns","src_ip":"x.x.x.x","src_port":33651,"dest_ip":"x.x.x.x","dest_port":53,"proto":"UDP","dns":{"type":"query","id":50404,"rrname":"srv1.cloudapp.azure.com","rrtype":"A","tx_id":0}}|
|office365\o365-all.conf|o365|-|JSON|-|
|sophos\sophos_xg_firewall.conf|firewall-sophos-xg|Local|Syslog|1. <30>device="SFW" date=2022-01-29 time=12:01:32 timezone="-03" device_name="XG45" device_id=C4307BHT log_id=054402617051 log_type="Content Filtering" log_component="Application" log_subtype="Denied" priority=Information fw_rule_id=156 user_name="tst@mail.com" user_gp="GR_MACRO" application_filter_policy=5 category="P2P" application_name="Torrent Clients P2P" application_risk=5 application_technology="P2P" application_category="P2P" src_ip=x.x.x.x src_country_code=R1 dst_ip=x.x.x.x dst_country_code=PHL protocol="UDP" src_port=58631 dst_port=60438 sent_bytes=0 recv_bytes=0 status="" message="" appresolvedby="Signature" hytest|
|vmware\vmware-esxi.conf|vmware-esxi|Local|Syslog|1. <166>2022-06-07T23:50:09.785Z myhost.local hostd-probe: quiet hostd-probe[2101754] [Originator@6876 sub=Default] Successfully acquired advanced option: UserVars.ESXiShellTimeOut = 0 <br> 2. <14>2022-06-07T23:50:00.573Z myhost.local crx-cli[4519096]: Log for VMware ESXi version=7.0.3 build=build-19193900 option=Release|
|windows\windows-events.conf|wineventlog|SIEM|JSON by beats|-|
|windows\windows-iis.conf|iis|-|JSON by beats|-|

#### Notes:
1. (Pipe) is used in CEF examples instead of | character because have conflicts with markdow´s table
2. About filebeat modules, the **Supported Input format** column shows the input format expected by filebeat for every fileset in the module configured. The filter always must receive a single JSON from filebeats