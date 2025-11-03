content = """# Intelligent Hangman Assistant (Hybrid HMM + Deep Reinforcement Learning)

This project implements an advanced AI system that plays Hangman using a combination of Hidden Markov Models (HMM) and Deep Q-Learning (DQN). Rather than choosing letters based on simple frequency statistics, this model learns English structure, predicts letter likelihoods, and strategically selects optimal guesses to maximize win rate.

## Team
| Name | SRN |
|------|------|
| Sharath Gowda G R | PES2UG24CS823 |
| Nandita R Nadig | PES2UG23CS365 |
| Moulya K A | PES2UG23CS351 |
| Najmus Seher | PES2UG23CS359 |


## Overview

### Hybrid Approach
| Component | Role |
|----------|------|
| HMM | Provides probability distribution of each letter at each blank position |
| Deep Q-Learning (DQN) | Learns optimal decision strategy to maximize win probability |

## Training Results Example

Loaded 49979 words.
HMM loaded successfully from /kaggle/working/hmm_models/hmm_global.npz
--- Starting Training for 50000 Episodes ---

Episode: 1000/50000
  Avg. Reward (Train): -37.33 | Epsilon: 0.951
  Eval Success Rate: 4.00%

Episode: 2000/50000
  Avg. Reward (Train): -37.45 | Epsilon: 0.905
  Eval Success Rate: 10.20%

Episode: 3000/50000
  Eval Success Rate: 11.20%

Final:
  Success Rate: 13.30%
  Avg. Wrong Guesses: 5.71
  Avg. Repeated Guesses: 0.00

## Key Observations
- Forward-Backward outputs needed conversion to usable letter probability.
- State space limited to a 53-dimensional hybrid vector.
- Reward engineering was critical for encouraging winning behavior.
- Action masking drastically reduced repeated guesses.

## Strategies

### HMM Design
- Each hidden state represents one English alphabet letter.
- Transition probabilities learned from corpus text.
- Emission probabilities model observed letters.
- Forward–Backward inference feeds probability vectors to DQN agent.

### RL State / Reward
- State vector = 53 dimensions
- Includes: letter probability, guessed memory, normalized lives
- Reward system encourages correct guesses and final winning objective.

## Exploration vs Exploitation
- Epsilon-greedy with exponential decay used.
- Slow decay to prevent getting stuck in poor strategies.

## Future Improvements
- Dueling DQN
- Prioritized Experience Replay
- Separate models per word-length bucket

## Tech Stack
| Component | Library |
|----------|----------|
| RL | PyTorch |
| HMM | hmmlearn |
| Data | English 50k corpus |
| Notebook Execution | Kaggle |

## How To Run
1. Preprocess corpus + compute letter statistics.
2. Train HMM on corpus.
3. Train DQN agent.
4. Evaluate final win percentage.
