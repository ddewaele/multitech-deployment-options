Some MultiTech deployment options

![](https://raw.githubusercontent.com/ddewaele/multitech-deployment-options/master/a-single-conduit-packetfw-loraserver.png)

- This is a typical setup for small scale deployments. 
- However, if certain sensors fall out of range another solution is needed.

![](https://raw.githubusercontent.com/ddewaele/multitech-deployment-options/master/b-multiople-conduits-single-lora-server.png)

- Here, extra Conduits would be used as range extenders and these extra conduits are setup as packet forwarder to 1 Single Conduit that runs the lora server. 
- The single Conduit acting as a Lora Network server accepts remote connections from the packet forwarders on its UDP ports.
- This single conduit could be considered a single point of failure, and it is difficult to setup Lora Servers on Conduits in high-available mode.


![](https://raw.githubusercontent.com/ddewaele/multitech-deployment-options/master/c-multiple-gateways-single-lora-server.png)

- Small variation from the previous deployment. 
- Here, multiple gateways are deployed only this time both Conduits and other off-the-shelf gateways). 
- They all act as packet forwarders and 1 Conduit is configured a the Lora server. It will contain the "known" sensor config, handle de-duplication / decryption of payloads. 
- This single Lora Server would be a single point of failure and could become a potential bottleneck as it is difficult (or even impossible) to scale. 
- having multiple lora servers in the architecture would lead to issues upstream I guess ? duplicate messages and such.

![](https://raw.githubusercontent.com/ddewaele/multitech-deployment-options/master/d-multiple-gateways-external-lora-server.png)

- Here, the Lora Server runs in the cloud and all Conduits are setup as packet forwarders. 
- The cloud based lorawan server will contain the "known" sensor config, handle de-duplication / decryption of payloads
- The advantage here would be a more robust LoRaWAN architecture where proper failover can be configured in the cloud.
