# RL_Labs

Lab assignments for the Reinforcement Learning course. Each lab lives in its own top-level folder.

## Labs

### [Lab1](Lab1)

Introduction to [Gymnasium](https://gymnasium.farama.org/): setting up the environment, exploring observation/action spaces, and running a random agent across multiple environments.

- Set up and verify the Gymnasium install
- Create and step through an environment (CartPole)
- Explore observation & action spaces across CartPole, FrozenLake, MountainCar, and Taxi
- Build a random agent (random actions until episode end)
- Log rewards and compare `terminated` vs `truncated`
- Summarize and compare results across environments

**Contents:**
- `Lab1_AIE23060_RL.ipynb` — main notebook
- `AI_report.html` / `AI_report.pdf` — generated report
- `lab1_final_comparison.csv` — environment comparison table
- `*.png` — result plots (per-environment random agent runs, reward comparison, episode steps, terminated vs truncated)

### [Lab3](Lab3)

**Stealth Maze** — a custom 10x10 grid-world term project: a thief (agent) evading randomly-walking police units to reach treasure, solved with tabular Q-learning and compared against SARSA for the on-policy/off-policy discussion.

- Custom `MazeEnv` (gym-style `reset`/`step`, ASCII render) with walls, a fixed treasure location, and randomly-walking police that bounce off walls/each other without stacking
- Reduced state representation for tabular tractability: `(thief_x, thief_y, direction_to_nearest_police, distance_to_nearest_police, direction_to_treasure)` instead of the full joint state of all police
- Actions: `up`, `down`, `left`, `right`, `attack` (back-attack kill only lands when the thief is adjacent and behind a police unit's facing direction)
- Reward shaping via potential-based shaping using true walls-aware BFS shortest-path distance to the treasure (a straight-line Manhattan potential was tried first and actively penalized the maze's only viable path, forcing a mandatory detour — documented as a mid-project bug fix)
- Q-learning agent trained for 15,000 episodes against 4 police (scaled down from an original 8-police design for tabular tractability), with rolling-average tracking of win rate, timeout/death rate, reward, and steps

**Status:** reward and survival time are still climbing at episode 15,000 (not yet plateaued); the environment is hard enough that wins are rare under the current reward/police settings. SARSA and a radar-based state variant (`MazeEnvRadar`) were designed but not re-run under the final corrected reward-shaping setup — flagged as open work in the notebook's discussion rather than reported with stale numbers.

**Contents:**
- `StealthMaze.ipynb` — main notebook (environment, agents, training, plots, discussion)
- `AIE23060_LeekhithNunna_Lab_3.pdf` — submitted lab report
- `LabExperiment3.pdf` — lab handout/template
- `win_rate.png`, `timeout_death_rate.png`, `avg_reward.png`, `avg_steps.png` — rolling 500-episode training curves
- `amrita_logo.png` — report header asset

## License

[MIT](LICENSE)
