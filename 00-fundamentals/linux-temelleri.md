# Linux Temelleri

Siber güvenlik için günlük kullandığım Linux komutları. Hedef makinelerde
%90 Linux ile uğraşıyoruz, bu yüzden refleks olması lazım.

## Dizin & Gezinme
| Komut | Ne yapar |
|-------|----------|
| `pwd` | Bulunduğun dizini yazar |
| `ls -la` | Gizli dosyalar + izinler dahil listeler |
| `cd -` | Bir önceki dizine döner |
| `tree` | Dizin ağacını çıkarır |
| `find / -name "*.txt" 2>/dev/null` | Sistemde dosya arar (hataları gizle) |

## Dosya İşlemleri
| Komut | Ne yapar |
|-------|----------|
| `cat / less / head / tail` | Dosya okuma |
| `cp` / `mv` / `rm` | Kopyala / taşı / sil |
| `touch dosya` | Boş dosya oluştur |
| `nano` / `vim` | Metin editörü |
| `wc -l` | Satır sayısı |

## İzinler (çok önemli)
```bash
chmod +x script.sh      # çalıştırılabilir yap
chmod 644 dosya         # rw-r--r--
chown user:grup dosya   # sahip değiştir
ls -l                   # izinleri gör (rwx)
```
- `r=4  w=2  x=1`  →  `7=rwx  6=rw-  5=r-x`
- İlk triad = sahip, 2. = grup, 3. = diğerleri

## Kullanıcı & Yetki
| Komut | Ne yapar |
|-------|----------|
| `whoami` / `id` | Kim olduğun + gruplar |
| `sudo -l` | Şifresiz/izinli root komutları (**privesc!**) |
| `su kullanıcı` | Kullanıcı değiştir |
| `cat /etc/passwd` | Sistem kullanıcıları |
| `cat /etc/shadow` | Parola hash'leri (sadece root) |

## Süreçler & Servisler
| Komut | Ne yapar |
|-------|----------|
| `ps aux` | Çalışan tüm süreçler |
| `top` / `htop` | Canlı süreç izleme |
| `kill -9 PID` | Süreci öldür |
| `systemctl status servis` | Servis durumu |
| `netstat -tulpn` / `ss -tulpn` | Açık portlar & dinleyen servisler |

## Ağ Komutları
| Komut | Ne yapar |
|-------|----------|
| `ip a` / `ifconfig` | IP adresleri |
| `ping host` | Erişilebilirlik testi |
| `curl -I http://site` | HTTP başlıkları |
| `wget url` | Dosya indir |
| `nc -lvnp 4444` | Dinleyici aç (reverse shell) |

## Paket Yönetimi (Debian/Ubuntu)
```bash
apt update && apt install araç
apt search kelime
dpkg -l                 # kurulu paketler
```

## Metin İşleme (enum için altın)
| Komut | Ne yapar |
|-------|----------|
| `grep -ri "password" /var` | İçerikte arama (özyinelemeli) |
| `find / -perm -4000 2>/dev/null` | SUID binary'ler (**privesc!**) |
| `sort` / `uniq` / `wc` | Sırala / tekilleştir / say |
| `awk '{print $1}'` | Sütun seç |
| `sed 's/a/b/g'` | Değiştir |

## Privesc açısından ilk bakılacaklar
```bash
sudo -l                              # izinli komutlar → GTFOBins
find / -perm -4000 -type f 2>/dev/null   # SUID
cat /etc/crontab                     # zamanlanmış görevler
uname -a                             # kernel sürümü (exploit?)
```
