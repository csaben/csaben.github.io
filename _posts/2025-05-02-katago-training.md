---
title: 'katago training'
date: 2025-02-05
permalink: /posts/2025/02/katago-training/
tags:
  - devlog
---

Putting this here for people trying to do this quickly in the future. 

There probably exists a better way to do this but I spent a few hours hacking around with the repo and sifting through the discord before just doing this:

___

How to train with selfplay:

- compile the cpp following the readme instructions

- run this command from inside the `python/selfplay` directory

```bash
# sample args
./synchronous_loop.sh andark pretrained andark-v1 'b10c128' 1      
```

>model configs to select from:
[Katago model configs](https://github.com/rsdmse/KataGo/blob/master/python/modelconfigs.py)

___

If starting from scratch but you want to use a ckpt from the [website](https://katagotraining.org/networks/) follow these instructions:

1. run the synchronus loop shell file until it saves a model to `modelstobetested`
then insert your model in that directory as a folder with whatever model name you want containing these two files:
    - .ckpt
    - .bin.gz

2. move the generated `modeltobetested` out of that directory so only your model you want to keep training from is there.

_voila_, 
next time you run `synchronous_loop.sh` it will initialize your provided model and do selfplay with it and train from there
