# LinRegBot
LinRegBot (short LRBot) is a trading bot for Binance and Poloniex.
Further crypto exchanges are planned.

### Strategy
Unlike most other bots it has its own approach. Because the trading methodologies are encapsulated in modules, one can change the complete trading strategy at will.

Currently there are two modules; both have in common that in bear markets the bot exchanges all coins in stable coins (USDT) in order to keep the balance. Normal bots usually stay in coins and thus faced massive losses in 2018. Further strategy modules are under development.

All modules so far are selling falling coins as soon as sensible, therefore there are no bags and no DCA is needed, which - even though it solves smaller problems - creates larger bags.

### Backtest
A backtest module is included, please see the documentation.

### License
Since version 0.7.1 a license is required to operate the bot, please see the documentation.
If you are interested contact me via Telegram (@pewi2017) or e-mail (autopt_binance@gmx.net)

## Requirements and installation
### Requirements
Windows:  
Python 64bit version 3.6.x  
Linux:  
Python 64bit version 3.5.x or 3.6.x

Attention:  
In Ubuntu 18.04 und higher there's a problem with Python 3.6, which leads to an error ("undefined symbol: PyFPE_jbuf") and program crash. Workaround: Manually install Python 3.5 and use the Python 3.5.x archives of LRBot.

### Installation
Windows:  
- install Python 3.6 (64 bit)  
- unpack LRBot ZIP archive into a new directory  
- open console window and changedir to the directory  
- ```lrinstall1.cmd```  
- ```lrinstall2.cmd```  
- copy license file lrbot.lic into the directory  

Linux:  
- install Python 3.5 or 3.6 (64 bit)  
- unpack the appropriate LRBot ZIP archive into a new directory  
- open console window and changedir to the directory  
- ```python3 -m venv .env```  
- ```source .env/bin/activate```  
- ```./lrinstall2.sh```  
- copy license file lrbot.lic into the directory  

(Excursus for better understanding of virtual environment see below)

Adjust settings in the config files:  
- customize lrbot.secrets.ini  
  (API key and secreat, Telegram ID, credentials for cryptocompare.com if required)  
- lrbot.ini  
  Paper trading with strategy ma3 is used by default

**Attention:**
If you want to use the bot to trade real money, then you should perform extensive tests to find suitable settings for your chosen strategy. More about this in the documentation (sorry - currently only available in german) for the backtest module. You'll also find the description to all parameters of the config file in this documentation.


## Launch LRBot
Windows:  
```lrbot.cmd```  
Linux:  
```./lrbot.sh```

If you want to use another config file, you can do this with the '-c <configfile>' parameter.

The bot displays several status messages on comsole and Telegram:  
- on programm launch
- on each new candle (balance and stock)
- on each buy and sell
- optionally info messages on each new candle

All messages except for buy/sell may be switched off in the config

You can abort the bot at any time with CTRL-C and restart it again, because the bot recovers all runtime data from the exchange. Some operations (fetching candles, buy/sell) can't be interrupted immediately, the bot will continue this operation to the end and then stops afterwards.


## EXCURSUS
Only for better understanding ;-)

Under Python you can create virtual environments. This has the advantage, that different Python programs, which might need different modules cannot influence each other because they run within their own environment with its own modules. Every virtual Python environment is starting from scratch. Any required module have to be installed once in each virtual environment.

You don't need sudo on Linux when installing modules in the virtual environment, as the virtual environment is created in the context of the logged in user.

The LRBot works in such a virtual Python environment, which is created during the installation. Here some explanations and notes on what the installation does.

### First time creation of virtual environment
- chdir to the directory where the Python files of LRBot are located
- create virtual environment  
Windows:  
```python -m venv.env```  
Linux:  
```python3 -m venv.env```

You may need to install Python's virtual environment first:  
```sudo pip3 install virtualenv```

The virtual Python environment with all necessary files is created in a subdirectory .env in the current directory.

### Activate the virtual environment for installation and start of LRBot
Windows:  
```.env\Scripts\activate.bat```  
Linux:  
```source .env/bin/activate```  

The console prompt changes to indicate that the environment was activated.
Under Windows you often get an error message about a wrong codepage, which can be safely ignored.

In case you want to leave the virtual environment:  
Windows:  
```.env\Scripts\deactivate.bat```  
Linux:  
```deactivate```

### Install the necessary Python modules in the virtual environment
- update pip if necessary:  
Windows:  
```python -m pip install --upgrade pip```  
Linux:  
```python3 -m pip3 install --upgrade pip```  
- install modules:  
Windows:  
```pip install  -r requirements.txt```  
Linux:  
```pip3 install -r requirements.txt```  

END EXCURSUS
