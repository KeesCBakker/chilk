# Chalk with Markers -- for the 💖 of 💄 ASCII art 🤙

I. Love. ASCII. Art. Seriously I can't make a NodeJS CLI or Chatbot without adding a decent splash-screen to it. That's why I love <a href="https://www.npmjs.com/package/chalk">Chalk</a>. But creating those strings got a little too verbose, that's why I created this lib.

**Note: we've upgraded to ESM, as Chalk is also in ESM.**

```js
import { asciiArtChalker } from "chalk-with-markers";

console.log(asciiArtChalker.colorize(`

b   ______g__  __y____o__    r__ __
b  / ____/g / / /y  _/o /   r/ //_/
b / /   g/ /_/ /y/ /o/ /   r/ ,<   
b/ /___g/ __  /y/ /o/ /___r/ /| |  
b\\____/g_/ /_/y___/o_____/r_/ |_|  

`));
```

<img src="resources/ChilkSplash.png" width="600" />

Note: I use the <a href="https://patorjk.com/software/taag/#p=display&f=Graffiti&t=CHILK">TAAG by patorjk</a> to generate the art.

This lib should just:
- be light weight & extendable
- provide readable, non-verbose markers


## Text highlight
If you want to highlight text, we use the default `chalker` like this:

```js
import { chalker } from "chalk-with-markers";

console.log("Results:");
console.log(chalker.colorize("- Checked status for [y]KeesTalksTech[/], website is [g]online[/]."));
console.log(chalker.colorize("- Checked status for [y]Recipes[/], website is [r]offline[/]."));
```

It produces:

<img src="resources/ChilkText.png" width="600" />

## Default color markings
We have the following:

| color                                                        | HTML name    | HEX      | `chalker` marker | `asciiArtChalker` marker | notes |
| ------------------------------------------------------------ | ------------ | -------- | ---------------- | ------------------------ | ----- |
| ![#FF0000](https://via.placeholder.com/50x25/FF0000/?text=+) | red          | `FF0000` | `[r]`            | `r`                      |       |
| ![#00FF00](https://via.placeholder.com/50x25/00FF00/?text=+) | lime         | `00FF00` | `[g]`            | `g`                      |       |
| ![#0080FF](https://via.placeholder.com/50x25/0080FF/?text=+) | light blue   | `0080FF` | `[b]`            | `b`                      |       |
| ![#FFFF00](https://via.placeholder.com/50x25/FFFF00/?text=+) | yellow       | `FFFF00` | `[y]`            | `y`                      |       |
| ![#FF00FF](https://via.placeholder.com/50x25/FF00FF/?text=+) | magenta      | `FF00FF` | `[m]`            | `m`                      |       |
| ![#00FFFF](https://via.placeholder.com/50x25/00FFFF/?text=+) | cyan         | `00FFFF` | `[c]`            | `c`                      |       |
| ![#FFA500](https://via.placeholder.com/50x25/FFA500/?text=+) | orange       | `FFA500` | `[o]`            | `o`                      |       |
| ![#FFFFFF](https://via.placeholder.com/50x25/B266FF/?text=+) | light violet | `FFFFFF` | `[p]`            | `p`                      |       |
| ![#FFFFFF](https://via.placeholder.com/50x25/FFFFFF/?text=+) | white        | `FFFFFF` | `[w]`            | `w`                      |       |
| ![#000000](https://via.placeholder.com/50x25/000000/?text=+) | black        | `000000` | `[k]`            | `k`                      |       |
|                                                              |              |          | `[q]` or `[/]`   | `q`                      | resets chalk |

## Own mappings
Can I make my own markers? Yes, you can!

```js
import { Chalker } from "chalk-with-markers";
import chalk from "chalk";

const x = new Chalker();
x.set("[r]", chalk.bgRed.black);
x.set("[w]", chalk.bgWhite.black);
x.set("[b]", chalk.bgBlue.black);
x.set("[/]", chalk.reset);

console.log(x.colorize(`
[r] X X X X 
[w]  X X X  
[b] X X X X 
[/]         `));

```

It produces:

<img src="resources/ChilkDutchFlag.png" width="600" />

## Extend
Can I extend the mappings? Yes you can!

```js
import { asciiArtChalker } from "chalk-with-markers";
import chalk from "chalk";

// global extend:
asciiArtChalker.set("p", chalk.hex("#FFC0CB")); // add HTML pink

// or clone to use extend locally:
const x = asciiArtChalker.clone();
x.set("p", chalk.hex("#FFC0CB")); // add HTML pink


```
