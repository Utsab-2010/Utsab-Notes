### Contributions
- Superhuman level chess
- no prior human chess data used.
- Blank-slate RL , entirely Self Play

### Core Methodology
NN Architecture:
- network took into state(current position) and output 2 vectors
	- move probabilities of different moves
	- value estimate: estimating the expected outcome of the game from that position

Monte Carlo Tree Search
- Used this instead of the traditional alpha-beta search used by chess engines
- Search is guided by the NN predictions
	- explores future moves by selecting those with high move probability and estimated value
	- 