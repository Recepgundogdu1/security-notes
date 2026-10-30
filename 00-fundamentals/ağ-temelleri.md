# Ağ Temelleri

CCNA tabanım var; burası siber açısından kritik olan ağ bilgisi özeti.
Pentest = ağı anlamak. Hedefin neyi nasıl konuştuğunu bilmeden saldıramazsın.

## OSI vs TCP/IP
| OSI (7) | TCP/IP (4) | Örnek |
|---------|-----------|-------|
| Application/Presentation/Session | Application | HTTP, DNS, SSH |
| Transport | Transport | TCP, UDP |
| Network | Internet | IP, ICMP |
| Data Link/Physical | Network Access | Ethernet, MAC |

## TCP vs UDP
- **TCP**: bağlantı kurar (3-way handshake), güvenilir, sıralı. Web, SSH, FTP.
- **UDP**: bağlantısız, hızlı, garanti yok. DNS, DHCP, VoIP.

### TCP 3-Way Handshake
