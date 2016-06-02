#How packet flow between machine M and Facebook.com#
1. Machine has ip = ip1
   * If it doesnt have ip
      * Machine will make UDP Request on port 67 ( DHCP Discovery) which will be        broadcast. All the machine will read the packets and only dhcp 
        server/relay-agent will processes the request. If the dhcp server is not        in the subnet then in that case there need to be dhcp relay agent in the        subnet.
      * If The discover request of the client if the gateway ip in the request header is not set then relay agenet adds that as address of itself
Then it forwards request to dhcp server
The dhcp server then leases the ip for the requesting machine ( may be based on scope defined based on gateway ip) and send response back to relay agent
The relay agent then sends back the response to the client
The dhcp server will lease the ip and send response to client

