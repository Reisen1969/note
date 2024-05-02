https://cn.tradingview.com/support/solutions/43000502332/


KDJ指标的学名叫做“Stochastic Oscillator”，标准的译法是“随机震荡指标”，这个指标由“K”“D”“J”三根指标线构成，所以国内最早引进这个指标的时候把它亲切地称为“KDJ”。


随机震荡指标（Stochastic Oscillator，简称STOCH）是一种常用的技术分析工具，用于衡量当前价格相对于一定时间范围内的价格区间的位置。它可以帮助交易者判断市场的超买和超卖情况，以及市场转势的可能性。STOCH 主要由两条线组成：%K线和%D线。


### 计算

%K 是收盘价 (K) 在回测期中使用的K线数的价格范围内的百分比。

%K = SMA(100 * (Current Close - Lowest Low) / (Highest High - Lowest Low), smoothK)

Current Close  是当前的收盘价，Lowest Low 是一定时间范围内的最低价，Highest High 是一定时间范围内的最高价。



%D 是 %K 的平滑平均值，以在保持较大趋势的同时最小化洗盘。

%D = SMA(%K, periodD)

> smoothK 和 periodD 都是 指的长度
>  TV官方的 SMA 函数:  ta.sma(source, length) → series float


### 基础

随机震荡指标是一个区间震荡指标，由在 0 和 100 之间移动的两条线组成。第一条线（称为 %K）显示当前收盘价相对于用户定义周期的高/低范围。第二条线（称为 %D）是 %K 线的简单移动平均线。现在，与大多数指标一样，随机指标中使用的所有周期都可以由用户定义。也就是说，最常见的选择是 14 周期的 %K 和 3 周期的 %D SMA。

基本理解是随机指标使用收盘价来确定动量。 当价格收于回顾期高/低范围的上半部分时，随机震荡指标 (%K) 上升也表明动能或买/卖压力增加。 当价格收于该期间高/低范围的下半部分时，%K 下降，表明势头减弱或买/卖压力。