# DHCP_loadbalancing

Specific case when 2 separate gateways have to be used inside the same network segment.
This Class load balances trafic based on parity of MAC Address' last byte.

Using ISC dhcpd.

Odd : match if ((extract-int (suffix (pick-first-value (option dhcp-client-identifier, hardware), 1), 8) % 2) = 1);	 	￼
Even : match if ((extract-int (suffix (pick-first-value (option dhcp-client-identifier, hardware), 1), 8) % 2) = 0);
