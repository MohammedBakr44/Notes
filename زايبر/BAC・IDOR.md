
#bug_hunting, #rakuten

# General Methodology

## Defining target

The target should be suitable with the kind of vulns you're working on, e.g: for BAC ・IDOR you need targets with multi-user functionality so the probability of having these vulns.


## Tech stack
- Akamai
- JQuery
- Apache
- HTTP/2
## Pointers

As for Rakuten, the initial request `GET /?l-id=top_normal_myrakuten_account` returns a boilerplate. 
Meanwhile another request `app.rakuten.co.jp/engine/zapi/MemberInformation/GetPointWithRz/20170907`. Returns a json of user info; this lead to the conclusion that the rendering is done server-side.

And this specific endpoint is what returns user info based on one of the cookies it have.

```
GET /engine/zapi/MemberInformation/GetPointWithRz/20170907 HTTP/1.1
Host: app.rakuten.co.jp
Cookie: _ra=1739711447631|7d5071bf-3080-441c-bb96-433b7de05995; Rp=dd4a459b4ad0a3bc8657c542b4ff48876e134248; Rz=A4hXKOlc_KAK7AxfvRvGaKkQt7TG4TWen7_Ly2lQ-P2_pEmSzp-K9bkByORxJVObvWzjSRZUOzGN_zwm1XT78UbIwNDlqOR4xR9A8i-JeX1-Jg_iKJBOYo2BCiQV-Kjw0w~~; Rq=M01.2&67b3594e; Rb=1s69c70M01&omnit246; Ra=A58Q-1G3EWjdpQWiJn4brY_p54OSz4qQjjtYhMC8Dn_5GslbZG6SjrHMofQXIoXIaHF9yS84wDS0vewP1Ff_ulS3aUEnTc5d1-ArEzckXh09LA~~; ak_bmsc=5AAEE8EAFA1371E2F13D0EB18DAB0654~000000000000000000000000000000~YAAQQO8WAggirgCVAQAAseGUFBrIbg3m+m/wauTrbTg7q78W31WUakxpmuGpUXcArw8Mm/DnZMVS9yE2UOPYr/HRmcZtx6jk2Bg+rFGwvLVkpR9TBEU3aqfnrL5pxnsRljpoP19mIeC8XLVlrh0iIICc0nnljIo+dg9rkuVSMXwDjQ4qNBMYprlaxDS35U5odr/HMmqa8+iLEiV0zvaA9NNRrfbODtDHaS89T0RY82d4kPTehZLgJmL1qeSB8RTC954ahIkEpNfaLT73GNfmXlegRowQ+6rTT8Jr0EYPwJCWwoBVGcEBUewaKr9SLdPaD7ZhxUdPpZWq1/+zAlulbv5cW7jEE/OvYpXI0VPDPhCuNISf3gDnQQN7PDXpcrJjYwkILOCPcnoYnMkF; bm_mi=F768074D3FE85FFE18CF5251A3F03CC9~YAAQQO8WAjEirgCVAQAAneeUFBpKH3crwGnqGTvQEVXSweb9QBgBA0Ub+RwEr+RgHjoVcwpJXwhse1WjlvTyPcWboehWRWKQUCTC/V0BKJWidmiZZDBZ3uwN8V8xNoV4ZrExRuqwqywWHCiiMB+hdaDdskq1JPLWKjCy8kpCqdWsb4khy1ESMZuUxKb0al9TVqALozlGQPGMjtkZf4tCe64y/uOwcPqiIPg9ZIMjvBaWSvNykEhEULkQgfZViNUW+JiE521u1LAwCjnqST9ykC38lIAmzF4qwDz3lrws6R+ozzoekUWa1xYm5ZBoaBFu~1; bm_sv=2D33A4618095A8952B67752BFE1C68A5~YAAQQO8WArMirgCVAQAASgGVFBoU461CO68gg6M6yXYojgZPXVZ2IWK0fkJBspUsM0mvaXqfdQcVlcGOH5f1uMhaLwzRhZMVZkt/kfFkDCmCoerA+kxOWPufQNHil1r7GS7h9EycAZZl5esqcoo6Mb1KHvHV56PiCPHX1IuaYIZIfLf4uUofwZ0uOOnAQ0NdoqrAWQrFLWJIdlv5UBxhD4eTRSIPSbU9ZczxKLQpbmAibXJ+UPbPf2X2s/dgllJzj0jA~1
```

The only cookie we need to get a successful response is `rz`.

```
GET /engine/zapi/MemberInformation/GetPointWithRz/20170907 HTTP/1.1
Host: app.rakuten.co.jp
Cookie: Rz=A4hXKOlc_KAK7AxfvRvGaKkQt7TG4TWen7_Ly2lQ-P2_pEmSzp-K9bkByORxJVObvWzjSRZUOzGN_zwm1XT78UbIwNDlqOR4xR9A8i-JeX1-Jg_iKJBOYo2BCiQV-Kjw0w~~;
```

Which leads to our first pointer(ironically it's the same as the video)
- CSRF Token doesn't appear to be used with the above GET request. 
## Accounts

reizouko+user1@bugcrowdninja.com

reizouko+user2@bugcrowdninja.com


## Methodology

- Look for functions that uses authentication methods e.g: cookies, tokens, etc...
- We need to make sure if it happens in FE or BE:
	- We look for personal info in the initial response of the request used to get data, if our data is in there then the data is fetched from the backend, otherwise the backend could be starting the DOM and some inner request-e.g Nextjs request- is fetching the data.
- After we find the request that's responsible of getting data from server, we try to minimise the request by testing with different cookies removed until we have the smallest request possible that returns a successful response.