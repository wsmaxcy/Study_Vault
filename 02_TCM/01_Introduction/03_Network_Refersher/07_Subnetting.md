### IP Config
we have a netmask, normally 255.255.255.0
What is this? its all bits. 8bits.8bits.8bits.8bits
Depending on how these are turned on, these matter. Here is a data sheet that might help

### Cyber Mentor's Subnetting Sheet

|             | Subnet x.0.0.0       |               |             |             |             |            |            |            |
| ----------- | -------------------- | ------------- | ----------- | ----------- | ----------- | ---------- | ---------- | ---------- |
| **CIDR**    | /1                   | /2            | /3          | /4          | /5          | /6         | /7         | /8         |
| **Hosts**   | 2,147,483,648        | 1,073,741,824 | 536,840,912 | 268,435,456 | 134,217,728 | 67,108,864 | 33,554,432 | 16,777,216 |
| **Class A** | Subnet 255.x.0.0     |               |             |             |             |            |            |            |
| **CIDR**    | /9                   | /10           | /11         | /12         | /13         | /14        | /15        | /16        |
| **Hosts**   | 8,388,608            | 4,194,304     | 2,097,153   | 1,048,576   | 524,288     | 262,144    | 161,072    | 65,536     |
| **Class B** | Subnet 255.255.x.0   |               |             |             |             |            |            |            |
| **CIDR**    | /17                  | /18           | /19         | /20         | /21         | /22        | /23        | /24        |
| **Hosts**   | 32,768               | 16,384        | 8,192       | 4,096       | 2,048       | 1,024      | 512        | 256        |
| **Class C** | Subnet 255.255.255.x |               |             |             |             |            |            |            |
| **CIDR**    | /25                  | /26           | /27         | /28         | /29         | /30        | /31        | /32        |
| **Hosts**   | 128                  | 64            | 32          | 16          | 8           | 4          | 2          | 1          |

- /24 Network is typically standard. they give us the 192.168.0.0 - 192.168.0.255, so all ip's on the same 
## Resources for this video:

Resources for this video:

 [Seven Second Subnetting](https://www.youtube.com/watch?v=ZxAwQB8TZsM)

[Subnet Guide](https://drive.google.com/file/d/1ETKH31-E7G-7ntEOlWGZcDZWuukmeHFe/view)

Subnetting is the process of dividing a network into smaller subnetworks called subnets. It allows for more efficient use of IP addresses and facilitates network management and routing. Subnetting is commonly used in IPv4 networks.

Subnetting involves borrowing bits from the host portion of an IP address to create a subnet identifier. By doing this, a network can be divided into multiple subnets, each with its own range of IP addresses.

CIDR (Classless Inter-Domain Routing) notation is a method used to represent IP addresses and their corresponding subnet masks. It specifies the network prefix length, which indicates the number of bits used for the network portion of the IP address. CIDR notation is expressed by appending a forward slash (/) followed by the prefix length to the IP address.

Here's an example to illustrate subnetting and CIDR notation:

Consider an IP address: 192.168.0.0/24

In this example, the IP address is in the format of "192.168.0.0" and the "/24" represents the prefix length, indicating that the first 24 bits represent the network portion of the IP address, while the remaining 8 bits represent the host portion.

With a /24 prefix length, the subnet mask for this network would be 255.255.255.0. This means that the first three octets are reserved for the network, and the last octet can be used for addressing hosts within the subnet.

To subnet this network further, additional bits can be borrowed from the host portion. For instance, if we borrow 2 bits, we can create 4 subnets. The subnet mask would become 255.255.255.192 (in binary: 11111111.11111111.11111111.11000000).

The four resulting subnets would be:

1. Subnet 1: 192.168.0.0/26 (network range: 192.168.0.0 - 192.168.0.63)
2. Subnet 2: 192.168.0.64/26 (network range: 192.168.0.64 - 192.168.0.127)
3. Subnet 3: 192.168.0.128/26 (network range: 192.168.0.128 - 192.168.0.191)
4. Subnet 4: 192.168.0.192/26 (network range: 192.168.0.192 - 192.168.0.255)

Each subnet can then be assigned to a different segment or used for different purposes within the network.

CIDR notation provides a concise way to represent networks and subnets by specifying the prefix length. It allows for flexibility in defining network boundaries and enables efficient address allocation in IP networking.

