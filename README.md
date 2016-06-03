#How packet flow between machine M and Facebook.com#
1. Machine has ip = ip1
   * If it doesnt have ip
      * Machine will make UDP Request on port 67 ( DHCP Discovery) which will be        broadcast. All the machine will read the packets and only dhcp 
        server/relay-agent will processes the request. If the dhcp server is not        in the local network then in that case there need to be dhcp relay agent in the local network.
      * If there is DHCP relay agent in the network, then it will remove 0.0.0.0 from the source ip field of the request and add its own IP in the request. It will forward this request to the DHCP Server. The dhcp server then leases the IP and forward the response message to the DHCP relay agent. The relay agent will unicast this response the requesting machine M.
      * The machine M will process the request and will set its IP to the one provided by the DHCP server.
2. To talk to facebook.com client browser issues GET request.
   * The OS tries to find the ip for the host name by invoking getHostByName() method. 
   * This makes the client to ask local DNS service to check whether it has record for facebook.com cached in its database.
   * If the client fails to find the record it makes DNS request to the preferred DNS server configured on the machine.
   * The DNS server operates are of two types
      * Recursive:
        * It will ask to its peer1 for facebook.com
        * Peer1 responds with "try 12.12.12.12"
        * DNS server then sends DNS request to 12.12.12.12
        * 12.12.12.12 replies with the IP of facebook.com
        * DNS server then cache that entry in its DB.
        * And it will send the response to the client M
      * Iterative:
        * Server will ask to its peer for facebook.com
        * Peer responds with "try 12.12.12.12"
        * Server sends response to client as "try 12.12.12.12"
        * Client sends DNS request to 12.12.12.12 and so on.
        * In this case client has to try untill it finds the IP of facebook.com
   * After retrieving IP from the DNS server the DNS client will cache the response and returns the IP address for the facebook.com to the OS
   
