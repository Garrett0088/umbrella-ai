# ☂️ Umbrella AI

**Should I bring an umbrella today?** Pick four things and get the call instantly.

**Live demo:** https://garrett0088.github.io/umbrella-ai/

> A class project for Professor Ping Wu's AI class at CSTU. The assignment, *Build Your FDE Toolbox*, asks students to write a prompt that makes Claude generate a skill, one that names the real problem before designing a fix. Umbrella AI turns that skill's decision logic into a live, one-page tool.

## How it works

Choose:

1. **Weather forecast:** Sunny, Cloudy, Light shower, Pouring
2. **Time to work:** 5 minutes up to 4 hours
3. **Look out your door:** Clear, Cloudy, Dark clouds, Raining
4. **Mood today:** Got wet recently, Neutral / trust AI, Feeling lucky, Hate carrying stuff

The answer slides between **No umbrella**, **Take a chance**, **Hoodie**, and **Must bring**, with a one-line reason. Rain falls in the background, bigger and faster as the odds of getting wet go up.

## AI mode vs. Dev mode

- **AI mode** (default) shows just the answer.
- **Dev mode** shows the points on every button, the live formula, and a heatmap of all 448 combinations.

Both modes run the exact same math.

## The scoring model

Every choice has a point value. Add them up.

| Input | Points |
|---|---|
| Forecast | Sunny −2, Cloudy +2, Light shower +5, Pouring +7 |
| Time to work | 5m 0, 10m +2, 15m +3, 30m +5, 1h +6, 2h +7, 4h +8 |
| Door view | Clear 0, Cloudy +1, Dark clouds +2, Raining +5 |
| Mood | Got wet recently +2, Neutral 0, Feeling lucky −4, Hate carrying −1 |

| Total | Call |
|---|---|
| 3 or less | No umbrella |
| 4 to 6 | Take a chance |
| 7 to 9 | Hoodie |
| 10 or more | Must bring |

The weights are tuned so real human behavior comes out of plain addition. Pouring rain, a 10-minute trip, and a lucky mood says *Take a chance*. Same trip but you hate carrying stuff? *Hoodie.*

## Run it

It's one HTML file with no install and no build step. Open `index.html` in any browser, or visit the live demo.

## Coming in v2

- **Live forecast:** pull the chance of rain from a weather API and pre-select the forecast button (you can still override it).
- **Your location:** use the browser's location, with permission, so the forecast matches where you are.
- **Commute timing:** check the rain chance for both the morning trip and the trip home.
- **Remember my defaults:** keep your usual commute time between visits.
- **Tune the weights:** adjust the point values in Dev mode and watch the heatmap update.

## Built with

Plain HTML, CSS, and JavaScript. Designed and iterated with Claude.

## Author

Garrett Liang

## License

MIT, see [LICENSE](LICENSE).
