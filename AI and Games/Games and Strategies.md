# Games
Games have:
- At least 2 of agents (players) interacting with each other
- At the end of the game, every player receives a pay-off based on moves each other made
- Clearly defined rules for what the players can do

Randomness in games can be solved with a third player, **nature**.

**Imperfect information** & **simultaneous moves** can be wrapped in a bubble.

A **fully specified strategy** defines what a player should do in every single possible situation.

A **pure strategy** - defines which choices a player should make on each level of the subtree.
Exactly one of the available moves to the player is in the subtree.

A game with **perfect information** has information sets of size 1.
Information sets are the box around, e.g. RPS in RPS.

# Normal Form
Normal form is a table of every strategy from the players with the respective payouts for each combination.
![87bbcab64d5ffd65fe3a9b9c7935c524.png](./87bbcab64d5ffd65fe3a9b9c7935c524.png)

A strategy is winning if all of its payoffs are > 0, and ensures a draw if its payoffs are ≥ 0.
**Zermelo's theorem** is that in a zero-sum, 2P, finite, perfect info, no chance, either:
- P1 has a winning strategy
- P2 has a winning strategy
- Both players can ensure a draw

# Equilibria
A **best response** is a strategy which has the greatest payoff out of your strategies, considering your opponents strategies.

A **Nash equilibrium** is when every players are playing a best response to another player.
It always exists for 2-player, zero-sum, perfect information games without chance.
It puts other players in a state where changing their strategies individually yields no additional gain.

In zero-sum games, strategy pair (i, j) is an equilibrium if and only if the cell is maximal in its column, and minimal in its row.
Maximin = Minimax.
In non-zero-sum games, an equilibrium may not end up being the best collective outcome (prisoner dilemma).
A **value** of a zero-sum game is the payoff of an equilibrium point.

The **Nash theorem** is that every 2P, zero-sum, perfect information, finite game has at least one pure strategy equilibrium point.
If there isn't perfect information, a mixed strategy equilibrium is guaranteed.

# Mixed Strategies

A **Mixed strategy** is a probability distribution over all available strategies for a player.

A strategy is **dominated** by another if, for all strategy combinations from other players, the payoff is always less than of the other. These can be removed without losing equilibria.
Removal order does matter, and it must be iterative.

# Minimax
Minimax takes a depth-first approach to finding the value and hence equilibria of 2-person, zero-sum, perfect-info games.
For imperfect info games, minimax doesn't work. This can be fixed by calculating expected payoffs.
Incomplete

# Alpha-Beta Pruning
Incomplete

# Learning
Learning is preferred over minimax when:
- Good heuristics cannot be found
- Branching factor is high
- Equilibria are hard to compute
Most games have trees too large to search.

In reinforcement learning:
- You learn while playing
- You obtain feedback from the outcome of the game
- A sequence of moves is required before the outcome is revealed
- You don't know which move was crucial to the outcome

### Regret
In a exploration-exploitation scenario, with actions and rewards:
- The action-value is the mean reward for action a, Q(a)
- The count is the expected number of selections for action a
- The optimal value V* is the maximal Q(a)
- The gap is the lost potential value, V* - Q(a)
- The regret is the opportunity loss for a step, 
Maximise cumulative reward and minimise total regret.
Ensure small counts for large gaps.

Greedy will forever exploit the best value is has.
$\epsilon$-Greedy will forever explore a random action.
Both have linear regret.

Solution is to decay chance of exploring.
Leads us to Upper Confidence Bounds, UCB1.
Logarithmic asymptotic total regret.