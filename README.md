# Crypto Technical Analysis Alert Bot

A Python-based cryptocurrency technical analysis alert system that monitors multiple markets in real time and delivers structured trading signals via Telegram.
Designed to be lightweight, configurable, and deployable on local machines or VPS environments.

Alerts only — no automated trading.

## Overview

This bot continuously analyzes price action using a carefully selected set of widely adopted technical indicators. Alerts are generated when predefined technical conditions are met, with built-in throttling to prevent notification spam.

The project emphasizes:

Clean indicator logic

Signal reliability over frequency

Minimal operational overhead

Safe separation from trading execution

Technical Indicator Stack

The following indicators are implemented to provide trend, momentum, volatility, and contextual bias:

EMA (20 / 50 / 200) — Trend direction and structure

RSI — Momentum and overbought/oversold conditions

MACD — Momentum shifts and signal confirmation

VWAP — Volume-weighted price context

ATR — Volatility measurement

Support & Resistance — Key reaction levels

Multi-Timeframe Bias — Higher timeframe trend alignment

This combination balances signal quality and computational efficiency.

Alert Types

The bot generates alerts for the following scenarios:

RSI overbought / oversold conditions (with higher timeframe bias)

EMA20 / EMA50 crossover events (validated against EMA200 trend)

MACD signal line crossovers

Price interaction with detected support or resistance levels

EMA200 tests (major trend interaction)

VWAP positioning (above / below value area)

Significant price movements (configurable percentage threshold)

Anti-Spam & Reliability Controls

Cooldown enforcement per alert type

Duplicate signal suppression

Graceful handling of API interruptions

Lightweight polling suitable for VPS deployment

## Supported Markets

Currently monitored pairs (configurable):

BTCUSDT

ETHUSDT

DOGEUSDT

SOLUSDT

BNBUSDT

Additional pairs can be added easily via configuration.

##Setup & Usage
Environment Variables

Create a .env file using the provided example:

TELEGRAM_BOT_TOKEN=your_bot_token
TELEGRAM_CHAT_ID=your_chat_id

## Install Dependencies
pip install -r requirements.txt

Run the Bot
python alert_bot.py


The bot runs continuously until manually stopped.

## Configuration

Core parameters can be adjusted to match individual trading styles:

WATCHLIST = ["BTCUSDT", "ETHUSDT", "DOGEUSDT"]

RSI_OVERSOLD = 30
RSI_OVERBOUGHT = 70
PRICE_CHANGE_ALERT = 0.03   # 3% price move

CHECK_INTERVAL = 300        # seconds
TIMEFRAME = "15"            # candle timeframe (minutes)


Future refactoring may move configuration to external files for improved modularity.

Example Alert Output
BTCUSDT — RSI OVERSOLD

RSI: 28.45
Price: $42,150.50
Context: Higher timeframe bullish
Time: 14:23:45

ETHUSDT — EMA BULLISH CROSSOVER

EMA20 crossed above EMA50
Price: $2,245.30
EMA200: $2,180.10
Time: 14:25:12

## Deployment Notes

Runs on Windows, Linux, or macOS

Tested on Python 3.11.9

Suitable for VPS environments (Ubuntu recommended)

Uses public exchange market data (no trading API keys required)

## Disclaimer

This project is for educational and research purposes only.
It does not constitute financial or investment advice.
Use at your own risk.

## License

MIT License
