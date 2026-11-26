# Security policy

## Reporting a security problem

If you find a security problem in Bolometrix, for example in its web page, its remote commands, Modbus TCP, OPC UA, MQTT, the video stream, the phone link or the AI link, please do not open a public issue. Write to **derekholzapfel@gmail.com** instead, with:

- the Bolometrix version (Help → About) and the system it runs on,
- what someone could do with the problem, and how to make it happen,
- anything else that helps to understand it.

Please allow a reasonable time for a fix before you tell others about it.

## Supported versions

Fixes come in the newest version only. Install the [latest release](https://github.com/derekownsall/bolometrix/releases/latest) to get them.

## How Bolometrix comes set up

Every network function is off until you switch it on, and one that listens (the web page, remote commands, Modbus TCP, OPC UA, the video stream, the phone link) stays on the PC itself (`127.0.0.1`) until you choose the network; the AI link uses a named pipe open only to its Windows user. Browser HTTP requests on the TCP remote-command port and cross-host browser `Origin` headers on the phone link are refused, and an optional `AUTH <password>` gate on the TCP command port fails closed if its stored secret cannot be read. `For-IT-departments.txt`, beside every release, lists every port and every outgoing connection.

Each release ships an offline ECDSA P-256 signature (`SHA256SUMS.txt.sig`) over `SHA256SUMS.txt` (including its `# Bolometrix <version>` header), which **Help → Check for a newer version** verifies offline against embedded public keys while refusing HTTP redirects off GitHub hosts before keeping any download.
