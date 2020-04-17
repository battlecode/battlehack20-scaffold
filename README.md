# battlehack20-scaffold

Read more about Battlehack 2020 at https://bh2020.battlecode.org!

## Installation
To install the engine as a local package, open your [terminal](https://askubuntu.com/questions/38162/what-is-a-terminal-and-how-do-i-open-and-use-it) and run
```
pip install --user --upgrade battlehack20
```

(Depending on how your pip is set up, you may need to replace `pip` with `pip3`.) 

## Running

Run a game! Use:

```
python3 run.py examplefuncsplayer examplefuncsplayer
```

You should see a game between `examplefuncsplayer` and `examplefuncsplayer` being played.

**If you're on Windows and you get incomprehensible output, try instead:**

```
python3 run.py examplefuncsplayer examplefuncsplayer --raw-text
```

If your code is in a directory `~/yourcode/coolplayer` then you can run it against examplefuncsplayer using

```
python3 run.py examplefuncsplayer ~/yourcode/coolplayer
```

## Running Interactively

Run

```
python3 -i run.py examplefuncsplayer examplefuncsplayer
```

This will open an interactive Python shell. There, you can run

```
step()
```

which advances the game 1 turn. This is very useful for debugging.

## More options

Run

```
python3 run.py -h
```

to list all possible options for running.

For example, turning off debug mode, which is on by default, can be helpful:

```
python3 run.py examplefuncsplayer --debug false
```

## Advanced usage

Interacting directly with the `battlehack20` API will give you more freedom and might make it easier to debug your code. The following is a minimal example of how to do that.

```
$ python3
>>> import battlehack20
>>> code = battlehack20.CodeContainer.from_directory('./examplefuncsplayer')
>>> game = battlehack20.Game([code, code], debug=True)
>>> game.turn()
```

You should see the output:
```
[Game info] Turn 1
[Game info] Queue: {}
[Game info] Lords: [<ROBOT WHITE HQ WHITE>, <ROBOT BLACK HQ BLACK>]
[Robot WHITE HQ log] Starting Turn!
[Robot WHITE HQ log] Team: Team.WHITE
[Robot WHITE HQ log] Type: RobotType.OVERLORD
[Robot WHITE HQ log] Spawned unit at: (0, 11)
[Robot WHITE HQ log] Done! Bytecode left: 19928
[Robot BLACK HQ log] Starting Turn!
[Robot BLACK HQ log] Team: Team.BLACK
[Robot BLACK HQ log] Type: RobotType.OVERLORD
[Robot BLACK HQ log] Spawned unit at: (15, 5)
[Robot BLACK HQ log] Done! Bytecode left: 19927
```

If you're curious, this is how the `run.py` script works. Study the source code of `run.py` to figure out how to set up a viewer.
