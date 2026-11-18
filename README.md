# security-notes

Kişisel siber güvenlik bilgi tabanım — öğrenirken (TryHackMe, lab'ler, Cisco Ethical Hacker gibi sertifikalar) topladığım notlar, komutlar ve teknikler. Amaç: gerçekten tekrar kullandığım hızlı bir referans.

Her klasör dolu değil — harita tam, ama sadece gerçekten çalıştığım alanlara not yazıyorum. Ben ilerledikçe repo da büyüyor.

## Harita

### Temeller
| Klasör | İçerik |
|---|---|
| [00-fundamentals](00-fundamentals/) | Ağ, Linux ve Windows temelleri |

### Ofansif — Aşamalar
| Klasör | İçerik |
|---|---|
| [01-recon](01-recon/) | Pasif & aktif keşif, OSINT |
| [02-scanning-enum](02-scanning-enum/) | Port tarama & servis enumerasyonu |
| [03-vuln-analysis](03-vuln-analysis/) | Zafiyet bulma & doğrulama |
| [04-exploitation](04-exploitation/) | İlk erişimi alma |
| [05-post-exploitation](05-post-exploitation/) | Shell, kalıcılık, pivoting, evasion, C2 |
| [06-privilege-escalation](06-privilege-escalation/) | Linux/Windows yetki yükseltme |

### Ofansif — Alanlar
| Klasör | İçerik |
|---|---|
| [07-web](07-web/) | OWASP Top 10, bug bounty |
| [08-api-security](08-api-security/) | API zafiyetleri |
| [09-mobile-security](09-mobile-security/) | Android / iOS |
| [10-network-attacks](10-network-attacks/) | MITM, sniffing, spoofing, relay |
| [11-wireless](11-wireless/) | Wi-Fi saldırıları |
| [12-active-directory](12-active-directory/) | AD enumerasyon & saldırı |
| [13-cloud-security](13-cloud-security/) | AWS / Azure / GCP |
| [14-container-k8s-security](14-container-k8s-security/) | Docker, Kubernetes |
| [15-iot-hardware-security](15-iot-hardware-security/) | IoT & donanım |
| [16-social-engineering](16-social-engineering/) | Phishing, pretexting, fiziksel güvenlik, OPSEC |
| [17-password-attacks](17-password-attacks/) | Hydra, hashcat, john, wordlist'ler |
| [18-ai-ml-security](18-ai-ml-security/) | AI/LLM güvenliği |
| [30-binary-exploitation](30-binary-exploitation/) | Buffer overflow, ROP, shellcode |
| [31-ot-ics-security](31-ot-ics-security/) | Endüstriyel sistemler, SCADA, kritik altyapı |

### Analiz
| Klasör | İçerik |
|---|---|
| [19-reverse-engineering](19-reverse-engineering/) | Binary analizi, debugging |
| [20-malware-analysis](20-malware-analysis/) | Zararlı yazılım analizi |
| [21-forensics-dfir](21-forensics-dfir/) | Adli bilişim & olay müdahale |
| [22-cryptography](22-cryptography/) | Encoding, hashing, kripto saldırıları |

### Defansif
| Klasör | İçerik |
|---|---|
| [23-blue-team-soc](23-blue-team-soc/) | SIEM, log analizi, detection, threat hunting |
| [24-threat-intel](24-threat-intel/) | Tehdit istihbaratı, MITRE ATT&CK |

### Meta / Destek
| Klasör | İçerik |
|---|---|
| [25-secure-coding-appsec](25-secure-coding-appsec/) | Güvenli kod, DevSecOps, threat modeling |
| [26-coding-scripting](26-coding-scripting/) | Kendi Python/Bash güvenlik araçlarım |
| [27-reporting](27-reporting/) | Pentest rapor şablonları & metodoloji |
| [28-tools](28-tools/) | Burp, Metasploit, Wireshark notları |
| [29-grc-compliance](29-grc-compliance/) | ISO 27001, risk yönetimi, uyumluluk |
| [99-cheatsheets](99-cheatsheets/) | Tek satırlık komut referansları |

## Nasıl kullanıyorum
- Her klasörün kendi `README.md`'si var → içindekiler + öğrenme kontrol listesi.
- Konu notları ilgili klasörde `<konu>.md` olarak; yeni not için `_templates/konu-sablonu.md`'yi kopyalıyorum.
- Tek satırlık komut aramaları `99-cheatsheets/` içinde.
- Çözdüğüm odaların hikâyesi ayrı repoda: [security-writeups](https://github.com/Recepgundogdu1/security-writeups).
- Kendime kuralım: bu repodaki her şeyi satır satır açıklayabilmeliyim.
