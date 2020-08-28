# Deprecated
Either the people who manage the account servers fixed this, or the Nebulous servers are just garbage. ¯\_(ツ)_/¯

You can use the following(really basic) batch script to get the most out of a view bot:
```
@echo off

set /a views=0
set /a total_views=0

rem set your ticket here vv. before setting it though, make sure it's url-encoded.
rem see the text below this script for a website you can use to url-encode your ticket.
set /a ticket=

rem set the account id here that will recieve the views
set /a accID=0

:loop
if %views% equ 25 (
  echo Total views: %total_views%
  timeout /t 30 /nobreak
  set /a views=0
)

curl -d "Game=Nebulous&Version=1065&Ticket=%ticket%&accountID=%accID%" https://www.simplicialsoftware.com/api/account/GetPlayerProfile

set /a views+=1
set /a total_views+=1

goto :loop
```
This will work provided you don't stop, then restart the script within the same minute. Also, you'd be averaging 25 views per minute, lol.
The reason why I capped the view count to 25 per minute is because on the 30th profile request without pausing, the server will begin to send back a `400 Bad Request` error.

[url-encode your ticket here](https://www.urlencoder.org/)

# Nebulous-ViewBot
Become a celebrity on Nebulous.

## Dependencies
* [Python 3](https://www.python.org/downloads/)
* urllib3 `pip install urllib3`

## Usage
Just add a login ticket where `LOGIN_TICKET` is inside viewbot.py
```
usage: viewbot.py [-h] [-t THREADS] [-v VIEWS] account_id

Become a celebrity on Nebulous.

positional arguments:
  account_id            Nebulous account ID to give the views to.

optional arguments:
  -h, --help            show this help message and exit
  -t THREADS, --threads THREADS
                        Number of threads(workers) to use.
  -v VIEWS, --views VIEWS
                        The number of views to work towards.

https://www.github.com/Anthy1x
```
Insta: [@r0x35c](https://www.instagram.com/r0x35c)

## Warning
I am not responsible for what you do with this. I am not responsible for what happens to you or your account by using this.
