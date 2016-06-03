#How packet flow between machine M and Facebook.com#
1. Machine has ip = ip1
   * If it doesnt have ip
      * Machine will make UDP Request on port 67 ( DHCP Discovery) which will be        broadcast. All the machine will read the packets and only dhcp 
        server/relay-agent will processes the request. If the dhcp server is not        in the local network then in that case there need to be dhcp relay agent in the local network.
      * If there is DHCP relay agent in the network, then it will remove 0.0.0.0 from the source ip field of the request and add its own IP in the request. It will forward this request to the DHCP Server. The dhcp server then leases the IP and forward the response message to the DHCP relay agent. The relay agent will unicast this response the requesting machine M.
      * The machine M will process the request and will set its IP to the one provided by the DHCP server.
2. 
