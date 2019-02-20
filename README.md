# LRBot

LinRegBot is a trading bot for Binance and Poloniex.
(Further crypto exchanges are planned.)


Unlike most bots, it has its own approach. Because the trading methodology is encapsulated in modules, one can change the complete trading strategy.


Currently there are two modules; both have in common that in bear times the bot exchanges all coins against USDT to keep the balance.

Normal Bots usually stay in coins and have thus faced 2018 massive losses in 2018.


Further strategy modules are under development.

All modules so far are separating early from falling coins, therefore there are no Bags and no DCA, which solves smaller problems, but in the countermove creates larger ones.


A backtest module is included - see backtest_readme.txt.

**If you are interested contact me via Telegram (@pewi2017) or e-mail (autopt_binance@gmx.net)**


_ATTENTION: Version V0.7.1 or higher requires a license!
See license_readme.txt._




## Requirements and installation


The computer language Python must be installed in the 64-bit version. Under Windows version 3.6.x is supported, under Linux the two Versions 3.5.x and 3.6.x.

Attention: Under Ubuntu 18.04 there is a problem. The Python 3.6 there has been created with other compiler flags and leads to an error message at startup ("undefined symbol: PyFPE_jbuf").
If you manually google Python 3.5 and install the 35 archives of the LRBot, it will work.



### Installation for Windows:

- install Python 3.6 (64 bit)
- unpack LRBot Zip archive into a new directory
- open console window and change to the directory
- launch lrinstall1.cmd
- launch lrinstall2.cmd

Done.



### Installation for Linux:

- install Python 3.5 (64 bit) if necessary
- unpack the appropriate LRBot-Zip archive into a new directory
- open console window and change to the directory
- python3 -m venv.env
- source.env/bin/activate
- ./lrinstall2.sh

Done.


## Adjust settings in the Configs

- customize lrbot.secrets.ini

- customize lrbot07.ini

- lrbot07.ini is set to paper trading using strategy 'ma3' by default.

- If you want to use the bot to administer money, then you should perform extensive tests to find suitable settings for your choosen strategy.

- More about this in the file backtest_readme.txt (sorry - currently only in german language) for the supplied backtest module.
Additionaly you can find there descriptions to all parameters of the config file.



## Launch LRBot

License file lrbot.lic available and in the bot directory?

If so, then:

```
Windows: python bot07.py (better: lrbot.cmd)
Linux:   python3 bot07.py (better: ./lrbot.sh (or use pm2))
```

The bot sends a telegram message after the startup, reports the balance after each new candle times the balance and the amount of coins you just own. Every buy and sell is reported also. If you like, you can also enable info message at every candle on Telegram.

You can abort the bot at any time with CTRL-C and then restart it again because the bot recreates all runtime data by the information from the exchange.


However - if the bot is currently fetching candles, the CTRL-C only stops the current URL call, not the whole bot! The
bot then continues fetching the next candle etc. In this case you have to wait until all candles are fetched (see Log-File) and then abort again with CTRL-C.
