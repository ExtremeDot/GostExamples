### توضیحات کلی به زبان فارسی

### مستندات پروتکل‌های GOST
نرم افزار GOST یک سرویس یا نود است که به دو لایه تقسیم می‌شود:

لایه پردازش داده و لایه کانال داده.

هر لایه با یک پروتکل شبکه مطابقت دارد. این دو لایه مستقل از یکدیگر هستند و می‌توانند با هر ترکیبی (به جز محدودیت‌های خاص) استفاده شوند.

----------
#### پردازش داده
پردازش داده به دو نوع تقسیم می‌شود: پراکسی و فورواردینگ.

##### پراکسی (Proxy)
`http` - پروتکل HTTP

`http2` - پروتکل HTTP2

`socks4` - پراکسی SOCKS4/SOCKS4A

`socks`, `socks5` - پراکسی SOCKS5

`ss` - Shadowsocks

`ssu` - Shadowsocks UDP Relay

`sni` - پراکسی SNI

`relay` - Relay
فورواردینگ (Forwarding)
`tcp` - فورواردینگ پورت TCP

`udp` - فورواردینگ پورت UDP

`rtcp` - فورواردینگ پورت TCP از راه دور

`rudp` - فورواردینگ پورت UDP از راه دور

-------------------

##### کانال داده
کانال داده برای حمل داده‌های پروتکل پراکسی یا فوروارد استفاده می‌شود. پروتکل‌های کانال داده پشتیبانی‌شده به شرح زیر هستند:

`tcp` - پروتکل TCP خام

`mtcp` - مالتی‌پلکس بر روی TCP خام

`udp` - پروتکل UDP خام

`tls` - پروتکل TLS

`dtls` - پروتکل DTLS

`mtls` - مالتی‌پلکس بر روی TLS

`ws` - وب‌سوکت

`mws` - مالتی‌پلکس بر روی وب‌سوکت

`wss` - وب‌سوکت امن

`mwss` - مالتی‌پلکس بر روی وب‌سوکت امن

`h2` - HTTP2

`h2c` - HTTP2 Cleartext

`grpc` - gRPC

`pht` - Plain HTTP Tunnel

`ssh`, `sshd` - SSH

`kcp` - پروتکل KCP

`quic` - پروتکل QUIC

`h3` - PHT بر روی HTTP/3

`wt` - WebTransport بر روی HTTP/3

`ohttp` - مخفی‌سازی HTTP

`otls` - مخفی‌سازی TLS

`icmp`, `icmp6` - پروتکل‌های ICMP و ICMPv6

`ftcp` - Fake TCP

-----------------------


##### پروتکل‌های خاص
`file` - سرور فایل HTTP

`https` - معادل ترکیب پراکسی HTTP و کانال TLS (http+tls)

`http3` - سرویس پراکسی معکوس HTTP3

`dns` - پراکسی DNS

`red`, `redir`, `redirect` - پراکسی شفاف TCP

`redu` - پراکسی شفاف UDP

`tun` - دستگاه TUN

`tap` - دستگاه TAP

`forward` - فورواردینگ سمت سرور

`virtual` - نود مجازی

`unix` - Redirector سوکت دامین یونیکس

`serial` - Redirector پورت سریال

-----------


##### محدودیت‌ها
همه کانال‌های داده بر اساس پروتکل UDP (مانند kcp، quic، h3، wt، و همچنین icmp) فقط برای نودهای سطح اول در زنجیره فورواردینگ قابل استفاده هستند.

----------

برای استفاده از GOST به همراه WireGuard و OpenVPN، باید پروتکل‌های مناسب برای انتقال داده و مدیریت ترافیک بین این سرویس‌ها انتخاب شوند. در اینجا توضیحات کامل‌تر درباره استفاده از GOST با WireGuard و OpenVPN ارائه می‌شود:

##### استفاده از GOST با WireGuard
وایرگارد یک پروتکل VPN است که بر اساس UDP کار می‌کند.

برای استفاده از GOST با WireGuard، شما باید از کانال‌های داده‌ای که بر اساس UDP هستند استفاده کنید. 

گزینه‌های مناسب شامل موارد زیر هستند:

1- `udp` - پروتکل UDP خام:
می‌تواند برای انتقال مستقیم بسته‌های UDP از WireGuard استفاده شود.

2- `kcp` - پروتکل KCP:
KCP یک پروتکل انتقال سریع و کم‌تاخیر است که بر روی UDP کار می‌کند و می‌تواند باعث بهبود عملکرد و کاهش تأخیر در شبکه‌های غیرقابل اعتماد شود.

. `quic` - پروتکل QUIC:
QUIC یک پروتکل لایه انتقال مبتنی بر UDP است که با ویژگی‌های مشابه TLS عمل می‌کند. برای افزایش امنیت و سرعت ارتباط مناسب است.

4- `dtls` - پروتکل DTLS:
DTLS نسخه‌ای از TLS است که برای UDP طراحی شده و امنیت ارتباطات را بهبود می‌بخشد.


-----------------
##### استفاده از GOST با OpenVPN


سرویس OPenVPN می‌تواند بر روی پروتکل‌های TCP یا UDP کار کند.


بسته به نوع تنظیمات OpenVPN، گزینه‌های مناسب GOST برای انتقال داده می‌تواند متفاوت باشد:

1- برای OpenVPN با UDP:

  * همان گزینه‌های WireGuard که شامل `udp`، `kcp`، `quic`، و `dtls` هستند، قابل استفاده خواهند بود.

2- برای OpenVPN با TCP:

  * `tcp` - پروتکل TCP خام:
می‌تواند برای انتقال مستقیم بسته‌های TCP از OpenVPN استفاده شود.

* `tls` - پروتکل TLS:
برای تأمین امنیت ارتباطات TCP، TLS یک انتخاب مناسب است که رمزگذاری را فراهم می‌کند.

* `mtcp` - مالتی‌پلکس بر روی TCP:
این پروتکل به شما اجازه می‌دهد چندین ارتباط TCP را به صورت همزمان و بهینه‌تر از طریق یک کانال TCP منفرد مدیریت کنید.

3- دیگر کانال‌های مناسب:

* `ws` و `wss` - وب‌سوکت (معمولی و امن):
این پروتکل‌ها می‌توانند برای عبور از محدودیت‌های فایروال یا پراکسی‌ها مفید باشند.

* `grpc` و `h2` - پروتکل‌های گرافیکی و HTTP2:
می‌توانند برای بهینه‌سازی انتقال داده‌ها در ارتباطات TCP به کار روند، مخصوصاً در مواقعی که نیاز به پوشش بالای امنیت و عملکرد داریم.

-------
##### نکته‌های مهم
  * اگر از پروتکل‌های مبتنی بر UDP مانند WireGuard استفاده می‌کنید و به دلیل محدودیت‌های شبکه، به TCP نیاز دارید، می‌توانید از `ftcp` *(Fake TCP)* استفاده کنید که داده‌های UDP را در قالب بسته‌های TCP منتقل می‌کند.

  * برای تنظیمات مخصوص به هر شبکه و برای افزایش کارایی، ممکن است نیاز به تنظیمات خاص GOST مانند تنظیمات مالتی‌پلکس و یا رمزگذاری‌های پیشرفته باشد.
این توضیحات می‌توانند به شما کمک کنند تا پروتکل مناسب برای استفاده با WireGuard و OpenVPN انتخاب کنید.
