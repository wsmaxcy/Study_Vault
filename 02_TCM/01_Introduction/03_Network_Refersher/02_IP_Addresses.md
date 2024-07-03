```
ifconfig
```
Gives out the following
 - IPV4 - decimal
 - IPV6 - Hex
X.X.X.X = 32 bits, so 8 bits per section, so basically it could be
11111111.11111111.11111111.11111111 = 255.255.255.255

## Binary Overload
| 128 | 64  | 32  | 16  | 8   | 4   | 2   | 1   |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 1   | 1   | 1   | 1   | 1   | 1   | 1   | 1   |
All this added together is 255.255.255.255

## IPv4
$2^{32} = 4,294,967,296$ only that many devices can be online! How do we do this?

| **Network Class**           | Network Numbers                     | Networkd Mask | No. of Networks | No. of Hosts per Network |
| --------------------------- | ----------------------------------- | ------------- | --------------- | ------------------------ |
| **Class A**                 | 10.0.0.0                            | 255.0.0.0     | 126             | 16,646,144               |
| **Class B**                 | 172.16.0.0 through 172.31.0.0       | 255.255.0.0   | 16,383          | 65,024                   |
| **Class C**                 | 192.168.0.0 through 192.168.255.255 | 255.255.255.0 | 2,097,151       | 254                      |
| **LOOPBACK<br>(localhost)** | 127.0.0.0 through 127.0.0.7         | 255.255.255.0 | -               | -                        |

## More Notes
IPv4 (Internet Protocol version 4) and IPv6 (Internet Protocol version 6) are two versions of the Internet Protocol, which is the underlying protocol that enables communication on the internet. They are used to identify and locate devices on a network.

IPv4 addresses are 32-bit numerical addresses represented in a dotted-decimal format, such as "192.168.0.1". Each section, or octet, of the address consists of 8 bits and can range from 0 to 255. This allows for a total of approximately 4.3 billion unique addresses. However, due to the rapid growth of the internet, the number of available IPv4 addresses has become limited, leading to the development of IPv6.

IPv6 addresses are 128-bit addresses represented in a hexadecimal format, such as "2001:0db8:85a3:0000:0000:8a2e:0370:7334". The longer address length of IPv6 allows for a significantly larger number of unique addresses, approximately 3.4×10^38. IPv6 addresses are divided into eight groups of four hexadecimal digits, separated by colons. Leading zeros within a group can be omitted, and consecutive groups of zeros can be represented by a double colon (::) to simplify the address.

The transition from IPv4 to IPv6 is necessary due to the depletion of available IPv4 addresses. IPv6 provides a solution to the address shortage while also introducing improvements in security, auto-configuration, and other features. However, IPv4 and IPv6 are not directly compatible, so various mechanisms and transition technologies exist to enable communication between the two protocols.

In summary, IPv4 and IPv6 are versions of the Internet Protocol that provide unique addresses to devices on a network. IPv4 addresses are 32-bit, while IPv6 addresses are 128-bit. IPv6 offers a larger address space and additional features compared to IPv4.