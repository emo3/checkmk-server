# checkmk

Here are two examples of where to get the free version:<br>
This for RHEL/CentOS only<br>
<code>
osv=8 # Version of RHEL/CentOS
cmkv='2.0.0p5' # Version of checkmk server
wget https://download.checkmk.com/checkmk/${cmkv}/check-mk-raw-${cmkv}-el${osv}-38.x86_64.rpm
</code>
My local server to get pre-packaged agent<br>
<code>
http://checkmks/cmk/check_mk/agents/check-mk-agent-${cmkv}-1.noarch.rpm
curl "http://checkmks/cmk/check_mk/webapi.py?action=get_all_hosts&_username=automation&_secret=$akey"
</code>
Creating a host:<br>
<code>
curl "http://checkmks/cmk/check_mk/webapi.py?action=add_host&_username=automation&_secret=$akey" -d 'request={"hostname":"checkmks","folder":"","attributes":{"ipaddress":"10.1.1.20","site":"cmk","tag_agent":"cmk-agent"}}'
</code>
Executing a Service Discovery<br>
<code>
curl "http://checkmks/cmk/check_mk/webapi.py?action=discover_services&_username=automation&_secret=$akey" -d 'request={"hostname":"checkmks"}'
</code>
Activating changes
<code>
curl "http://checkmks/cmk/check_mk/webapi.py?_secret=$akey&_username=automation&action=activate_changes" -d 'request={"sites":["cmk"]}'
</code>
