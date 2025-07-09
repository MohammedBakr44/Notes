#whois #dig #nslookup #recon #shodan

Reconnaissance(recon) -استطلاع- is the process of collecting information about a target.

- Passive recon(public data and no interaction with target)
- Active recon(direct engagement with the target)

## Passive recon

- Looking up DNS records of a domain from a public DNS server.
- Checking job ads related to the target website.
- Reading news articles about the target company.

### whois

WHOIS is a request and response protocol that follows the [RFC 3912](https://www.ietf.org/rfc/rfc3912.txt) specification. A WHOIS server listens on TCP port 43 for incoming requests.

### nslookup

`nameserver lookup`

```
nslookup OPTIONS DOMAIN SERVER
```


- OPTIONS contain query types
	A: IPv4 addresses
	AAAA: IPv6 addresses
	CNAME: Canonical Name
	MX: Mailserver
	SOA: State of Authority
	TXT: TXT records

- Server: DNS used to query(e.g: Cloudflare's `1.1.1.1`, `1.0.0.1` and google's `8.8.8.8`)

example
```
nslookup -type=A tryhackme.com 1.1.1.1
```

output:
```
Server:         1.1.1.1
Address:        1.1.1.1#53

Non-authoritative answer:
Name:   tryhackme.com
Address: 104.22.54.228
Name:   tryhackme.com
Address: 172.67.27.10
Name:   tryhackme.com
Address: 104.22.55.228
```

MX example:
```
nslookup -type=MX tryhackme.com
```

```
Server:         199.85.126.30
Address:        199.85.126.30#53

Non-authoritative answer:
tryhackme.com   mail exchanger = 10 alt4.aspmx.l.google.com.
tryhackme.com   mail exchanger = 5 alt1.aspmx.l.google.com.
tryhackme.com   mail exchanger = 5 alt2.aspmx.l.google.com.
tryhackme.com   mail exchanger = 1 aspmx.l.google.com.
tryhackme.com   mail exchanger = 10 alt3.aspmx.l.google.com.
```

THM uses google as a mailserver; whenever an email is sent to THM the mail server tries to deliver the mail to `@tryhackme.com`, it will start with the server with number 1 i.e `aspms.l.google.com` if it failed it will move the next one in order i.e `alt1.aspms.l.google.com` ordered `5`.

### dig

```
dig DOMAIN TYPE
```

```
dig tryhackme.com MX
```

dig returned more details about the servers

```
; <<>> DiG 9.20.4 <<>> tryhackme.com MX
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 54129
;; flags: qr rd ra; QUERY: 1, ANSWER: 5, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 4096
;; QUESTION SECTION:
;tryhackme.com.                 IN      MX

;; ANSWER SECTION:
tryhackme.com.          300     IN      MX      10 alt3.aspmx.l.google.com.
tryhackme.com.          300     IN      MX      10 alt4.aspmx.l.google.com.
tryhackme.com.          300     IN      MX      5 alt1.aspmx.l.google.com.
tryhackme.com.          300     IN      MX      5 alt2.aspmx.l.google.com.
tryhackme.com.          300     IN      MX      1 aspmx.l.google.com.

;; Query time: 103 msec
;; SERVER: 199.85.126.30#53(199.85.126.30) (UDP)
;; WHEN: Sat Jun 14 02:45:37 EEST 2025
;; MSG SIZE  rcvd: 157
```

### dnsdumpster

An [online tool](https://dnsdumpster.com/) that fetches subdomains based on DNS records.

## Active recon

- Connecting to one of the company servers such as HTTP, FTP, and SMTP.
- Calling the company in an attempt to get information (social engineering).
- Entering company premises pretending to be a repairman.


