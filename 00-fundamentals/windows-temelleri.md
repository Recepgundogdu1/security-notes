# Windows Temelleri

AD ve kurumsal ağlarda Windows çıkıyor. CMD + PowerShell refleks olmalı.

## Sistem & Kullanıcı Bilgisi
| Komut | Ne yapar |
|-------|----------|
| `whoami` / `whoami /priv` | Kim + yetkiler (**privesc!**) |
| `systeminfo` | OS sürümü, yama durumu (exploit tespiti) |
| `net user` | Yerel kullanıcılar |
| `net user kullanıcı` | Kullanıcı detayı & grupları |
| `net localgroup administrators` | Admin grubu üyeleri |
| `hostname` | Makine adı |

## Ağ (CMD)
| Komut | Ne yapar |
|-------|----------|
| `ipconfig /all` | IP, DNS, MAC |
| `arp -a` | ARP tablosu |
| `netstat -ano` | Açık portlar + PID |
| `route print` | Yönlendirme tablosu |
| `nslookup alan` | DNS sorgusu |

## Dosya & Dizin (CMD)
| Komut | Ne yapar |
|-------|----------|
| `dir /a` | Gizli dahil listele |
| `cd` / `type dosya` | Gez / oku |
| `where dosya` | Dosya konumu |
| `tasklist` / `taskkill /PID x /F` | Süreçler |

## PowerShell (daha güçlü)
```powershell
Get-Process                      # süreçler
Get-Service                      # servisler
Get-LocalUser                    # kullanıcılar
Get-ChildItem -Recurse -Filter *.txt   # dosya arama
Get-Content dosya.txt            # dosya oku
Invoke-WebRequest url -OutFile x # indir
```

## Privesc açısından ilk bakılacaklar
```powershell
whoami /priv                     # SeImpersonate vb. yetkiler
systeminfo                       # yama → kernel exploit?
Get-Service | ? {$_.Status -eq "Running"}   # servisler
schtasks /query /fo LIST         # zamanlanmış görevler
```
- Araçlar: **WinPEAS**, **PowerUp**, **Seatbelt** (otomatik enum)
- Hash/parola: **Mimikatz**, SAM/LSASS dump
