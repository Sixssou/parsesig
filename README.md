# Parsesig

![Parsig](https://github.com/konichar/parsesig/blob/master/parsig.png)

## Before ALL, you need to have a telegram bot which will forward the message from the first group to another group in which this bot is admin.
So Follow this insctructions https://sendpulse.com/knowledge-base/chatbot/create-telegram-chatbot

## You will need to create a telegram app in order to get the api id and api hash
1. Go to my.telegram.org , if not accessible than use any VPN
2. Enter Telegram phone number in format +918457345497
3. Enter the received code on @telegram
4. Click on Create Application
5. Enter any name and nickname.
6. Select other and leave discription empty and proceed.
7. You will get your APP ID & HASH

## Create a .env from the .env.example
And put the parameters you got in the previous steps

## A Telegram program that forwards Forex Signals from one Telegram group or channel to another

Listens for message events on CHATINPUT channel that matches the Regex pattern 
`^(BUY|SELL)\s([A-Z]*)\s[\(@at\s]*([0-9]*[.,][0-9]*)[\).]` 
and passes it with `pasig()` Engine

```comment
                                |     #EURUSD
BUY EURUSD (@ 1.0877)           |     BUY📈1.0877
Take profit 1 at 1.0897         |     ✅TP 1.0897
Take profit 2 at 1.0927         |     ✅TP 1.0927
Take profit 3 at 1.0977         |     ✅TP 1.0977
Stop loss at 1.07978            |     🛑SL 1.07978
```

Sigparser takes the following environment variables or configure .env file in the project directory
Main pair

  ```python
  API_HASH = f36c29aaaaa698ecb1e59e31b
  API_ID = 127555
  CHATINPUT = -12345678901234
  CHATOUTPUT = -1234567890123
  SESSION = *this would be auto generated at first run*
  ```

All matching messages from the channel set in the CHATINPUT environment variable 
is forwarded to the channel set in the CHATOUTPUT environment variable same goes for the test variables


## Heroku setup

---

* Create new Heroku app on your [Heroku account](https://heroku.com).
* Link app to using the github option and select the repository
* From terminal set git heroku remote url
   
  ```bash
  git remote set-url --add heroku https://git.heroku.com/{your_app_name}.git
  heroku login
  ```

* After build and deploy succeed, check for the number of running dynos

  ```bash
  heroku ps
  ```

  *this application is define from the Procfile as a worker process, on first build number of dynos=0*
* Set environment variables on heroku, goto settings and reveal config vars and set key:value
  *Start up one dyno with a single process*

  ```bash
  heroku ps:scale worker=1
  ```


=======
## Local PC and ubuntu server setup 

---

* Download and Install [Python intepreter](https://www.python.org/) and git
* From terminal 
```bash
git clone https://github.com/konichar/parsesig
cd parsesig
```
* Add environment variables to .env file
* From terminal 
``` 
pip install -r requirements.txt
python telethon_access.py
```
 *On first run you would be asked for your Phone number and a verification code*
 *a valid SESSION would be generated and added to your .env file*
