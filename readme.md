# Agent Miner

## Page 1 @showdialogue

### Activity Instructions

Code your agent to break blocks and collect the items dropped. You can use those items to craft the requirements for opening the exit door.

In Task 1 you will acquire the items to make gold nuggets.
In Task 2 you will acquire the items to make iron nuggents.
In Task 3, if you look hard enough, you will find one diamond.

## Page 2

### Task 1: Breaking blocks in a line

Code your Agent to ``||agent.destroy forward||`` and ``||agent.collect all||`` to break and collect the ore. You can initiate your code using either a ``||player.chat command||`` or an ``||player.item||`` (such as a blaze rod). You need to right-click on the item to initiate the code. There are some items you can use in the supply chest.

```blocks
player.onItemInteracted(BLAZE_ROD, function () {
    agent.destroy(FORWARD)
    agent.collectAll()
})
```

```ghost
for (let index = 0; index < 4; index++)
agent.turn(LEFT_TURN)
player.onChat("run", function ())
```

## Page 3

### Task 1: Breaking blocks in a line

You can add an additional block to make your Agent ``||agent.move right||`` each time after it destroys and collects. You can also ``||loops.loop||`` your code so you don't need to initiate it as often.

```blocks
player.onItemInteracted(BLAZE_ROD, function () {
    agent.destroy(FORWARD)
    agent.collectAll()
    agent.move(RIGHT, 1)
})
```

## Page 4

### Task 2: Breaking blocks in two-dimensions

For Task 2, code your Agent to ``||agent.move forward||`` after each line. There are different ways you can approach this problem, but ``||loops.loops||`` will always make things easier.

```blocks
player.onItemInteracted(BLAZE_ROD, function () {
    for (let index = 0; index < 10; index++) {
        agent.destroy(FORWARD)
        agent.collectAll()
        agent.move(RIGHT, 1)
    }
    agent.move(FORWARD, 1)
})
```

## Page 5

### Task 2: Breaking blocks in two-dimensions

Notice your Agent finishes the first line on the right-hand side of the workspace. One way to approach this problem is coding the Agent to ``||agent.move left||`` for the second line.

```blocks
player.onItemInteracted(BLAZE_ROD, function () {
    for (let index = 0; index < 10; index++) {
        agent.destroy(FORWARD)
        agent.collectAll()
        agent.move(RIGHT, 1)
    }
    agent.move(FORWARD, 1)
    for (let index = 0; index < 10; index++) {
        agent.destroy(FORWARD)
        agent.collectAll()
        agent.move(RIGHT, 1)
    }
    agent.move(FORWARD, 1)
})
```

## Page 6

### Task 2: Breaking blocks in two-dimensions

To reduce the amount of times you need to initiate the code, you can wrap all the code in another ``||loops.loop||`` to create a nested loop. Doing this will make life much easier when you get to Task 3.

```blocks
player.onItemInteracted(BLAZE_ROD, function () {
    for (let index = 0; index < 5; index++) {
        for (let index = 0; index < 10; index++) {
            agent.destroy(FORWARD)
            agent.collectAll()
            agent.move(RIGHT, 1)
        }
        agent.move(FORWARD, 1)
        for (let index = 0; index < 10; index++) {
            agent.destroy(FORWARD)
            agent.collectAll()
            agent.move(RIGHT, 1)
        }
        agent.move(FORWARD, 1)
    }
})
```

## Page 7

### Task 3: Breaking blocks in three-dimensions

For Task 3, you need to code your Agent to ``||agent.move up||`` at some point in your code. Again, there are different ways to approach this problem. Some methods may need the ``||agent.destory up||`` block.

```blocks
player.onItemInteracted(BLAZE_ROD, function () {
    for (let index = 0; index < 5; index++) {
        for (let index = 0; index < 10; index++) {
            agent.destroy(FORWARD)
            agent.collectAll()
            agent.move(RIGHT, 1)
        }
        agent.move(FORWARD, 1)
        for (let index = 0; index < 10; index++) {
            agent.destroy(FORWARD)
            agent.collectAll()
            agent.move(RIGHT, 1)
        }
        agent.move(FORWARD, 1)
    }
    agent.destroy(UP)
    agent.move(UP, 1)
})
```

## Page 8

### Task 3: Breaking blocks in three-dimensions

One way to approach this problem is to destroy each layer from front to back (shown in hint). You could also destroy each layer from bottom to top. No matter how you approach it, ``||loops.nested loops||`` will mean you have to initiate your code less often.

```blocks
player.onItemInteracted(BLAZE_ROD, function () {
    for (let index = 0; index < 2; index++) {
        for (let index = 0; index < 10; index++) {
            agent.destroy(FORWARD)
            agent.collectAll()
            agent.move(RIGHT, 1)
        }
        agent.move(UP, 1)
        for (let index = 0; index < 10; index++) {
            agent.destroy(FORWARD)
            agent.collectAll()
            agent.move(RIGHT, 1)
        }
        agent.move(UP, 1)
    }
})
```

## Page 9

### Task 3: Breaking blocks in three-dimensions

It is possible to code you Agent to complete this task in one go. You'll need to use a ``||loops.nested loop||`` inside a ``||loops.nested loop||``.

```blocks
player.onItemInteracted(BLAZE_ROD, function () {
    for (let index = 0; index < 9; index++) {
        for (let index = 0; index < 2; index++) {
            for (let index = 0; index < 10; index++) {
                agent.destroy(FORWARD)
                agent.collectAll()
                agent.move(RIGHT, 1)
            }
            agent.move(UP, 1)
            for (let index = 0; index < 10; index++) {
                agent.destroy(FORWARD)
                agent.collectAll()
                agent.move(RIGHT, 1)
            }
            agent.move(UP, 1)
        }
        agent.move(DOWN, 4)
        agent.move(FORWARD, 1)
    }
})
```

## Page 10

### Craft the items to exit

You should now have all the items you need to exit.

You'll need to smelt the ore into metal, and then use the crafting table to make nuggets.

Once you have all the required materials, open the exit door and go try the challenge level.

## Page 11

### Challenge level

In this super pit, you need to mine and collect five diamonds in order to exit into the free world.

Be careful, if you collect too many extra items you can full up your Agent's inventory. Either trade with your Agent to get rid of some items, or you can code using ``||logic.conditional statements||`` to prevent the Agent from collecting everything.

```blocks
player.onItemInteracted(BLAZE_ROD, function () {
    if (agent.inspect(AgentInspection.Block, FORWARD) == DIAMOND_ORE) {
        agent.destroy(FORWARD)
        agent.collectAll()
        agent.move(RIGHT, 1)
    } else {
        agent.destroy(FORWARD)
        agent.move(RIGHT, 1)
    }
})
```

