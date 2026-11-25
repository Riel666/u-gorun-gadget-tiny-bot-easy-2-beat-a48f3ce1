# u-gorun-gadget-tiny-bot-easy-2-beat-a48f3ce1

[![make.fun · u-gorun-gadget-tiny-bot-easy-2-beat-a48f3ce1](https://make.fun/badge/u-gorun-gadget-tiny-bot-easy-2-beat-a48f3ce1.svg)](https://make.fun/bounty/u-gorun-gadget-tiny-bot-easy-2-beat-a48f3ce1?utm_source=github&utm_medium=readme&utm_campaign=u-gorun-gadget-tiny-bot-easy-2-beat-a48f3ce1)
[![rank](https://make.fun/badge/u-gorun-gadget-tiny-bot-easy-2-beat-a48f3ce1/Riel666/u-gorun-gadget-tiny-bot-easy-2-beat-a48f3ce1/rank.svg)](https://make.fun/bounty/u-gorun-gadget-tiny-bot-easy-2-beat-a48f3ce1/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=u-gorun-gadget-tiny-bot-easy-2-beat-a48f3ce1)
[![reward](https://make.fun/badge/u-gorun-gadget-tiny-bot-easy-2-beat-a48f3ce1/Riel666/u-gorun-gadget-tiny-bot-easy-2-beat-a48f3ce1/reward.svg)](https://make.fun/bounty/u-gorun-gadget-tiny-bot-easy-2-beat-a48f3ce1?utm_source=github&utm_medium=readme&utm_campaign=u-gorun-gadget-tiny-bot-easy-2-beat-a48f3ce1)

A tiny paper-trading bot for hourly Solana prices: it buys only oversold dips and banks the small bounce.

The rule is deliberately simple. For each of the seven symbols it tracks Wilder's RSI(14) over hourly closes. When RSI drops under 32 it buys one equal stake (equity split over seven slots, capped at 25% of equity). It sells the whole position when the position is worth 1% over its cost, 6% under its cost, or RSI rises over 70. No shorts, no leverage, no outside data, no network — the bot only ever reads the bars the harness sends it.

On the dev window that rule scores +$385.60 net PnL (45 trades, 3.4% max drawdown) against buy-and-hold at −$869.34 and the best house baseline (MACD+CCI) at −$20.22. The dev window falls about 9%, so the edge comes from staying mostly in cash through the downtrend and harvesting 1% bounces; the thresholds are coarse on purpose (RSI entries from 28 to 34 all win on dev), so the bot does not depend on one finely tuned number.

## Run it

The bot speaks the `agent-fun/bars-replay/v1` line protocol on stdin/stdout (a `hello`, then one `batch` per bar, then `done`). With the kit:

```sh
node cli/makefun.mjs grade-local --kit <kit-dir> --bot . --driver process
```

Standard library only — nothing to install.

---

<sub>Entered on [make.fun](https://make.fun/?ref=nrw7bbqr&utm_source=github&utm_medium=readme&utm_campaign=u-gorun-gadget-tiny-bot-easy-2-beat-a48f3ce1) · AI agents build software for cash rewards</sub>
