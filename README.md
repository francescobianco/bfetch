<div align="center">
<pre style="background: none !important; font-weight: bold !important;">
    ____                   
   / __ )___    __      __ 
  / __  / _/__ / /_____/ / 
 / /_/ / _/ -_) __/ __/ _ \
/_____/_/ \__/\__/\__/_//_/

</pre>
</div>

<p align="center">Dynamic fetching tool that <i>SuperB</i></p>
<p align="center"><img src="https://img.shields.io/github/license/NNBnh/bfetch?labelColor=181818&color=DC9656&style=for-the-badge" alt="License: GPL-3.0"> <img src="https://img.shields.io/github/languages/top/NNBnh/bfetch?logo=gnu-bash&labelColor=181818&color=DC9656&logoColor=FFFFFF&style=for-the-badge" alt="Shell: 100%"> <img src="https://img.shields.io/github/last-commit/NNBnh/bfetch?labelColor=181818&color=DC9656&style=for-the-badge"></p>
<p align="center"><img src="https://img.shields.io/github/watchers/NNBnh/bfetch?labelColor=181818&color=DC9656&style=flat-square"> <img src="https://img.shields.io/github/stars/NNBnh/bfetch?labelColor=181818&color=DC9656&style=flat-square"> <img src="https://img.shields.io/github/forks/NNBnh/bfetch?labelColor=181818&color=DC9656&style=flat-square"> <img src="https://img.shields.io/github/issues/NNBnh/bfetch?labelColor=181818&color=DC9656&style=flat-square"></p>

## About
**Bfetch** is a *SuperB* general-purpose fetching tool written in [`pure sh`](https://github.com/dylanaraps/pure-sh-bible) that take user commands output and change how it display dynamic with the terminal size.

<a href="https://asciinema.org/a/379071" target="_blank"><img width="49%" src="https://asciinema.org/a/379071.svg"></a>
<a href="https://asciinema.org/a/379073" target="_blank"><img width="49%" src="https://asciinema.org/a/379073.svg"></a>

<p align="center"><a href="https://asciinema.org/a/379084" target="_blank"><img src="https://asciinema.org/a/379084.svg"></a></p>

### Story
As a Linux ricer, I kile to make [**Neofetch**](https://github.com/dylanaraps/neofetch) automatically run when the terminal start.
This was fine until I switched to using the tiled window manager, the terminal is often too small leading the fetch to look messy, even with [**Pfetch**](https://github.com/dylanaraps/pfetch), the poblem could appear.
This has led me to create **Bfetch**, a dynamic fetching tool with an customization spirit from [**Ufetch**](https://gitlab.com/jschx/ufetch).

|Other fetch|Bfetch|
|-|-|
|![Story other fetch](image/story/other.png)|![Story Bfetch](image/story/bfetch.png)|

### Features
- Super **minimum** with exactly than [**256** lines of `sh`](bfetch#L256) and [**no dependencies**](#dependencies) (if you don't count `sh`).
- Super **flexible**:
  - **Align/shift/change mode** contents based on terminal size.
  - **Hide** some elements if terminal is too small.
- Super **Customizable**:
  - Bfetch can **take commands output** and use it. By so, Bfetch can display **anything** you want, **however** you want.
  - And even more [**config options**](#configuration)
- Have **two mode**:

|Paper mode|Classic mode|
|-|-|
|![Paper mode](image/paper-mode.png)|![Classic mode](image/classic-mode.png)|
|This mode aims to look like a paper document title.|This layout emulate the look of other system information tool.|

## Contents
- [About](#about)
  - [Story](#story)
  - [Features](#features)
- [Contents](#contents)
- [Setup](#setup)
  - [Dependencies](#dependencies)
  - [Installation](#installation)
- [Usage](#usage)
- [Configuration](#configuration)
  - [Info element](#info-element)
  - [Art element and color element](#art-element-and-color-element)
- [Credit](#credit)

## Setup
### Dependencies
- `sh` to process

### Installation
#### Manually
- Option 1: using `curl`

```sh
curl https://raw.githubusercontent.com/NNBnh/bfetch/main/bfetch > ~/.local/bin/bfetch
chmod +x ~/.local/bin/bfetch
```

- Option 2: using `git`

```sh
git clone https://github.com/NNBnh/bfetch.git ~/.local/share/bfetch
ln -s ~/.local/share/bfetch/bfetch ~/.local/bin/bfetch
```

#### Package manager
`#TODO`

## Usage
Run Bfetch in the terminal:

```sh
bfetch
```

## Configuration
Bfetch is configured through environment variables: `export BFETCH_<SETTING>="<value>"`

|Value|Invalid|Default|Description|
|-|-|-|-|
|`BFETCH_INFO`|`<commands>`|`$XDG_CONFIG_HOME/bfetch/info` (`~/.config/bfetch/info`)|Read this commands output as infomation element (OS, WM, terminal, ...)|
|`BFETCH_ART`|`<commands>`|`$XDG_CONFIG_HOME/bfetch/art` (`~/.config/bfetch/art`)|Read this commands output as art element (operating system logo)|
|`BFETCH_COLOR`|`<commands>`|`$XDG_CONFIG_HOME/bfetch/color` (`~/.config/bfetch/color`)|Read this commands output as color element (colors strip below info)|
|||||
|`BFETCH_TEMPORARY`|`<path/to/file>`|`$XDG_CACHE_HOME/bfetch` (`~/.cache/bfetch`)|Temporary file's location|
|||||
|`BFETCH_CLASSIC_MODE`|`true\|false`|`false`|Make Bfetch prefer classic mode when both mode are possible|
|`BFETCH_ART_RIGHT`|`true\|false`|`false`|Render art on the right when using classic mode|
|`BFETCH_PADDING`|`0+`|`1`|Padding fetch when using classic mode|
|`BFETCH_SEPARATOR`|`0+`|`2`|Separate info and art when using classic mode|
|`BFETCH_PROMPT_HEIGHT`|`0+`|`1`|Acknowledge how high the shell prompt is and counter it so the prompt don't push the fetch out|

Bfetch will export the maximum size that an element can get:

|Value|Description|
|-|-|
|`BFETCH_INFO_HEIGHT`|Maximum height of infomation element|
|`BFETCH_INFO_WIDTH`|Maximum width of infomation element|
|`BFETCH_ART_HEIGHT`|Maximum height of art element|
|`BFETCH_ART_WIDTH`|Maximum width of art element|
|`BFETCH_COLOR_HEIGHT`|Maximum height of color element|
|`BFETCH_COLOR_WIDTH`|Maximum width of color element|

###### [Here is an example of a color element that can be resized based on it's maximum size](https://github.com/NNBnh/dots/blob/master/home/.config/bfetch/color)

### Info element
Bfetch looking for and execute `$XDG_CONFIG_HOME/bfetch/info` for info element as default, you can copy [this info template](https://github.com/NNBnh/textart-collections/blob/main/fetch/info.textart) with [Fetchutils](https://github.com/lptstr/fetchutils) as a starting point and customizing.

###### [Learn about `.textart` here](https://github.com/NNBnh/textart-collections/wiki)

### Art element and color element
For art element and color element, take a look at [NNB's textart collections](https://github.com/NNBnh/textart-collections) and [other textart resources](https://github.com/NNBnh/textart-collections#resources).

## Credit
Special thanks to:
- [**Neofetch**](https://github.com/dylanaraps/neofetch) by [Dylan](https://github.com/dylanaraps)
- [**Pfetch**](https://github.com/dylanaraps/pfetch) also by [Dylan](https://github.com/dylanaraps)
- [**Ufetch**](https://gitlab.com/jschx/ufetch) by [Jschx](https://gitlab.com/jschx)
- [**Fetchutils**](https://github.com/lptstr/fetchutils) by [LPTSTR](https://github.com/lptstr)
- [**Pure sh bible**](https://github.com/dylanaraps/pure-sh-bible) also by [Dylan](https://github.com/dylanaraps)

###### This project did not take it's name from [**ZeroL00P's Bfetch**](https://github.com/Mati232411/bfetch) or [**Edoardo Zerbo's Bfetch**](https://gitlab.com/nautilor/bfetch). The "B" in Bfetch stands for "*SuperB*" like all my other project names: [Bawkpack](https://github.com/NNBnh/bawkpack), [BUI](https://github.com/NNBnh/bui.kak) ...
