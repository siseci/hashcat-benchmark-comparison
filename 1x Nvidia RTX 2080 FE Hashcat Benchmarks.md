

## Nvidia RTX 2080 FE Hashcat Benchmarks

**Product:** As there is currently no Linux driver, we had to use chick3nman's desktop (Windows 7)

**Software:** Hashcat v4.2.1, Nvidia driver 411.63

**Accelerator:** 1x Nvidia RTX 2080 Founders Edition

**Source:** https://gist.github.com/epixoip/23068f4bc81db505115c43e7751522f2

#### Notes

1. This is not the huge generational leap in performance we are accustomed to with new architectures. Turing is an incremental improvement over Pascal at best.

2. The card looks like a VHS tape and I hate it.

3. Performance is kind of all over the place. On average, it's roughly ~20% faster than GTX 1080 and ~20% slower than GTX 1080 Ti, putting it squarely in the middle of the two. In some cases, however, performance is much closer to GTX 1080 Ti than GTX 1080 (e.g., raw MD5.) In other cases, performance is much closer to the GTX 1080 (e.g., MS Office.)

4. This is a release-day Windows driver, and there is currently no Linux driver. Future drivers may yield better and more stable performance.

5. The clocks stay around 1815 MHz - 1840 MHz under full load. Max power consumption (as reported by driver) was 266W (well below 300W board capacity.) This is presumably because we're really only using half of the chip (not using RTUs or TPUs.)

6. The FE GPU cooler copes with compute workloads surprisingly well; temp stays around 75C, and we never saw the GPU break 77C. With that said, the FE card *will not stack* and is definitely an exception to the "always buy reference design" rule. Only buy the FE card if it will be the only card in the system, while also keeping in mind this style cooler (vertical-fin heatsink with axial fans) will exhaust hot air *into* the chassis instead of out of the chassis. Blower-style OEM GPUs are strongly recommended in this instance.


### Benchmarks

```bash
hashcat (v4.2.1) starting in benchmark mode...

OpenCL Platform #1: Intel(R) Corporation
========================================
* Device #1: Intel(R) Core(TM) i7-6700K CPU @ 4.00GHz, skipped.

OpenCL Platform #2: NVIDIA Corporation
======================================
* Device #2: GeForce RTX 2080, 2048/8192 MB allocatable, 46MCU

Benchmark relevant options:
===========================
* --benchmark-all
* --optimized-kernel-enable
* --workload-profile=4

Hashmode: 0 - MD5

Speed.Dev.#2.....: 37085.5 MH/s (82.48ms) @ Accel:256 Loops:1024 Thr:256 Vec:1

Hashmode: 10 - md5($pass.$salt)

Speed.Dev.#2.....: 36671.4 MH/s (83.00ms) @ Accel:256 Loops:1024 Thr:256 Vec:1

Hashmode: 11 - Joomla < 2.5.18

Speed.Dev.#2.....: 37101.4 MH/s (82.72ms) @ Accel:256 Loops:1024 Thr:256 Vec:1

Hashmode: 12 - PostgreSQL

Speed.Dev.#2.....: 36671.6 MH/s (82.90ms) @ Accel:256 Loops:1024 Thr:256 Vec:1

Hashmode: 20 - md5($salt.$pass)

Speed.Dev.#2.....: 20862.7 MH/s (147.23ms) @ Accel:256 Loops:1024 Thr:256 Vec:1

Hashmode: 21 - osCommerce, xt:Commerce

Speed.Dev.#2.....: 20881.8 MH/s (146.84ms) @ Accel:256 Loops:1024 Thr:256 Vec:1

Hashmode: 22 - Juniper NetScreen/SSG (ScreenOS)

Speed.Dev.#2.....: 20767.7 MH/s (147.83ms) @ Accel:256 Loops:1024 Thr:256 Vec:1

Hashmode: 23 - Skype

Speed.Dev.#2.....: 20830.6 MH/s (147.44ms) @ Accel:256 Loops:1024 Thr:256 Vec:1

Hashmode: 30 - md5(utf16le($pass).$salt)

Speed.Dev.#2.....: 34925.6 MH/s (87.30ms) @ Accel:256 Loops:1024 Thr:256 Vec:1

Hashmode: 40 - md5($salt.utf16le($pass))

Speed.Dev.#2.....: 20748.3 MH/s (147.72ms) @ Accel:256 Loops:1024 Thr:256 Vec:1

Hashmode: 50 - HMAC-MD5 (key = $pass)

Speed.Dev.#2.....:  6269.0 MH/s (243.83ms) @ Accel:256 Loops:512 Thr:256 Vec:1

Hashmode: 60 - HMAC-MD5 (key = $salt)

Speed.Dev.#2.....: 13166.5 MH/s (232.71ms) @ Accel:256 Loops:1024 Thr:256 Vec:1

Hashmode: 100 - SHA1

Speed.Dev.#2.....: 12004.4 MH/s (255.51ms) @ Accel:256 Loops:1024 Thr:256 Vec:1

Hashmode: 101 - nsldap, SHA-1(Base64), Netscape LDAP SHA

Speed.Dev.#2.....: 11965.2 MH/s (255.16ms) @ Accel:256 Loops:1024 Thr:256 Vec:1

Hashmode: 110 - sha1($pass.$salt)

Speed.Dev.#2.....: 12010.8 MH/s (255.40ms) @ Accel:256 Loops:1024 Thr:256 Vec:1

Hashmode: 111 - nsldaps, SSHA-1(Base64), Netscape LDAP SSHA

Speed.Dev.#2.....: 11999.7 MH/s (256.17ms) @ Accel:256 Loops:1024 Thr:256 Vec:1

Hashmode: 112 - Oracle S: Type (Oracle 11+)

Speed.Dev.#2.....: 11870.9 MH/s (255.81ms) @ Accel:256 Loops:1024 Thr:256 Vec:1

Hashmode: 120 - sha1($salt.$pass)

Speed.Dev.#2.....:  9490.2 MH/s (323.52ms) @ Accel:256 Loops:1024 Thr:256 Vec:1

Hashmode: 121 - SMF (Simple Machines Forum) > v1.1

Speed.Dev.#2.....:  9485.9 MH/s (323.94ms) @ Accel:256 Loops:1024 Thr:256 Vec:1

Hashmode: 122 - macOS v10.4, macOS v10.5, MacOS v10.6

Speed.Dev.#2.....:  9320.1 MH/s (323.23ms) @ Accel:256 Loops:1024 Thr:256 Vec:1

Hashmode: 124 - Django (SHA-1)

Speed.Dev.#2.....:  9489.7 MH/s (323.69ms) @ Accel:256 Loops:1024 Thr:256 Vec:1

Hashmode: 125 - ArubaOS

Speed.Dev.#2.....:  9493.0 MH/s (323.24ms) @ Accel:256 Loops:1024 Thr:256 Vec:1

Hashmode: 130 - sha1(utf16le($pass).$salt)

Speed.Dev.#2.....: 12275.8 MH/s (249.15ms) @ Accel:256 Loops:1024 Thr:256 Vec:1

Hashmode: 131 - MSSQL (2000)

Speed.Dev.#2.....: 12338.8 MH/s (248.65ms) @ Accel:256 Loops:1024 Thr:256 Vec:1

Hashmode: 132 - MSSQL (2005)

Speed.Dev.#2.....: 12318.3 MH/s (248.92ms) @ Accel:256 Loops:1024 Thr:256 Vec:1

Hashmode: 133 - PeopleSoft

Speed.Dev.#2.....: 12277.7 MH/s (249.07ms) @ Accel:256 Loops:1024 Thr:256 Vec:1

Hashmode: 140 - sha1($salt.utf16le($pass))

Speed.Dev.#2.....:  9503.4 MH/s (323.12ms) @ Accel:256 Loops:1024 Thr:256 Vec:1

Hashmode: 141 - Episerver 6.x < .NET 4

Speed.Dev.#2.....:  9507.4 MH/s (322.78ms) @ Accel:256 Loops:1024 Thr:256 Vec:1

Hashmode: 150 - HMAC-SHA1 (key = $pass)

Speed.Dev.#2.....:  2551.5 MH/s (301.18ms) @ Accel:256 Loops:256 Thr:256 Vec:1

Hashmode: 160 - HMAC-SHA1 (key = $salt)

Speed.Dev.#2.....:  4722.7 MH/s (323.32ms) @ Accel:256 Loops:512 Thr:256 Vec:1

Hashmode: 200 - MySQL323

Speed.Dev.#2.....:   104.5 GH/s (29.08ms) @ Accel:256 Loops:1024 Thr:256 Vec:1

Hashmode: 300 - MySQL4.1/MySQL5

Speed.Dev.#2.....:  5255.5 MH/s (291.20ms) @ Accel:256 Loops:512 Thr:256 Vec:1

Hashmode: 400 - phpass, WordPress (MD5), phpBB3 (MD5), Joomla (MD5) (Iterations: 2048)

Speed.Dev.#2.....: 10142.4 kH/s (138.41ms) @ Accel:256 Loops:1024 Thr:256 Vec:1

Hashmode: 500 - md5crypt, MD5 (Unix), Cisco-IOS $1$ (MD5) (Iterations: 1000)

Speed.Dev.#2.....: 15743.9 kH/s (86.24ms) @ Accel:1024 Loops:1000 Thr:32 Vec:1

Hashmode: 501 - Juniper IVE (Iterations: 1000)

Speed.Dev.#2.....: 15845.7 kH/s (85.53ms) @ Accel:1024 Loops:1000 Thr:32 Vec:1

Hashmode: 600 - BLAKE2b

Speed.Dev.#2.....:  2812.9 MH/s (270.71ms) @ Accel:256 Loops:256 Thr:256 Vec:1

Hashmode: 900 - MD4

Speed.Dev.#2.....: 53191.9 MH/s (57.51ms) @ Accel:256 Loops:1024 Thr:256 Vec:1

Hashmode: 1000 - NTLM

Speed.Dev.#2.....: 52954.9 MH/s (57.51ms) @ Accel:256 Loops:1024 Thr:256 Vec:1

Hashmode: 1100 - Domain Cached Credentials (DCC), MS Cache

Speed.Dev.#2.....: 15930.1 MH/s (192.52ms) @ Accel:256 Loops:1024 Thr:256 Vec:1

Hashmode: 1300 - SHA-224

Speed.Dev.#2.....:  5264.7 MH/s (291.54ms) @ Accel:256 Loops:512 Thr:256 Vec:1

Hashmode: 1400 - SHA-256

Speed.Dev.#2.....:  5361.3 MH/s (284.86ms) @ Accel:256 Loops:512 Thr:256 Vec:1

Hashmode: 1410 - sha256($pass.$salt)

Speed.Dev.#2.....:  5380.8 MH/s (285.38ms) @ Accel:256 Loops:512 Thr:256 Vec:1

Hashmode: 1411 - SSHA-256(Base64), LDAP {SSHA256}

Speed.Dev.#2.....:  5392.8 MH/s (284.68ms) @ Accel:256 Loops:512 Thr:256 Vec:1

Hashmode: 1420 - sha256($salt.$pass)

Speed.Dev.#2.....:  4764.4 MH/s (322.61ms) @ Accel:256 Loops:512 Thr:256 Vec:1

Hashmode: 1421 - hMailServer

Speed.Dev.#2.....:  4727.4 MH/s (322.52ms) @ Accel:256 Loops:512 Thr:256 Vec:1

Hashmode: 1430 - sha256(utf16le($pass).$salt)

Speed.Dev.#2.....:  5331.1 MH/s (287.61ms) @ Accel:256 Loops:512 Thr:256 Vec:1

Hashmode: 1440 - sha256($salt.utf16le($pass))

Speed.Dev.#2.....:  4760.1 MH/s (322.54ms) @ Accel:256 Loops:512 Thr:256 Vec:1

Hashmode: 1441 - Episerver 6.x >= .NET 4

Speed.Dev.#2.....:  4762.3 MH/s (322.71ms) @ Accel:256 Loops:512 Thr:256 Vec:1

Hashmode: 1450 - HMAC-SHA256 (key = $pass)

Speed.Dev.#2.....:   962.3 MH/s (399.36ms) @ Accel:256 Loops:128 Thr:256 Vec:1

Hashmode: 1460 - HMAC-SHA256 (key = $salt)

Speed.Dev.#2.....:  2013.9 MH/s (379.91ms) @ Accel:256 Loops:256 Thr:256 Vec:1

Hashmode: 1500 - descrypt, DES (Unix), Traditional DES

Speed.Dev.#2.....:  1284.3 MH/s (299.84ms) @ Accel:32 Loops:1024 Thr:256 Vec:1

Hashmode: 1600 - Apache $apr1$ MD5, md5apr1, MD5 (APR) (Iterations: 1000)

Speed.Dev.#2.....: 16003.7 kH/s (83.83ms) @ Accel:1024 Loops:1000 Thr:32 Vec:1

Hashmode: 1700 - SHA-512

Speed.Dev.#2.....:  1763.8 MH/s (431.85ms) @ Accel:256 Loops:256 Thr:256 Vec:1

Hashmode: 1710 - sha512($pass.$salt)

Speed.Dev.#2.....:  1776.9 MH/s (432.12ms) @ Accel:256 Loops:256 Thr:256 Vec:1

Hashmode: 1711 - SSHA-512(Base64), LDAP {SSHA512}

Speed.Dev.#2.....:  1776.7 MH/s (431.49ms) @ Accel:256 Loops:256 Thr:256 Vec:1

Hashmode: 1720 - sha512($salt.$pass)

Speed.Dev.#2.....:  1556.2 MH/s (246.20ms) @ Accel:256 Loops:128 Thr:256 Vec:1

Hashmode: 1722 - macOS v10.7

Speed.Dev.#2.....:  1545.9 MH/s (248.24ms) @ Accel:256 Loops:128 Thr:256 Vec:1

Hashmode: 1730 - sha512(utf16le($pass).$salt)

Speed.Dev.#2.....:  1780.5 MH/s (431.18ms) @ Accel:256 Loops:256 Thr:256 Vec:1

Hashmode: 1731 - MSSQL (2012, 2014)

Speed.Dev.#2.....:  1777.1 MH/s (429.50ms) @ Accel:256 Loops:256 Thr:256 Vec:1

Hashmode: 1740 - sha512($salt.utf16le($pass))

Speed.Dev.#2.....:  1692.7 MH/s (454.30ms) @ Accel:256 Loops:256 Thr:256 Vec:1

Hashmode: 1750 - HMAC-SHA512 (key = $pass)

Speed.Dev.#2.....:   346.3 MH/s (277.76ms) @ Accel:128 Loops:64 Thr:256 Vec:1

Hashmode: 1760 - HMAC-SHA512 (key = $salt)

Speed.Dev.#2.....:   744.0 MH/s (258.27ms) @ Accel:256 Loops:64 Thr:256 Vec:1

Hashmode: 1800 - sha512crypt $6$, SHA512 (Unix) (Iterations: 5000)

Speed.Dev.#2.....:   268.5 kH/s (283.31ms) @ Accel:1024 Loops:256 Thr:32 Vec:1

Hashmode: 2100 - Domain Cached Credentials 2 (DCC2), MS Cache 2 (Iterations: 10240)

Speed.Dev.#2.....:   461.3 kH/s (324.99ms) @ Accel:256 Loops:512 Thr:256 Vec:1

Hashmode: 2400 - Cisco-PIX MD5

Speed.Dev.#2.....: 25879.5 MH/s (118.62ms) @ Accel:256 Loops:1024 Thr:256 Vec:1

Hashmode: 2410 - Cisco-ASA MD5

Speed.Dev.#2.....: 23624.2 MH/s (130.02ms) @ Accel:256 Loops:1024 Thr:256 Vec:1

Hashmode: 2500 - WPA-EAPOL-PBKDF2 (Iterations: 4096)

Speed.Dev.#2.....:   571.4 kH/s (327.82ms) @ Accel:256 Loops:256 Thr:256 Vec:1

Hashmode: 2501 - WPA-EAPOL-PMK (Iterations: 1)

Speed.Dev.#2.....:   134.3 MH/s (0.01ms) @ Accel:256 Loops:1 Thr:256 Vec:1

Hashmode: 2600 - md5(md5($pass))

Speed.Dev.#2.....: 11255.6 MH/s (273.11ms) @ Accel:256 Loops:1024 Thr:256 Vec:1

Hashmode: 2611 - vBulletin < v3.8.5

Speed.Dev.#2.....: 11223.0 MH/s (273.88ms) @ Accel:256 Loops:1024 Thr:256 Vec:1

Hashmode: 2612 - PHPS

Speed.Dev.#2.....: 11205.3 MH/s (274.34ms) @ Accel:256 Loops:1024 Thr:256 Vec:1

Hashmode: 2711 - vBulletin >= v3.8.5

Speed.Dev.#2.....:  7883.9 MH/s (390.14ms) @ Accel:256 Loops:1024 Thr:256 Vec:1

Hashmode: 2811 - IPB2+ (Invision Power Board), MyBB 1.2+

Speed.Dev.#2.....:  8252.0 MH/s (372.55ms) @ Accel:256 Loops:1024 Thr:256 Vec:1

Hashmode: 3000 - LM

Speed.Dev.#2.....: 32407.9 MH/s (94.52ms) @ Accel:256 Loops:1024 Thr:256 Vec:1

Hashmode: 3100 - Oracle H: Type (Oracle 7+)

Speed.Dev.#2.....:  1126.1 MH/s (341.27ms) @ Accel:256 Loops:128 Thr:256 Vec:1

Hashmode: 3200 - bcrypt $2*$, Blowfish (Unix) (Iterations: 32)

Speed.Dev.#2.....:    18485 H/s (155.66ms) @ Accel:32 Loops:8 Thr:8 Vec:1

Hashmode: 3710 - md5($salt.md5($pass))

Speed.Dev.#2.....: 10406.6 MH/s (295.41ms) @ Accel:256 Loops:1024 Thr:256 Vec:1

Hashmode: 3711 - MediaWiki B type

Speed.Dev.#2.....: 10392.9 MH/s (295.84ms) @ Accel:256 Loops:1024 Thr:256 Vec:1

Hashmode: 3800 - md5($salt.$pass.$salt)

Speed.Dev.#2.....: 20317.0 MH/s (151.19ms) @ Accel:256 Loops:1024 Thr:256 Vec:1

Hashmode: 3910 - md5(md5($pass).md5($salt))

Speed.Dev.#2.....:  7901.8 MH/s (389.26ms) @ Accel:256 Loops:1024 Thr:256 Vec:1

Hashmode: 4010 - md5($salt.md5($salt.$pass))

Speed.Dev.#2.....:  9102.9 MH/s (337.75ms) @ Accel:256 Loops:1024 Thr:256 Vec:1

Hashmode: 4110 - md5($salt.md5($pass.$salt))

Speed.Dev.#2.....:  9831.7 MH/s (312.72ms) @ Accel:256 Loops:1024 Thr:256 Vec:1

Hashmode: 4300 - md5(strtoupper(md5($pass)))

Speed.Dev.#2.....: 11230.1 MH/s (273.77ms) @ Accel:256 Loops:1024 Thr:256 Vec:1

Hashmode: 4400 - md5(sha1($pass))

Speed.Dev.#2.....:  6628.7 MH/s (463.90ms) @ Accel:256 Loops:1024 Thr:256 Vec:1

Hashmode: 4500 - sha1(sha1($pass))

Speed.Dev.#2.....:  4714.5 MH/s (326.12ms) @ Accel:256 Loops:512 Thr:256 Vec:1

Hashmode: 4520 - sha1($salt.sha1($pass))

Speed.Dev.#2.....:  4358.8 MH/s (352.80ms) @ Accel:256 Loops:512 Thr:256 Vec:1

Hashmode: 4521 - Redmine

Speed.Dev.#2.....:  4347.5 MH/s (353.62ms) @ Accel:256 Loops:512 Thr:256 Vec:1

Hashmode: 4522 - PunBB

Speed.Dev.#2.....:  4401.4 MH/s (348.83ms) @ Accel:256 Loops:512 Thr:256 Vec:1

Hashmode: 4700 - sha1(md5($pass))

Speed.Dev.#2.....:  6861.6 MH/s (448.17ms) @ Accel:256 Loops:1024 Thr:256 Vec:1

Hashmode: 4800 - iSCSI CHAP authentication, MD5(CHAP)

Speed.Dev.#2.....: 23142.6 MH/s (132.73ms) @ Accel:256 Loops:1024 Thr:256 Vec:1

Hashmode: 4900 - sha1($salt.$pass.$salt)

Speed.Dev.#2.....:  9141.4 MH/s (336.38ms) @ Accel:256 Loops:1024 Thr:256 Vec:1

Hashmode: 5000 - SHA-3 (Keccak)

Speed.Dev.#2.....:  1202.2 MH/s (319.71ms) @ Accel:256 Loops:128 Thr:256 Vec:1

Hashmode: 5100 - Half MD5

Speed.Dev.#2.....: 24063.8 MH/s (127.56ms) @ Accel:256 Loops:1024 Thr:256 Vec:1

Hashmode: 5200 - Password Safe v3 (Iterations: 2048)

Speed.Dev.#2.....:  2149.1 kH/s (345.22ms) @ Accel:256 Loops:512 Thr:256 Vec:1

Hashmode: 5300 - IKE-PSK MD5

Speed.Dev.#2.....:  3060.5 MH/s (251.10ms) @ Accel:256 Loops:256 Thr:256 Vec:1

Hashmode: 5400 - IKE-PSK SHA1

Speed.Dev.#2.....:  1158.3 MH/s (331.52ms) @ Accel:256 Loops:128 Thr:256 Vec:1

Hashmode: 5500 - NetNTLMv1 / NetNTLMv1+ESS

Speed.Dev.#2.....: 31243.0 MH/s (98.24ms) @ Accel:256 Loops:1024 Thr:256 Vec:1

Hashmode: 5600 - NetNTLMv2

Speed.Dev.#2.....:  2752.9 MH/s (278.83ms) @ Accel:256 Loops:256 Thr:256 Vec:1

Hashmode: 5700 - Cisco-IOS type 4 (SHA256)

Speed.Dev.#2.....:  5383.8 MH/s (285.13ms) @ Accel:256 Loops:512 Thr:256 Vec:1

Hashmode: 5800 - Samsung Android Password/PIN (Iterations: 1023)

Speed.Dev.#2.....:  8158.9 kH/s (351.31ms) @ Accel:256 Loops:1023 Thr:256 Vec:1

Hashmode: 6000 - RIPEMD-160

Speed.Dev.#2.....:  7191.6 MH/s (427.65ms) @ Accel:256 Loops:1024 Thr:256 Vec:1

Hashmode: 6100 - Whirlpool

Speed.Dev.#2.....:   285.8 MH/s (336.61ms) @ Accel:128 Loops:64 Thr:256 Vec:1

Hashmode: 6211 - TrueCrypt PBKDF2-HMAC-RIPEMD160 + XTS 512 bit (Iterations: 2000)

Speed.Dev.#2.....:   438.1 kH/s (430.91ms) @ Accel:256 Loops:128 Thr:256 Vec:1

Hashmode: 6212 - TrueCrypt PBKDF2-HMAC-RIPEMD160 + XTS 1024 bit (Iterations: 2000)

Speed.Dev.#2.....:   250.9 kH/s (374.98ms) @ Accel:256 Loops:64 Thr:256 Vec:1

Hashmode: 6213 - TrueCrypt PBKDF2-HMAC-RIPEMD160 + XTS 1536 bit (Iterations: 2000)

Speed.Dev.#2.....:   175.9 kH/s (269.08ms) @ Accel:128 Loops:64 Thr:256 Vec:1

Hashmode: 6221 - TrueCrypt PBKDF2-HMAC-SHA512 + XTS 512 bit (Iterations: 1000)

Speed.Dev.#2.....:   676.2 kH/s (245.84ms) @ Accel:128 Loops:125 Thr:256 Vec:1

Hashmode: 6222 - TrueCrypt PBKDF2-HMAC-SHA512 + XTS 1024 bit (Iterations: 1000)

Speed.Dev.#2.....:   373.7 kH/s (247.32ms) @ Accel:128 Loops:62 Thr:256 Vec:1

Hashmode: 6223 - TrueCrypt PBKDF2-HMAC-SHA512 + XTS 1536 bit (Iterations: 1000)

Speed.Dev.#2.....:   247.9 kH/s (371.94ms) @ Accel:128 Loops:62 Thr:256 Vec:1

Hashmode: 6231 - TrueCrypt PBKDF2-HMAC-Whirlpool + XTS 512 bit (Iterations: 1000)

Speed.Dev.#2.....:    43086 H/s (1077.05ms) @ Accel:64 Loops:62 Thr:256 Vec:1

Hashmode: 6232 - TrueCrypt PBKDF2-HMAC-Whirlpool + XTS 1024 bit (Iterations: 1000)

Speed.Dev.#2.....:    21695 H/s (1066.13ms) @ Accel:64 Loops:31 Thr:256 Vec:1

Hashmode: 6233 - TrueCrypt PBKDF2-HMAC-Whirlpool + XTS 1536 bit (Iterations: 1000)

Speed.Dev.#2.....:    14463 H/s (801.89ms) @ Accel:32 Loops:31 Thr:256 Vec:1

Hashmode: 6241 - TrueCrypt PBKDF2-HMAC-RIPEMD160 + XTS 512 bit + boot-mode (Iterations: 1000)

Speed.Dev.#2.....:   767.6 kH/s (418.02ms) @ Accel:256 Loops:125 Thr:256 Vec:1

Hashmode: 6242 - TrueCrypt PBKDF2-HMAC-RIPEMD160 + XTS 1024 bit + boot-mode (Iterations: 1000)

Speed.Dev.#2.....:   404.0 kH/s (370.10ms) @ Accel:128 Loops:125 Thr:256 Vec:1

Hashmode: 6243 - TrueCrypt PBKDF2-HMAC-RIPEMD160 + XTS 1536 bit + boot-mode (Iterations: 1000)

Speed.Dev.#2.....:   355.4 kH/s (257.95ms) @ Accel:128 Loops:62 Thr:256 Vec:1

Hashmode: 6300 - AIX {smd5} (Iterations: 1000)

Speed.Dev.#2.....: 16141.3 kH/s (83.71ms) @ Accel:1024 Loops:1000 Thr:32 Vec:1

Hashmode: 6400 - AIX {ssha256} (Iterations: 64)

Speed.Dev.#2.....: 26321.2 kH/s (91.31ms) @ Accel:256 Loops:64 Thr:256 Vec:1

Hashmode: 6500 - AIX {ssha512} (Iterations: 64)

Speed.Dev.#2.....: 10048.2 kH/s (257.00ms) @ Accel:256 Loops:64 Thr:256 Vec:1

Hashmode: 6600 - 1Password, agilekeychain (Iterations: 1000)

Speed.Dev.#2.....:  4586.9 kH/s (314.64ms) @ Accel:256 Loops:500 Thr:256 Vec:1

Hashmode: 6700 - AIX {ssha1} (Iterations: 64)

Speed.Dev.#2.....: 46742.4 kH/s (42.72ms) @ Accel:256 Loops:64 Thr:256 Vec:1

Hashmode: 6800 - LastPass + LastPass sniffed (Iterations: 500)

Speed.Dev.#2.....:  4145.2 kH/s (338.57ms) @ Accel:256 Loops:250 Thr:256 Vec:1

Hashmode: 6900 - GOST R 34.11-94

Speed.Dev.#2.....:   290.8 MH/s (330.36ms) @ Accel:128 Loops:64 Thr:256 Vec:1

Hashmode: 7000 - FortiGate (FortiOS)

Speed.Dev.#2.....:  9826.7 MH/s (308.99ms) @ Accel:256 Loops:1024 Thr:256 Vec:1

Hashmode: 7100 - macOS v10.8+ (PBKDF2-SHA512) (Iterations: 35000)

Speed.Dev.#2.....:    21554 H/s (252.77ms) @ Accel:256 Loops:64 Thr:256 Vec:1

Hashmode: 7200 - GRUB 2 (Iterations: 10000)

Speed.Dev.#2.....:    75547 H/s (252.42ms) @ Accel:256 Loops:64 Thr:256 Vec:1

Hashmode: 7300 - IPMI2 RAKP HMAC-SHA1

Speed.Dev.#2.....:  2336.9 MH/s (329.11ms) @ Accel:256 Loops:256 Thr:256 Vec:1

Hashmode: 7400 - sha256crypt $5$, SHA256 (Unix) (Iterations: 5000)

Speed.Dev.#2.....:   724.5 kH/s (410.64ms) @ Accel:256 Loops:512 Thr:256 Vec:1

Hashmode: 7500 - Kerberos 5 AS-REQ Pre-Auth etype 23

Speed.Dev.#2.....:   436.2 MH/s (441.44ms) @ Accel:512 Loops:128 Thr:64 Vec:1

Hashmode: 7700 - SAP CODVN B (BCODE)

Speed.Dev.#2.....:  2675.4 MH/s (287.37ms) @ Accel:256 Loops:256 Thr:256 Vec:1

Hashmode: 7701 - SAP CODVN B (BCODE) mangled from RFC_READ_TABLE

Speed.Dev.#2.....:  2882.0 MH/s (266.80ms) @ Accel:256 Loops:256 Thr:256 Vec:1

Hashmode: 7800 - SAP CODVN F/G (PASSCODE)

Speed.Dev.#2.....:  2058.0 MH/s (371.01ms) @ Accel:256 Loops:256 Thr:256 Vec:1

Hashmode: 7801 - SAP CODVN F/G (PASSCODE) mangled from RFC_READ_TABLE

Speed.Dev.#2.....:  3336.9 MH/s (460.80ms) @ Accel:256 Loops:512 Thr:256 Vec:1

Hashmode: 7900 - Drupal7 (Iterations: 16384)

Speed.Dev.#2.....:    93626 H/s (249.46ms) @ Accel:256 Loops:128 Thr:256 Vec:1

Hashmode: 8000 - Sybase ASE

Speed.Dev.#2.....:   684.9 MH/s (280.44ms) @ Accel:256 Loops:64 Thr:256 Vec:1

Hashmode: 8100 - Citrix NetScaler

Speed.Dev.#2.....: 10450.3 MH/s (294.09ms) @ Accel:256 Loops:1024 Thr:256 Vec:1

Hashmode: 8200 - 1Password, cloudkeychain (Iterations: 40000)

Speed.Dev.#2.....:    19778 H/s (240.58ms) @ Accel:256 Loops:64 Thr:256 Vec:1

Hashmode: 8300 - DNSSEC (NSEC3)

Speed.Dev.#2.....:  4597.9 MH/s (334.29ms) @ Accel:256 Loops:512 Thr:256 Vec:1

Hashmode: 8400 - WBB3 (Woltlab Burning Board)

Speed.Dev.#2.....:  1891.6 MH/s (405.50ms) @ Accel:256 Loops:256 Thr:256 Vec:1

Hashmode: 8500 - RACF

Speed.Dev.#2.....:  3440.2 MH/s (446.94ms) @ Accel:256 Loops:512 Thr:256 Vec:1

Hashmode: 8600 - Lotus Notes/Domino 5

Speed.Dev.#2.....:   254.0 MH/s (378.77ms) @ Accel:128 Loops:64 Thr:256 Vec:1

Hashmode: 8700 - Lotus Notes/Domino 6

Speed.Dev.#2.....: 83855.3 kH/s (286.73ms) @ Accel:64 Loops:32 Thr:256 Vec:1

Hashmode: 8800 - Android FDE <= 4.3 (Iterations: 2000)

Speed.Dev.#2.....:  1171.6 kH/s (316.01ms) @ Accel:256 Loops:256 Thr:256 Vec:1

Hashmode: 8900 - scrypt (Iterations: 1)

Speed.Dev.#2.....:   940.2 kH/s (8.09ms) @ Accel:16 Loops:1 Thr:16 Vec:1

Hashmode: 9000 - Password Safe v2 (Iterations: 1000)

Speed.Dev.#2.....:   411.4 kH/s (148.27ms) @ Accel:512 Loops:500 Thr:8 Vec:1

Hashmode: 9100 - Lotus Notes/Domino 8 (Iterations: 5000)

Speed.Dev.#2.....:   940.4 kH/s (315.73ms) @ Accel:256 Loops:512 Thr:256 Vec:1

Hashmode: 9200 - Cisco-IOS $8$ (PBKDF2-SHA256) (Iterations: 20000)

Speed.Dev.#2.....:   109.1 kH/s (350.16ms) @ Accel:256 Loops:256 Thr:256 Vec:1

Hashmode: 9300 - Cisco-IOS $9$ (scrypt) (Iterations: 1)

Speed.Dev.#2.....:    42455 H/s (97.43ms) @ Accel:16 Loops:1 Thr:8 Vec:1

Hashmode: 9400 - MS Office 2007 (Iterations: 50000)

Speed.Dev.#2.....:   189.0 kH/s (325.06ms) @ Accel:256 Loops:1024 Thr:256 Vec:1

Hashmode: 9500 - MS Office 2010 (Iterations: 100000)

Speed.Dev.#2.....:    94684 H/s (324.47ms) @ Accel:256 Loops:1024 Thr:256 Vec:1

Hashmode: 9600 - MS Office 2013 (Iterations: 100000)

Speed.Dev.#2.....:    16420 H/s (466.15ms) @ Accel:256 Loops:256 Thr:256 Vec:1

Hashmode: 9700 - MS Office <= 2003 $0/$1, MD5 + RC4

Speed.Dev.#2.....:   414.5 MH/s (464.11ms) @ Accel:512 Loops:128 Thr:64 Vec:1

Hashmode: 9710 - MS Office <= 2003 $0/$1, MD5 + RC4, collider #1

Speed.Dev.#2.....:   433.5 MH/s (441.94ms) @ Accel:256 Loops:256 Thr:64 Vec:1

Hashmode: 9720 - MS Office <= 2003 $0/$1, MD5 + RC4, collider #2

Speed.Dev.#2.....:  3212.0 MH/s (479.05ms) @ Accel:256 Loops:512 Thr:256 Vec:1

Hashmode: 9800 - MS Office <= 2003 $3/$4, SHA1 + RC4

Speed.Dev.#2.....:   464.2 MH/s (414.48ms) @ Accel:512 Loops:128 Thr:64 Vec:1

Hashmode: 9810 - MS Office <= 2003 $3, SHA1 + RC4, collider #1

Speed.Dev.#2.....:   478.0 MH/s (400.52ms) @ Accel:256 Loops:256 Thr:64 Vec:1

Hashmode: 9820 - MS Office <= 2003 $3, SHA1 + RC4, collider #2

Speed.Dev.#2.....:  4833.2 MH/s (318.27ms) @ Accel:256 Loops:512 Thr:256 Vec:1

Hashmode: 9900 - Radmin2

Speed.Dev.#2.....: 13950.0 MH/s (220.37ms) @ Accel:256 Loops:1024 Thr:256 Vec:1

Hashmode: 10000 - Django (PBKDF2-SHA256) (Iterations: 20000)

Speed.Dev.#2.....:   108.8 kH/s (351.03ms) @ Accel:256 Loops:256 Thr:256 Vec:1

Hashmode: 10100 - SipHash

Speed.Dev.#2.....: 42674.9 MH/s (71.83ms) @ Accel:256 Loops:1024 Thr:256 Vec:1

Hashmode: 10200 - CRAM-MD5

Speed.Dev.#2.....:  6221.0 MH/s (247.04ms) @ Accel:256 Loops:512 Thr:256 Vec:1

Hashmode: 10300 - SAP CODVN H (PWDSALTEDHASH) iSSHA-1 (Iterations: 1023)

Speed.Dev.#2.....:  7951.2 kH/s (359.86ms) @ Accel:256 Loops:1023 Thr:256 Vec:1

Hashmode: 10400 - PDF 1.1 - 1.3 (Acrobat 2 - 4)

Speed.Dev.#2.....:   511.5 MH/s (376.22ms) @ Accel:512 Loops:128 Thr:64 Vec:1

Hashmode: 10410 - PDF 1.1 - 1.3 (Acrobat 2 - 4), collider #1

Speed.Dev.#2.....:   520.6 MH/s (367.33ms) @ Accel:256 Loops:256 Thr:64 Vec:1

Hashmode: 10420 - PDF 1.1 - 1.3 (Acrobat 2 - 4), collider #2

Speed.Dev.#2.....: 11900.3 MH/s (258.43ms) @ Accel:256 Loops:1024 Thr:256 Vec:1

Hashmode: 10500 - PDF 1.4 - 1.6 (Acrobat 5 - 8) (Iterations: 70)

Speed.Dev.#2.....: 21695.7 kH/s (118.19ms) @ Accel:1024 Loops:70 Thr:64 Vec:1

Hashmode: 10600 - PDF 1.7 Level 3 (Acrobat 9)

Speed.Dev.#2.....:  5416.3 MH/s (283.42ms) @ Accel:256 Loops:512 Thr:256 Vec:1

Hashmode: 10700 - PDF 1.7 Level 8 (Acrobat 10 - 11) (Iterations: 64)

Speed.Dev.#2.....:    61138 H/s (384.75ms) @ Accel:16 Loops:8 Thr:256 Vec:1

Hashmode: 10800 - SHA-384

Speed.Dev.#2.....:  1747.0 MH/s (440.31ms) @ Accel:256 Loops:256 Thr:256 Vec:1

Hashmode: 10900 - PBKDF2-HMAC-SHA256 (Iterations: 999)

Speed.Dev.#2.....:  2144.1 kH/s (272.89ms) @ Accel:256 Loops:249 Thr:256 Vec:1

Hashmode: 11000 - PrestaShop

Speed.Dev.#2.....: 13708.9 MH/s (224.30ms) @ Accel:256 Loops:1024 Thr:256 Vec:1

Hashmode: 11100 - PostgreSQL CRAM (MD5)

Speed.Dev.#2.....: 10882.4 MH/s (282.65ms) @ Accel:256 Loops:1024 Thr:256 Vec:1

Hashmode: 11200 - MySQL CRAM (SHA1)

Speed.Dev.#2.....:  3169.0 MH/s (239.98ms) @ Accel:256 Loops:256 Thr:256 Vec:1

Hashmode: 11300 - Bitcoin/Litecoin wallet.dat (Iterations: 199999)

Speed.Dev.#2.....:     8053 H/s (475.78ms) @ Accel:256 Loops:256 Thr:256 Vec:1

Hashmode: 11400 - SIP digest authentication (MD5)

Speed.Dev.#2.....:  5362.1 MH/s (284.61ms) @ Accel:256 Loops:512 Thr:256 Vec:1

Hashmode: 11500 - CRC32

Speed.Dev.#2.....:  9176.7 MH/s (167.44ms) @ Accel:256 Loops:512 Thr:256 Vec:1

Hashmode: 11600 - 7-Zip (Iterations: 524288)

Speed.Dev.#2.....:    16201 H/s (361.50ms) @ Accel:256 Loops:1024 Thr:256 Vec:1

Hashmode: 11700 - GOST R 34.11-2012 (Streebog) 256-bit

Speed.Dev.#2.....: 58841.5 kH/s (409.28ms) @ Accel:64 Loops:32 Thr:256 Vec:1

Hashmode: 11800 - GOST R 34.11-2012 (Streebog) 512-bit

Speed.Dev.#2.....: 58988.5 kH/s (408.15ms) @ Accel:64 Loops:32 Thr:256 Vec:1

Hashmode: 11900 - PBKDF2-HMAC-MD5 (Iterations: 999)

Speed.Dev.#2.....: 12136.2 kH/s (224.46ms) @ Accel:256 Loops:999 Thr:256 Vec:1

Hashmode: 12000 - PBKDF2-HMAC-SHA1 (Iterations: 999)

Speed.Dev.#2.....:  4535.8 kH/s (211.92ms) @ Accel:256 Loops:499 Thr:256 Vec:1

Hashmode: 12001 - Atlassian (PBKDF2-HMAC-SHA1) (Iterations: 9999)

Speed.Dev.#2.....:   471.7 kH/s (324.91ms) @ Accel:256 Loops:512 Thr:256 Vec:1

Hashmode: 12100 - PBKDF2-HMAC-SHA512 (Iterations: 999)

Speed.Dev.#2.....:   762.7 kH/s (216.82ms) @ Accel:128 Loops:124 Thr:256 Vec:1

Hashmode: 12200 - eCryptfs (Iterations: 65535)

Speed.Dev.#2.....:    24735 H/s (472.66ms) @ Accel:256 Loops:256 Thr:256 Vec:1

Hashmode: 12300 - Oracle T: Type (Oracle 12+) (Iterations: 4095)

Speed.Dev.#2.....:   191.2 kH/s (241.93ms) @ Accel:256 Loops:64 Thr:256 Vec:1

Hashmode: 12400 - BSDi Crypt, Extended DES (Iterations: 2899)

Speed.Dev.#2.....:  1834.6 kH/s (539.52ms) @ Accel:256 Loops:1024 Thr:256 Vec:1

Hashmode: 12500 - RAR3-hp (Iterations: 262144)

Speed.Dev.#2.....:    47604 H/s (246.55ms) @ Accel:16 Loops:16384 Thr:256 Vec:1

Hashmode: 12600 - ColdFusion 10+

Speed.Dev.#2.....:  3033.0 MH/s (250.93ms) @ Accel:256 Loops:256 Thr:256 Vec:1

Hashmode: 12700 - Blockchain, My Wallet (Iterations: 10)

Speed.Dev.#2.....: 65008.0 kH/s (12.92ms) @ Accel:256 Loops:10 Thr:256 Vec:1

Hashmode: 12800 - MS-AzureSync PBKDF2-HMAC-SHA256 (Iterations: 99)

Speed.Dev.#2.....: 17175.9 kH/s (134.46ms) @ Accel:256 Loops:99 Thr:256 Vec:1

Hashmode: 12900 - Android FDE (Samsung DEK) (Iterations: 4095)

Speed.Dev.#2.....:   533.6 kH/s (349.62ms) @ Accel:256 Loops:256 Thr:256 Vec:1

Hashmode: 13000 - RAR5 (Iterations: 32767)

Speed.Dev.#2.....:    66824 H/s (346.73ms) @ Accel:256 Loops:256 Thr:256 Vec:1

Hashmode: 13100 - Kerberos 5 TGS-REP etype 23

Speed.Dev.#2.....:   455.5 MH/s (422.36ms) @ Accel:512 Loops:128 Thr:64 Vec:1

Hashmode: 13200 - AxCrypt (Iterations: 10000)

Speed.Dev.#2.....:   126.0 kH/s (304.51ms) @ Accel:256 Loops:128 Thr:256 Vec:1

Hashmode: 13300 - AxCrypt in-memory SHA1

Speed.Dev.#2.....: 11184.8 MH/s (274.31ms) @ Accel:256 Loops:1024 Thr:256 Vec:1

Hashmode: 13400 - KeePass 1 (AES/Twofish) and KeePass 2 (AES) (Iterations: 6000)

Speed.Dev.#2.....:   152.1 kH/s (842.74ms) @ Accel:1024 Loops:512 Thr:32 Vec:1

Hashmode: 13500 - PeopleSoft PS_TOKEN

Speed.Dev.#2.....:  4479.9 MH/s (340.99ms) @ Accel:256 Loops:512 Thr:256 Vec:1

Hashmode: 13600 - WinZip (Iterations: 1000)

Speed.Dev.#2.....:  1544.1 kH/s (479.12ms) @ Accel:256 Loops:250 Thr:256 Vec:1

Hashmode: 13711 - VeraCrypt PBKDF2-HMAC-RIPEMD160 + XTS 512 bit (Iterations: 655331)

Speed.Dev.#2.....:     1353 H/s (425.75ms) @ Accel:256 Loops:128 Thr:256 Vec:1

Hashmode: 13712 - VeraCrypt PBKDF2-HMAC-RIPEMD160 + XTS 1024 bit (Iterations: 655331)

Speed.Dev.#2.....:      773 H/s (371.14ms) @ Accel:256 Loops:64 Thr:256 Vec:1

Hashmode: 13713 - VeraCrypt PBKDF2-HMAC-RIPEMD160 + XTS 1536 bit (Iterations: 655331)

Speed.Dev.#2.....:      540 H/s (265.40ms) @ Accel:128 Loops:64 Thr:256 Vec:1

Hashmode: 13721 - VeraCrypt PBKDF2-HMAC-SHA512 + XTS 512 bit (Iterations: 500000)

Speed.Dev.#2.....:     1531 H/s (247.98ms) @ Accel:256 Loops:64 Thr:256 Vec:1

Hashmode: 13722 - VeraCrypt PBKDF2-HMAC-SHA512 + XTS 1024 bit (Iterations: 500000)

Speed.Dev.#2.....:      752 H/s (253.82ms) @ Accel:128 Loops:64 Thr:256 Vec:1

Hashmode: 13723 - VeraCrypt PBKDF2-HMAC-SHA512 + XTS 1536 bit (Iterations: 500000)

Speed.Dev.#2.....:      503 H/s (378.42ms) @ Accel:128 Loops:64 Thr:256 Vec:1

Hashmode: 13731 - VeraCrypt PBKDF2-HMAC-Whirlpool + XTS 512 bit (Iterations: 500000)

Speed.Dev.#2.....:       86 H/s (1101.56ms) @ Accel:128 Loops:32 Thr:256 Vec:1

Hashmode: 13732 - VeraCrypt PBKDF2-HMAC-Whirlpool + XTS 1024 bit (Iterations: 500000)

Speed.Dev.#2.....:       43 H/s (1098.78ms) @ Accel:64 Loops:32 Thr:256 Vec:1

Hashmode: 13733 - VeraCrypt PBKDF2-HMAC-Whirlpool + XTS 1536 bit (Iterations: 500000)

Speed.Dev.#2.....:       28 H/s (826.10ms) @ Accel:64 Loops:16 Thr:256 Vec:1

Hashmode: 13741 - VeraCrypt PBKDF2-HMAC-RIPEMD160 + XTS 512 bit + boot-mode (Iterations: 327661)

Speed.Dev.#2.....:     2709 H/s (423.51ms) @ Accel:256 Loops:128 Thr:256 Vec:1

Hashmode: 13742 - VeraCrypt PBKDF2-HMAC-RIPEMD160 + XTS 1024 bit + boot-mode (Iterations: 327661)

Speed.Dev.#2.....:     1531 H/s (372.78ms) @ Accel:256 Loops:64 Thr:256 Vec:1

Hashmode: 13743 - VeraCrypt PBKDF2-HMAC-RIPEMD160 + XTS 1536 bit + boot-mode (Iterations: 327661)

Speed.Dev.#2.....:     1088 H/s (265.30ms) @ Accel:128 Loops:64 Thr:256 Vec:1

Hashmode: 13751 - VeraCrypt PBKDF2-HMAC-SHA256 + XTS 512 bit (Iterations: 500000)

Speed.Dev.#2.....:     2046 H/s (374.00ms) @ Accel:256 Loops:128 Thr:256 Vec:1

Hashmode: 13752 - VeraCrypt PBKDF2-HMAC-SHA256 + XTS 1024 bit (Iterations: 500000)

Speed.Dev.#2.....:     1016 H/s (375.51ms) @ Accel:256 Loops:64 Thr:256 Vec:1

Hashmode: 13753 - VeraCrypt PBKDF2-HMAC-SHA256 + XTS 1536 bit (Iterations: 500000)

Speed.Dev.#2.....:      673 H/s (284.47ms) @ Accel:128 Loops:64 Thr:256 Vec:1

Hashmode: 13761 - VeraCrypt PBKDF2-HMAC-SHA256 + XTS 512 bit + boot-mode (Iterations: 200000)

Speed.Dev.#2.....:     5068 H/s (374.46ms) @ Accel:256 Loops:128 Thr:256 Vec:1

Hashmode: 13762 - VeraCrypt PBKDF2-HMAC-SHA256 + XTS 1024 bit + boot-mode (Iterations: 200000)

Speed.Dev.#2.....:     2546 H/s (374.54ms) @ Accel:256 Loops:64 Thr:256 Vec:1

Hashmode: 13763 - VeraCrypt PBKDF2-HMAC-SHA256 + XTS 1536 bit + boot-mode (Iterations: 200000)

Speed.Dev.#2.....:     1695 H/s (281.10ms) @ Accel:128 Loops:64 Thr:256 Vec:1

Hashmode: 13800 - Windows Phone 8+ PIN/password

Speed.Dev.#2.....:  1307.3 MH/s (293.78ms) @ Accel:256 Loops:128 Thr:256 Vec:1

Hashmode: 13900 - OpenCart

Speed.Dev.#2.....:  2992.5 MH/s (256.48ms) @ Accel:256 Loops:256 Thr:256 Vec:1

Hashmode: 14000 - DES (PT = $salt, key = $pass)

Speed.Dev.#2.....: 31496.5 MH/s (97.32ms) @ Accel:256 Loops:1024 Thr:256 Vec:1

Hashmode: 14100 - 3DES (PT = $salt, key = $pass)

Speed.Dev.#2.....:  1482.1 MH/s (259.46ms) @ Accel:32 Loops:1024 Thr:256 Vec:1

Hashmode: 14400 - sha1(CX)

Speed.Dev.#2.....:   516.2 MH/s (372.41ms) @ Accel:256 Loops:64 Thr:256 Vec:1

Hashmode: 14600 - LUKS (Iterations: 163044)

Speed.Dev.#2.....:    13272 H/s (10.15ms) @ Accel:2 Loops:1024 Thr:256 Vec:1

Hashmode: 14700 - iTunes backup < 10.0 (Iterations: 9999)

Speed.Dev.#2.....:   236.5 kH/s (323.22ms) @ Accel:256 Loops:256 Thr:256 Vec:1

Hashmode: 14800 - iTunes backup >= 10.0 (Iterations: 9999999)

Speed.Dev.#2.....:      209 H/s (2.68ms) @ Accel:2 Loops:250 Thr:256 Vec:1

Hashmode: 14900 - Skip32 (PT = $salt, key = $pass)

Speed.Dev.#2.....:  6543.1 MH/s (9.98ms) @ Accel:256 Loops:1024 Thr:256 Vec:1

Hashmode: 15000 - FileZilla Server >= 0.9.55

Speed.Dev.#2.....:  1661.3 MH/s (460.89ms) @ Accel:256 Loops:256 Thr:256 Vec:1

Hashmode: 15100 - Juniper/NetBSD sha1crypt (Iterations: 19999)

Speed.Dev.#2.....:   239.9 kH/s (319.90ms) @ Accel:256 Loops:512 Thr:256 Vec:1

Hashmode: 15200 - Blockchain, My Wallet, V2 (Iterations: 5000)

Speed.Dev.#2.....:   474.4 kH/s (323.42ms) @ Accel:256 Loops:256 Thr:256 Vec:1

Hashmode: 15300 - DPAPI masterkey file v1 (Iterations: 23999)

Speed.Dev.#2.....:    98201 H/s (324.77ms) @ Accel:256 Loops:256 Thr:256 Vec:1

Hashmode: 15400 - ChaCha20

Speed.Dev.#2.....:  5803.5 MH/s (262.99ms) @ Accel:256 Loops:512 Thr:256 Vec:1

Hashmode: 15500 - JKS Java Key Store Private Keys (SHA1)

Speed.Dev.#2.....: 11596.9 MH/s (264.75ms) @ Accel:256 Loops:1024 Thr:256 Vec:1

Hashmode: 15600 - Ethereum Wallet, PBKDF2-HMAC-SHA256 (Iterations: 262143)

Speed.Dev.#2.....:     8391 H/s (347.27ms) @ Accel:256 Loops:256 Thr:256 Vec:1

Hashmode: 15700 - Ethereum Wallet, SCRYPT (Iterations: 1)

Speed.Dev.#2.....:        0 H/s (0.00ms) @ Accel:256 Loops:256 Thr:1 Vec:1
```
