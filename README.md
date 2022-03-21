# PyPeerChat
TCP Socket Based Centralized Customizable Chat Platform

# All Event Flags
## All Constructed Payloads are Parsed Using Json
### Ex: {'flag': 10, 'content': 'MESSAGE CONTENT; TO_USER_ID', 'from': 'FROM_SENDING_USER_ID'}
```
| Flag  (hex|int) | Flag Name                 | Flag Content Structure | From Id Needed |
| --------------- |:-------------------------:|:----------------------:|----------------|
| 0xA          10 | CLIENT_SEND_MSG           | MESSAGE;ID             | True           |
| 0xB          11 | CLIENT_RECV_MSG           | MESSAGE                | True           |
| 0xC          12 | CLIENT_UPDATE_NAME        | NAME  : 24             | True           |
| 0xD          13 | CLIENT_UPDATE_MOTTO       | MOTTO : 256            | True           |
| 0xEE        238 | GENERAL_ERROR             | ERROR                  | True           |
| 0xAA        170 | CLIENT_RECEIVE_KEY        | CLIENT AES KEY         | True           |
| 0xAB        171 | CLIENT_SEND_KEY           | SERVER AES KEY         | False          |
| 0xBA        186 | INVOKE_CLIENT_NOTIFICATION| MESSAGE                | False          |
| 0xCD        205 | CLIENT_LIST_UPDATE        | [(CLIENT_ID, USERNAME)]| False          |
```

# Run Commands
```
Server Side -
  python(3) HostingStartup.py [--debug 0|1] [--address 0.0.0.0] [--port 1025-65535] [--method tcp] [--max-message-length 2048]
   --method should always be tcp, a future implementation of others will be used
   --max-message-length is how big the CLIENT_SEND_MSG content field can be
   
Client Side -
  python(3) ClientStartup.y [--debug 0|1] [--address IPV4] [--port PORT] [--username USERNAME] [--motto MOTTO]
  
 Enabling Debug will Decrease Performance, This is used by developers
 ```
