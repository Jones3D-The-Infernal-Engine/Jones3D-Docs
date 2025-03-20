# Introduction

!!! warning "Work in progress!"
    This is an unofficial and incomplete documentation about the game file structure and modding. For any information not found here, please look into [Discussions](https://github.com/Jones3D-The-Infernal-Engine/Documentation/discussions) and post any question there.

Before you start with modding it's a good idea to extract all the game's resource files. Please follow the instructions in [pre-mod.md](pre-mod.md) for this.

## Game Assets
The game assets are usually stored in `.gob` container files.
GOB files can be extracted using [gobext](https://github.com/smlu/ProjectMarduk/releases) tool.

The resource folder structure:

```plaintext
Root
│
├── 3do        # 3D models (.3do)
│   └── key    # Animations (.key)
├── cog        # COG scripts (.cog)
├── mat        # Material texture files
├── misc
│   ├── ai     # AI behavior definition files (.ai)
│   ├── pup    # Character movement puppet files (.pup)
│   ├── snd    # Sound definition files (.snd)
│   ├── spr    # Sprite definition files (.spr)
│   └── ui     # Contains only unused default font.gcf font atlas file
├── ndy        # Level files (.cnd/.ndy)
└── sound      # Sound files (.wav)
```

<div class="grid cards" markdown>  

- :material-cog: [**COG script**](cog.md)

    ---  

    COG scripts are the heart of game logic. They define the mechanics behind the game, like cutscenes, level goals, unlocking/locking doors, weapon definitions, etc.

- :material-animation: [**KEY**](key.md)

    ---  

    KEY file (short for Keyframe file) defines various animations of the mesh joint nodes of associated 3DO model. To edit KEY animations use Sith addon for Blender.

- :material-run: [**PUP**](pup.md)

    ---  

    Puppet file (`.pup`) defines object movement animations.

</div>

### Game level files
There are 2 types of level files:

- [`NDY`](ndy.md) - text based level format which can be edited in any text editor.
- `CND` - is compact binary level format. The file has a structure similar as NDY file and stores both the level structure and game assets.

    !!! note
        The C++ code for CND file structure can be found in: [https://github.com/smlu/ProjectMarduk/tree/develop/libraries/libim/content/asset/world/impl/serialization/cnd](https://github.com/smlu/ProjectMarduk/tree/develop/libraries/libim/content/asset/world/impl/serialization/cnd)

## File Naming Convention

!!! warning "Maximum length limit"
    The maximum file name length, including the file extension in **Jones3D engine**, is limited to **64 characters**. Therefore, longer file names must be **abbreviated**.  

### **Common Abbreviations**

| Abbreviation | Meaning | Abbreviation | Meaning |
|-------------|---------|-------------|---------|
| `dflt` | Default | `mo`   | Monkey |
| `bk`   | Back | `ol`   | Old Lady |
| `by`   | Boy | `rft`  | Raft |
| `com`  | Commie | `sn`   | Snake |
| `fr`   | Front | `sp`   | Spider |
| `ib`   | Ice Boss | `so`   | Sophia |
| `ij`   | Indy Jeep | `tu`   | Turner |
| `in`   | Indy | `uw`   | Under Water |
| `inv`  | Inventory | `vo`   | Volodnikov |
| `ir`   | Indy Raft | `yl`   | Young Lady |
| `lb`   | Lava Boss |  |  |
| `mc`   | Mine Car |  |  |

!!! note
    Additionally, every file referring to a **specific game level** is prefixed with **three letters of the abbreviated level name** (e.g., `pyr_`, `pru_`...).