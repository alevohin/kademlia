Kademlia
========

# Description
This is a basic DHT implementation using the Kademlia routing protocol. It's not an implementation of a full Kademlia node.
You can find an example implementation of a Kademlia node here: https://github.com/cgrotz/kademlia-example

# Usage
Simply include Kademlia as a dependency in your code:
```xml
<dependency>
    <groupId>de.cgrotz</groupId>
    <artifactId>kademlia</artifact>
    <version>1.0.1</version>
</dependency>
```

```java
// In production the nodeId would preferably be static for one node
Kademlia kad = new Kademlia(new NodeId(), "127.0.0.1", 9000);
// Bootstrap using a remote server (there is no special configuration on the remote server necessary)
kad.bootstrap("127.0.0.1", 9001);
// Store a key/value pair in the DHT
kad.put("key", "value");
// Retrieve a key/value pair from the DHT
kad.get("key", value -> { ... });
// Or synchronously with
kad.get("key");
```

See the [Getting Started](docs/Getting_Started.md) guide for more information. [Protocol](docs/protocol.md) gives you information on the protocol.

# Open Points
- [ ] Extend Testing
- [x] Bucket Refreshing
- [x] Key Republishing
- [x] Client retry behavior
- [ ] Caching
- [ ] Store value as continuous log of events?
- [ ] Provide TLS encryption with Key Exchange for inter node communication
- [ ] provide local Unix Domain Socket interface for IPC
- [ ] Switchable local storage implementation (e.g. to enable other storage engines like Levels DB)

# Credit goes to
Joshua Kissoon and his work on Kademlia where I took inspiration from. https://github.com/JoshuaKissoon/Kademlia
His great blog post: http://gleamly.com/article/introduction-kademlia-dht-how-it-works
