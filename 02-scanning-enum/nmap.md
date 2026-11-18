# Nmap

Ağ keşif & port tarama aracı. CTF/pentest'te ilk refleks: hedefte hangi
portlar açık, hangi servisler çalışıyor, sürümleri ne? Nmap bunu söyler.
(TryHackMe Nmap serisinin özeti: Host Discovery + Basic/Advanced/Post scans.)

## 1. Host Discovery (hangi makineler ayakta?)
| Komut | Ne yapar |
|-------|----------|
| `nmap -sn 10.10.10.0/24` | Sadece canlı host bul (port tarama yok, ping sweep) |
| `nmap -PR 10.10.10.0/24` | ARP ping (yerel ağda en güvenilir) |
| `nmap -PE` / `-PP` / `-PM` | ICMP echo / timestamp / address-mask ping |
| `nmap -PS22,80,443` | TCP SYN ping (belirtilen portlara) |
| `nmap -PA80` | TCP ACK ping (root gerekir) |
| `nmap -PU53` | UDP ping |
| `-n` / `-R` | DNS çözümlemesini kapat / zorla |

## 2. Temel Port Taramaları
| Komut | Tür | Not |
|-------|-----|-----|
| `nmap -sT <IP>` | TCP Connect | Tam 3'lü el sıkışma, root gerekmez, "gürültülü" |
| `sudo nmap -sS <IP>` | TCP SYN | "Half-open", hızlı & sessiz, **varsayılan** (root) |
| `sudo nmap -sU <IP>` | UDP | Yavaş ama DNS/SNMP/DHCP için şart |

## 3. Port Seçimi & Performans
| Seçenek | Ne yapar |
|---------|----------|
| `-p-` | Tüm 65535 portu tara |
| `-p1-1023` | 1–1023 aralığı |
| `-p80,443,22` | Belirli portlar |
| `-F` | En yaygın 100 port (hızlı) |
| `-r` | Portları sırayla tara (rastgele değil) |
| `-T0 … -T5` | Hız (T0 en yavaş/gizli, T5 en hızlı/gürültülü) |
| `--min-rate 1000` | Saniyede en az X paket |
| `--max-rate 50` | Saniyede en fazla X paket (gizlilik) |

## 4. Gelişmiş Taramalar (flag manipülasyonu / atlatma)
| Komut | Tür | Mantık |
|-------|-----|--------|
| `sudo nmap -sN` | Null | Hiç flag yok |
| `sudo nmap -sF` | FIN | Sadece FIN |
| `sudo nmap -sX` | Xmas | FIN+PSH+URG |
| `sudo nmap -sM` | Maimon | FIN+ACK |
| `sudo nmap -sA` | ACK | Firewall kuralı tespiti |
| `sudo nmap -sW` | Window | ACK'in gelişmişi |
| `--scanflags SYNFIN` | Özel | Kendi flag kombinasyonun |

> Null/FIN/Xmas → **kapalı** porttan cevap alır (açık/filtreli sessiz kalır).
> Firewall/IDS atlatmada işe yarar ama modern sistemlerde güvenilmez.

### Gizlilik / Atlatma
| Seçenek | Ne yapar |
|---------|----------|
| `-D DECOY1,DECOY2,ME` | Decoy (sahte kaynaklarla gerçek IP'ni gizle) |
| `-S SAHTE_IP` | Kaynak IP spoof |
| `--spoof-mac MAC` | MAC spoof |
| `-f` / `-ff` | Paketi 8/16 byte'a parçala (fragment) |
| `-sI ZOMBIE_IP` | Idle/Zombie scan (3. makine üzerinden, tam anonim) |
| `--source-port 53` | Kaynak portu sahtele (firewall bypass) |
| `--data-length 25` | Pakete rastgele veri ekle |

## 5. Servis & OS Tespiti + Scriptler
| Komut | Ne yapar |
|-------|----------|
| `-sV` | Servis/sürüm tespiti (**çok önemli** → exploit için) |
| `-sV --version-light` / `--version-all` | 2 vs 9 prob (hız/kapsam) |
| `-O` | İşletim sistemi tespiti |
| `--traceroute` | Yol haritası |
| `-sC` veya `--script=default` | Varsayılan NSE scriptleri |
| `--script=vuln` | Zafiyet taraması |
| `-A` | Hepsi: `-sV -O -sC --traceroute` |

## 6. Çıktı Kaydetme
| Komut | Format |
|-------|--------|
| `-oN out.txt` | Normal |
| `-oG out.gnmap` | Grepable |
| `-oX out.xml` | XML |
| `-oA out` | Üçü birden |

## Pratik Akış (CTF'te tipik ilk komut)
```bash
# Hızlı tam tarama + servis/script + kayıt:
sudo nmap -sS -sV -sC -p- -T4 <IP> -oN nmap_full.txt

# UDP'yi unutma (ayrı):
sudo nmap -sU --top-ports 20 <IP>
```
Çıktıdan: açık portlar → servis sürümleri → `searchsploit <servis sürüm>` → exploit.

## Hatırlatma
- `-sV` olmadan "port açık" demek yarım bilgi; **sürüm** exploit'i belirler.
- Root (`sudo`) = SYN scan + OS tespiti + ham paket seçenekleri açılır.
- Gerçek testte `-T4` iyi denge; `-T5` paket kaybettirebilir.
