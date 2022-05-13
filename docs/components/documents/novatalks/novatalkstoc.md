#NovaTalks
###Flowcharts
###Conversation flow
###Incoming message


``` mermaid
graph TB
  A{Customer IM} --> |IM proprietary Protocol| B[Messenger]
  B -->|IM Webhook Communication Protocol| C[Webhook URL for incoming messages]
  C --> |:443| D[Reverse-Proxy - e.g. enginx]
  D --> E[BotConnector - unification]
  subgraph Nova.ChatsConnector
  E -->|:8080| F[ChatProxy - de-unification]
  E & F -->|:27017| J[(MongoDB - Database)]
  end
  F --->|:500X| G[Internal System: Genesys - PureConnect, PureEngage, PureCloud, Cisco - UCCE, UCCX, NovaIT - Nova.Chats]
  G -->  H[Operator]
```

###Outgoing message