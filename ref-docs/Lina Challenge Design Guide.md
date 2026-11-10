# Lina Challenge Design Guide

Oct 21, 2026 · @Adam

A Lina challenge works when a 7 and a 9 year old can say what to do in one sentence, get a laugh within a minute, and earn a visible reward. This guide sets the rules, the expert frameworks behind them, and about 60 challenges across the house.

## The formula

Every challenge is one **Verb** on one **Thing** in one **Place**, with a **Twist** that surprises, a **Reaction** the kids can see and hear at once, and a **Reward** they can keep.

```latex
Challenge = Verb + Thing + Place + Twist + Reaction + Reward
```

Seven rules fall out of the research below. They are design heuristics built from the frameworks, not measured results for Oscar and his sister.

1. **One-sentence goal.** If it needs two sentences, split it into two challenges. Text stays short and big (the kids asked for bigger text).
2. **Laugh in 60 seconds.** The first attempt should produce a funny reaction (crash, squeak, Uncle Adam face) even if it fails.
3. **No failing, only retrying.** Nothing is lost, nothing is timed against the kid, and a retry costs under 5 seconds.
4. **Choice inside the goal.** Give two or more ways to do it (roll, throw, climb) so the kids feel clever, not guided.
5. **A nudge, not a lecture.** After about 90 seconds stuck, a glowing arrow or a sparkle points at the next step.
6. **Mix the board.** Of the three open missions, one is easy, one medium, one a stretch.
7. **Share the win.** Big wins get a toast, a sound and a change in the world (Uncle Adam dances, the oven glows) so a sibling watching feels it too.

## The expert team

Ten specialists sit at the table. Each brings one framework and changes something concrete in the game. Frameworks marked "background" are from general knowledge and were not re-checked this session; the others have a linked source.

| Expert | Framework | What it says | What it changes in Lina |
| --- | --- | --- | --- |
| Game designer | [MDA: Mechanics, Dynamics, Aesthetics](https://users.cs.northwestern.edu/%7Ehunicke/MDA.pdf) (Hunicke, LeBlanc, Zubek) | Design the rules to produce a target feeling. Their eight feelings: Sensation, Fantasy, Narrative, Challenge, Fellowship, Discovery, Expression, Submission | Pick the feeling first. Lina targets Sensation (crashes, sounds), Fantasy (tiny tortoise, big house), Discovery (secrets), Expression (skins, patterns), Fellowship (two kids, Uncle Adam) |
| Mission designer | Flow channel (Csikszentmihalyi; see [overview](https://mediadesign.de/de/news/2017/flow-and-flow-control-how-design-games-player-growth-replay-value-and-great-gaming)) | Too hard gives anxiety, too easy gives boredom, a match gives flow | Three tiers per board, a hint after 90 seconds, no automatic difficulty changes (sources are mixed on whether they work) |
| Motivation psychologist | [Self-determination theory](https://www.rochester.edu/warner/lida/wp-content/uploads/2022/11/02bfe513dd59366750000000.pdf) (Ryan, Rigby, Przybylski 2006) | Autonomy, competence and relatedness each predict enjoyment and wanting to play again | Autonomy: several ways to finish. Competence: visible progress and quick wins. Relatedness: Uncle Adam reacts, two kids can share the iPad |
| Child development specialist | Piaget's concrete operational stage and Vygotsky's zone of proximal development (background) | Ages 7 to 11 reason well about real objects and clear rules; learning stretches with a small nudge | Challenges use physical things (push, stack, throw), clear rules, and hints as scaffolding. Abstract puzzles (codes, maps) come later and stay optional |
| Behavioural scientist | Fogg Behavior Model and the goal-gradient effect (background) | Action needs motivation, ability and a prompt together; people speed up as a goal gets close | Always show the next prompt on screen, keep the first step easy, show progress as 3/8 with icons |
| Comedy writer | Incongruity, slapstick, rule of three, callbacks (background) | Surprise plus harmlessness is funny; a pattern of three then a break is funnier | Uncle Adam is the foil: calm, then bonked, then red and chasing. Each room gets one running gag that returns later |
| Communication designer | Plain-language UX writing (background) | One instruction at a time, verbs first, icon plus word | Mission names are 2 to 4 words, descriptions one sentence, same button names everywhere (JUMP, GRAB, SHELL) |
| Player-type analyst | [Bartle's types and Yee's motivations](https://nickyee.com/facets/bartle.html) | Players differ: achievers, explorers, socialisers, troublemakers. Built from adult online-game players | Offer all four: counters (achiever), secrets (explorer), Uncle Adam and co-play (socialiser), chaos (troublemaker). Treat as a checklist, not a diagnosis of the kids |
| Safety and ethics reviewer | [Dark patterns in kids' games](https://papers.academic-conferences.org/index.php/ecgbl/article/view/1656) (research on ages 0 to 5 and 10 to 15) | Timers, paywalls, gambling-like rewards and guilt messages are common and harmful | The guardrails in the next sections |
| Economy designer | Faucet and sink balance (background) | Rewards flowing in need worthwhile things to spend on | Challenge rewards scale with effort; shop prices (20 to 80) take 3 to 10 challenges |

## Tiers, rewards and the board

Four tiers set how long a challenge takes and what it pays. Times are targets to check in playtests, not measured values.

| Tier | Target time | Skill asked | Reward (coins) | Example |
| --- | --- | --- | --- | --- |
| Easy | 20 to 60 seconds | One action, hard to fail | 3 to 4 | Bump the radio |
| Medium | 1 to 3 minutes | One skill with a twist (jump, throw, roll) | 5 to 8 | Break 5 vases |
| Hard | 3 to 6 minutes | Several steps or some planning | 10 to 15 | Oscar's Pizza |
| Epic | 10 minutes or more, in parts | A chain of challenges | 25 plus a special skin or pattern | A full quest line |

**Board rule.** Three missions are open. Slot 1 is always Easy, slot 2 Medium, slot 3 Hard (or Epic when a chain is running). Finishing a slot opens the next unfinished mission of the same tier, so the mix never drifts to three hard ones. The game currently opens missions in list order; switching to tier slots is the first build task.

**Reward rule.** Pay at the moment of the win with a sound, a toast and a visible change in the world, then add coins. Rewards are fixed and known ("+8"), never random.

**Feedback rule.** Every action answers within a fifth of a second: a sound, a movement or a toast. Progress counters show as 3/8 with the item icon.

**Hint rule.** After 90 seconds with no progress on a mission, a sparkle or arrow points to the next object. The kids can turn hints off in a later settings screen.

**Co-play rule.** Where it fits, a challenge has a version for two: one steers, one throws; or one hides in the box while the other sets off Uncle Adam.

## Guardrails

Research on kids' games finds timers, paywalls, gambling-like rewards and guilt messages are common (see [early childhood study](https://papers.academic-conferences.org/index.php/ecgbl/article/view/1656) and [a study of games popular with ages 10 to 15](https://uni.oslomet.no/belong/2023/11/21/from-digital-playground-to-dark-patterns/)). Lina avoids all of them.

- **No pressure.** No countdowns that punish, no streaks to lose, no "come back tomorrow". The only timer is the optional bug hunt, and it only pays out.
- **No gambling.** Rewards are fixed. No loot boxes, mystery prizes or spin wheels.
- **No money, no ads, no accounts.** Coins are earned in play and saved on the device.
- **No guilt.** Quitting mid-mission shows nothing sad. Progress stays.
- **Kind chaos.** Slapstick only: Uncle Adam is bonked, dizzy, then cross, never hurt. No blood, no "dead".
- **Easy to stop.** Missions are 1 to 6 minutes, and a natural pause point appears after each win.
- **Private by default.** No analytics, no photos or location, and nothing that ties the game to the kids' real address (the site is public).

## The challenge suite

About 60 challenges across eight zones: 17 are built today, the rest are new. The living room, kitchen, rafters and garden exist in the game. The bedroom, bathroom, games room and entry are **placeholder zones**: their rooms depend on the layout choice still open with Adam (house-inspired or exact). Rewards for built missions will be rebalanced to the tier table.

### Living room

| Challenge | What Lina does | Twist | Tier | Coins | Status |
| --- | --- | --- | --- | --- | --- |
| Disco Lina | Bump the red radio | Uncle Adam dances | Easy | 3 | Built |
| Curiosity | Jump up the wooden steps to the rafters | First use of JUMP | Easy | 4 | Built |
| Hide in the Box | Sit in the cardboard box for 3 seconds | Uncle Adam cannot catch you inside | Easy | 4 | Built |
| Crate Crash | Roll the shell into the crate pyramid | Crates fall like dominoes, Uncle Adam jumps | Easy | 3 | New |
| Lamp Out | Knock over both lamps | Room goes dim, Uncle Adam says "Who turned off the lights?" | Easy | 3 | New |
| Pick and Throw | GRAB 3 things and THROW them | Throws can hit Uncle Adam | Easy | 4 | Built |
| Vase Smasher | Break 5 vases | Breaks pay coins | Medium | 7 | Built |
| Uncle Adam Bonker | Bonk Uncle Adam 3 times with the shell | He turns red and chases | Medium | 8 | Built |
| Domino Library | Knock over 8 books | Push the first one | Medium | 7 | Built |
| Timber! | Topple both side tables | Tables can be pushed over | Medium | 6 | Built |
| Balloon Pop | Pop 8 balloons | Some are very high | Medium | 7 | Built |
| Art Lover | Say hi to all 6 paintings | Frames light up when visited | Medium | 6 | Built |
| Bug Hunter | Catch 5 bugs in 30 seconds | Starts on the orange pad | Medium | 8 | Built |
| Bowling Night | Roll one ball into the crate tower | A scoreboard pops up and the crowd cheers | Medium | 6 | New |
| Goal! | Throw a ball into the box 3 times | The box cheers | Medium | 6 | New |
| Sneak Past | Cross the room while Uncle Adam faces away | He turns around now and then; getting spotted just restarts the walk | Medium | 6 | New |
| From Above | Push something off the rafters onto Uncle Adam | Slapstick landing | Hard | 10 | Built |

### Kitchen

| Challenge | What Lina does | Twist | Tier | Coins | Status |
| --- | --- | --- | --- | --- | --- |
| Fridge Light | Bump the fridge to open it | Light and cold mist, a lettuce inside | Easy | 3 | New |
| Crumb Trail | Follow a trail of 6 crumbs to the pantry | Discovery: a secret snack | Easy | 4 | New |
| King of the Fridge | Climb the steps and jump on top | Victory pose | Medium | 8 | Built |
| Kitchen Band | Hit 4 glowing pots in the order they light up | Plays a tune | Medium | 6 | New |
| Noodle Slip | Tip the pasta pot behind Uncle Adam's path | He slips on noodles (our own gag instead of anything harmful) | Medium | 7 | New |
| Oscar's Pizza | Find 5 ingredients, bake in the brick oven | Squash, bacon, maple, onion jam, mozzarella | Hard | 15 | Built |
| Pizza Delivery | Carry the baked pizza to the dinner table | Jumping drops it; retry from the oven | Hard | 10 | New |

### Rafters

| Challenge | What Lina does | Twist | Tier | Coins | Status |
| --- | --- | --- | --- | --- | --- |
| Bird's Eye | Walk to the end of the rafters and switch to the From above view | Teaches the View button | Easy | 3 | New |
| Gold on the Beam | Find 3 gold coins up high | Sparkles hint | Medium | 6 | New |
| Airmail | Throw an item from the rafters into the box below | Box cheers | Medium | 7 | New |
| Rafter Bowling | Roll a ball off the rafters into the crate tower | Combo with Bowling Night | Hard | 10 | New |
| Tightrope | Walk a narrow beam to the far side | Wobble sound; a fall means a quick retry from the start | Hard | 10 | New |

### Garden

| Challenge | What Lina does | Twist | Tier | Coins | Status |
| --- | --- | --- | --- | --- | --- |
| Dino Friend | Say hi to the big T-rex | He roars back | Easy | 4 | Built |
| Dino Dance | Jump 3 times next to the T-rex | He stomps in time | Easy | 3 | New |
| Lettuce Feast | Eat 8 lettuces | They grow back | Medium | 8 | Built |
| Droid Bump | Bump the little droid 3 times | BEEP BOOP | Medium | 6 | Built |
| Dino Dig | Jump on 3 glowing patches in the soil to dig up bones | Bones go in a museum shelf later | Medium | 6 | New |
| Pond Hop | Hop across 4 lily pads | Jump skill; a splash means retry | Medium | 6 | New |
| Jedi Gates | Roll through 5 glowing gates in order | Star Wars training sounds | Medium | 7 | New |
| Droid Parade | Bump the droid all the way to the T-rex | The droid beeps happier each bump | Hard | 10 | New |

### Bedroom (placeholder zone)

| Challenge | What Lina does | Twist | Tier | Coins | Status |
| --- | --- | --- | --- | --- | --- |
| Night Light | Bump the star lamp on | Stars drift across the ceiling | Easy | 4 | New |
| Pillow Pop | Roll through the pillow pile | Feathers fly | Easy | 3 | New |
| Bed Bounce | Jump on the bed 5 times in a row | Trampoline feel, a springy sound | Medium | 6 | New |
| Toy Hunt | Find 3 hidden toys | Hide and seek: a sparkle when close | Medium | 6 | New |
| Dino Parade | Push 4 toy dinosaurs into a line | Each roars when placed | Medium | 7 | New |
| Teddy Rescue | Carry the teddy from the closet to the bed | Dropping it means pick up again | Hard | 10 | New |

### Bathroom (placeholder zone)

| Challenge | What Lina does | Twist | Tier | Coins | Status |
| --- | --- | --- | --- | --- | --- |
| Bubble Trouble | Bump the tap, then pop 8 bubbles | Bubbles float up like balloons | Easy | 4 | New |
| Towel Cape | GRAB the towel and wear it | Cosmetic: Super Lina | Easy | 3 | New |
| Duck Parade | Push 3 rubber ducks into the tub | Squeaks | Medium | 6 | New |
| Toothpaste Trail | Squeeze the toothpaste into a trail | Uncle Adam slips on it | Medium | 7 | New |

### Games room (placeholder zone, D&D and Star Wars flavour)

| Challenge | What Lina does | Twist | Tier | Coins | Status |
| --- | --- | --- | --- | --- | --- |
| Natural 20 | Push the giant d20 | It always lands on 20 with a fanfare (fixed, not random) | Easy | 4 | New |
| Switch Board | Flip 3 control switches in the order shown | Lights and space sounds | Medium | 7 | New |
| Dino Museum | Find 5 bone pieces around the house | Assembles a skeleton on the shelf | Medium | 7 | New |
| Dungeon Door | Find 3 rune stones to open the door | A picture riddle for each stone | Hard | 12 | New |
| Secret Plans | Carry the plans to the droid in the garden | Cross the whole house without Uncle Adam spotting you | Hard | 12 | New |

### Entry hall (placeholder zone)

| Challenge | What Lina does | Twist | Tier | Coins | Status |
| --- | --- | --- | --- | --- | --- |
| Shoe Shuffle | Knock all the shoes off the rack | Shoes bounce and pile up | Easy | 3 | New |
| Ding Dong | Ring the doorbell | Uncle Adam runs to answer; nobody is there | Easy | 4 | New |
| Hook Hop | Jump from the boxes up to 3 coat hooks | Jump precision | Medium | 7 | New |
| Ding Dong Heist | Ring the bell, then grab 3 things while Uncle Adam is at the door | Combo of two skills | Hard | 10 | New |

## Quest chains and whole-house challenges

Oscar plays D&D, so chains of 3 to 5 linked challenges with a story and a final prize fit him. Each chain is Epic tier and pays a skin or shell pattern that cannot be bought.

| Chain | Steps | Finale | Prize |
| --- | --- | --- | --- |
| Oscar's Feast | Oscar's Pizza, Pizza Delivery, Crumb Trail, Kitchen Band | A dinner table party where Uncle Adam hands out slices | Chef Lina hat |
| Dino Rescue | Dino Friend, Dino Dig, Dino Museum, Dino Parade | The T-rex and the museum skeleton roar together | Dino pattern |
| Rebel Tortoise | Jedi Gates, Switch Board, Secret Plans, Droid Parade | Droid and Lina deliver the plans | Jedi cape |
| The Dungeon | Natural 20, Dungeon Door, Gold on the Beam, Tightrope | Treasure chest opens in the games room | Dragon scale pattern |
| Prank Master | Noodle Slip, Toothpaste Trail, Ding Dong Heist, From Above | Uncle Adam gives a mock trophy | Gold crown |

**Whole-house challenges** span rooms and reward exploring:

- **House Tour** (Easy, 5): visit every zone once.
- **Collector** (Medium, 8): find 10 hidden gold stars across the house, each with a small sparkle.
- **Breakfast to Bedtime** (Hard, 12): do one challenge in each zone.
- **Best Friends** (Medium, 8): finish a two-player challenge together.
- **Uncle Adam's Day Off** (Epic, 25): earn 20 challenge stars and Uncle Adam hosts a victory party.

## Playtest protocol and build order

Watch before asking. With Oscar and his sister playing on the iPad, Adam notes these four things per challenge. No analytics are installed.

| Signal | How to notice | If it is bad |
| --- | --- | --- |
| Time to first laugh | Count seconds from start to the first laugh | Over 60 seconds: add a reaction to the first action |
| Stuck moments | Child says "what do I do?" or wanders | Add a hint arrow, shorten the text |
| Repeats | They redo it unasked | Good sign: keep the twist, add a harder version |
| Quits early | They switch to another task or stop | Cut the challenge length in half |

Ask two questions after: "What was the funniest bit?" and "What should be harder?".

### Build order

Ranked by fun per effort. The first three change how the whole board feels.

1. **Tier slots on the board** (Easy, Medium, Hard) and rebalanced rewards.
2. **90 second hint sparkle** pointing at the next goal.
3. **Crate Crash, Lamp Out, Fridge Light**: three cheap Easy wins that fill the first slot.
4. **Bed Bounce and Pond Hop**: the kids asked for trampolines, and JUMP is new.
5. **Noodle Slip and Toothpaste Trail**: Uncle Adam's signature gags.
6. **Dino Dig and Dino Parade**: dinosaurs are Oscar's favourite.
7. **Pizza Delivery**: finishes the pizza story.
8. **The new rooms**, once the house layout choice is made.
9. **Quest chains**, with prizes.
10. **Two-player versions** of selected challenges.

## Sources and what is not verified

Search results this session (snippets, not full papers):

- [Ryan, Rigby, Przybylski: motivational pull of video games](https://www.rochester.edu/warner/lida/wp-content/uploads/2022/11/02bfe513dd59366750000000.pdf): autonomy, competence and relatedness predict enjoyment. Adult and general player samples.
- [MDA framework paper](https://users.cs.northwestern.edu/%7Ehunicke/MDA.pdf) and [overview](https://en.wikipedia.org/wiki/MDA_framework): the eight kinds of fun.
- [Flow and flow control](https://mediadesign.de/de/news/2017/flow-and-flow-control-how-design-games-player-growth-replay-value-and-great-gaming), plus a [CHI paper on difficulty adjustment](https://www.cs.mcgill.ca/~jeromew/data/COMP766/CHI2016/p5595-smeddinck.pdf): the flow channel; automatic difficulty adjustment is debated.
- [Bartle's types](https://nickyee.com/facets/bartle.html): built on online-game players, not children.
- [Dark patterns in early childhood mobile games](https://papers.academic-conferences.org/index.php/ecgbl/article/view/1656) (ages 0 to 5) and [games popular with ages 10 to 15](https://uni.oslomet.no/belong/2023/11/21/from-digital-playground-to-dark-patterns/).

**Not verified.** The searches found nothing specific to ages 7 to 9. Piaget, Vygotsky, Fogg, goal-gradient, comedy theory, UX writing and economy design are from general knowledge and were not looked up. The tier times, coin values and the 90 second hint delay are design guesses to test with the kids. The suite assumes the living room, kitchen, rafters and garden as built; other zones wait for the house layout choice. This guide is the reference for building the game, so update it after each playtest.
