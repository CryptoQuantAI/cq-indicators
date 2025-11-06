# 📊 cq-indicators
### Advanced Technical Indicators for Algorithmic Crypto Trading  
Part of the **CryptoQuantAI** Ecosystem

`cq-indicators` provides a rich collection of **technical indicators**, **feature engineering tools**,  
and **multi-timeframe (MTF) indicator support** for algorithmic trading, ML model pipelines, and quantitative research.

This library is optimized to work seamlessly with:
- cq-ohlcv (data loading)
- cq-backtester (strategy testing)
- cq-trader (live trading)
- cq-aimodels (machine learning/AI trading)

---

## 🚀 Features

- ✅ 100+ technical indicators  
- ✅ Multi-timeframe indicators (MTF)  
- ✅ Cross-asset and cross-exchange compatibility  
- ✅ GPU acceleration support (optional CuPy mode)  
- ✅ ML-ready feature engineering helpers  
- ✅ Zero external dependencies (pure numpy/pandas implementation)  
- ✅ Compatible with any DataFrame (pandas / polars / cuDF)

Includes:
- Moving Averages (SMA, EMA, WMA, HMA, DEMA, TEMA…)  
- Momentum indicators (RSI, Stoch, CCI, Williams %)  
- Volatility indicators (ATR, Bollinger Bands, Donchian)  
- Trend indicators (ADX, SuperTrend, MACD, Ichimoku)  
- Custom Crypto-Specific Indicators (Funding-derived signals, Dominance signals)  

---

## 📦 Installation

```bash
pip install cq-indicators
```

Or install with the entire ecosystem:

```bash
pip install cq-ohlcv cq-backtester cq-trader cq-aimodels
```

---

## 💡 Quick Start

### ✅ Add Indicators to OHLCV Data

```python
from cq_indicators import Indicators
from cq_ohlcv import OHLCV

df = OHLCV("BTCUSDT", "5m").load()
ind = Indicators(df)

df = (
    ind.ema(9)
       .ema(21)
       .rsi(period=14)
       .macd()
       .bollinger(20)
       .compute()
)

print(df.tail())
```

---

## ✅ Multi-Timeframe Indicators (MTF)

```python
from cq_indicators import Indicators
from cq_ohlcv import OHLCV

df = OHLCV("BTCUSDT", "1m").load()

mtf_df = Indicators(df).mtf("15m").ema(20).compute()
```

Produces a 15m EMA aligned to 1m timestamps.

---

## ✅ Feature Engineering for ML

```python
from cq_indicators import Features

feat = Features(df)

df = feat.percent_change(["close"], periods=[1,3,5])
df = feat.zscore(["close", "volume"])
df = feat.normalize(["rsi_14"])
```

---

## 🔧 Supported Indicators (Partial List)

```
Moving Averages:
- sma, ema, wma, hma, tema, dema
Momentum:
- rsi, stoch, cci, mfi, williams_r
Volatility:
- atr, bollinger, donchian
Trend:
- macd, supertrend, ichimoku, adx
Custom:
- crypto_vix, funding_slope, dominance_flow
```

Full list available in documentation.

---

## 🗂 Folder Structure

```
cq-indicators/
│
├── cq_indicators/
│   ├── __init__.py
│   ├── indicators.py
│   ├── mtf.py
│   ├── features.py
│   │
│   ├── core/
│   │   ├── math_ops.py
│   │   ├── smoothing.py
│   │   ├── transforms.py
│   │
│   └── utils/
│       ├── validators.py
│       ├── dataframe_tools.py
│
├── tests/
├── examples/
└── README.md
```

---

## 📅 Roadmap

- ✅ Add more volatility models (Keltner, Chaikin, RangeFlow)  
- ✅ Better ML feature pipelines  
- ⏳ GPU-native mode using Numba + CuPy  
- ⏳ Polars-native indicator backend  
- ⏳ Real-time streaming indicators  

---

## 🤝 Contributing

We welcome contributions from:
- Quant developers  
- Python engineers  
- ML researchers  
- Crypto traders  

Guidelines:
- PEP8 + type hints  
- Use Black for formatting  
- Add unit tests for new indicators  

---

## ⚖️ License

MIT License — fully free for commercial & personal use.

---

## 👨‍💻 Maintained By

**CryptoQuantAI Development Team**  
AI-Powered Trading Infrastructure
