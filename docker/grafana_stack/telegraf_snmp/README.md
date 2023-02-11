# Telegraf with SNMP

My telegraf config relies on SNMP to poll metrics from nodes. The default provided docker image does not include SNMP. The dockerfile provided adds SNMP support to the image. You will need to include MIBs relevant to the device that you are monitoring.