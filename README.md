# security-notes

Kişisel siber güvenlik bilgi tabanım — öğrenirken (TryHackMe, lab'ler,
Cisco Ethical Hacker gibi sertifikalar) topladığım notlar, komutlar ve
teknikler. Amaç: gerçekten tekrar kullandığım hızlı bir referans.

> Her klasör dolu değil — harita tam, ama sadece gerçekten çalıştığım
> alanlara not yazıyorum. Ben ilerledikçe repo da büyüyor.

## Harita

### Temeller
| Klasör | İçerik |
|--------|--------|
| `00-fundamentals` | Ağ, Linux ve Windows temelleri |

### Ofensif — Aşamalar
| Klasör | İçerik |
|--------|--------|
| `01-recon` | Pasif & aktif keşif, OSINT |
| `02-scanning-enum` | Port tarama & servis enumerasyonu (nmap, protokoller) |
| `03-vuln-analysis` | Zafiyet bulma & doğrulama |
| `04-exploitation` | İlk erişimi alma |
| `05-post-exploitation` | Shell, kalıcılık, pivoting |
| `06-privilege-escalation` | Linux/Windows yetki yükseltme, GTFOBins |

### Ofensif — Alanlar
| Klasör | İçerik |
|--------|--------|
| `07-web` | OWASP: SQLi, XSS, LFI/RFI, dosya yükleme, SSRF, bug bounty |
| `08-api-security` | API zafiyetleri |
| `09-mobile-security` | Android / iOS |
| `10-network-attacks` | MITM, sniffing, spoofing, relay |
| `11-wireless` | Wi-Fi saldırıları |
| `12-active-directory` | AD enumerasyon & saldırı |
| `13-cloud-security` | AWS / Azure / GCP |
| `14-container-k8s-security` | Docker, Kubernetes |
| `15-iot-hardware-security` | IoT & donanım |
| `16-social-engineering` | Phishing, pretexting |
| `17-password-attacks` | Hydra, hashcat, john, wordlist'ler |
| `18-ai-ml-security` | AI/LLM güvenliği: prompt injection, model saldırıları |

### Analiz
| Klasör | İçerik |
|--------|--------|
| `19-reverse-engineering` | Binary analizi, debugging |
| `20-malware-analysis` | Zararlı yazılım analizi |
| `21-forensics-dfir` | Adli bilişim & olay müdahale |
| `22-cryptography` | Encoding, hashing, kripto saldırıları |

### Defansif
| Klasör | İçerik |
|--------|--------|
| `23-blue-team-soc` | SIEM, log analizi, detection, threat hunting |
| `24-threat-intel` | Tehdit istihbaratı, MITRE ATT&CK |

### Meta / Destek
| Klasör | İçerik |
|--------|--------|
| `25-secure-coding-appsec` | Güvenli kod, DevSecOps, threat modeling |
| `26-coding-scripting` | Kendi Python/Bash güvenlik araçlarım |
| `27-reporting` | Pentest rapor şablonları & metodoloji |
| `28-tools` | Burp, Metasploit, Wireshark notları |
| `29-grc-compliance` | ISO 27001, risk yönetimi, denetim, uyumluluk |
| `99-cheatsheets` | Hızlı komut referansları |

## Nasıl kullanıyorum
- Her klasörün kendi `README.md`'si var → index + öğrenme kontrol listesi.
- Konu notları ilgili klasörde `<konu>.md` olarak.
- Tek satırlık komut aramaları `99-cheatsheets/` içinde.
- **Kendime kuralım:** bu repodaki her şeyi satır satır açıklayabilmeliyim.

## İlgili
- `security-writeups` — öne çıkan CTF/makine writeup'ları.
