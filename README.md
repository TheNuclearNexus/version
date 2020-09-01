# Versions
## What is **Versions**
**Versions** is a library for version control in minecraft datapacks!

## How do I setup Versions?
Simply copy the contents of ``version/data`` into your datapack! *It may be required to merge the contents of ``version/data/minecraft`` depending on your project*

After you've done that, add your function to ``#version:load``

Then, set your version numbers inside your load function! *CMD is a 3 digit number registered [here](https://mc-datapacks.web.app/custom_model_id). This is optional but helps to insure compatibility*

### Vanilla
```mcfunction
scoreboard players set <CMD>.<name> major 1
scoreboard players set <CMD>.<name> minor 2
scoreboard players set <CMD>.<name> patch 0
```
### Trident
```mcfunction
set <CMD>.<name>->major = 1
set <CMD>.<name>->minor = 2
set <CMD>.<name>->patch = 0
```

Finally, add your ticking functions to ``#version:tick`` rather than ``#minecraft:tick``, this is so you can disable your ticking functions if you don't locate the proper datapack/version. (More in the following section)

## How do I use Versions properly?
If you followed the previous section, then you should have a version number setup! Checking for a datapack existing or it's version is fairly easy!

###Vanilla
```mcfunction
execute if score <CMD>.<name> major matches 1 if score <CMD>.<name> minor matches 2 if score <CMD>.<name> patch matches 0 run say Found <name>!
```
###Trident
```mcfunction
if score <CMD>.<name> major matches 1 
if score <CMD>.<name> minor matches 2 
if score <CMD>.<name> patch matches 0 say Found <name>!
```

## Quick Start / Helpful Code

###Example version tellraw
```mcfunction
tellraw @a ["'Name' v",{"score":{"name":"CMD.name","objective":"major"}},".",{"score":{"name":"CMD.name","objective":"minor"}},".",{"score":{"name":"CMD.name","objective":"patch"}}, " Loaded"]
```