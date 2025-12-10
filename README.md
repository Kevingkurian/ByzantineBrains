# The Byzantine Brains: Fault-Tolerant Consensus with LLMs

**An Agent-Based Social Deduction Simulation Powered by Large Language Models**

## Project Overview
The Byzantine Brains project explores fault-tolerant consensus-building in distributed AI systems using Large Language Models (LLMs). Inspired by a social deduction game ( *Among Us*), the project simulates a spaceship environment where **Honest Agents** (Crewmates) must complete tasks and identify impostors, while **Byzantine Agents** (Impostors) attempt to deceive, eliminate agents, and manipulate consensus.

This project uses locally hosted LLMs (via Hugging Face Transformers) to drive agent decision-making, allowing for  behavioral analysis and "Game Theory" experimentation with AI agents.

## Objectives
- **Simulate Deception & Detection:** Analyze how LLM agents behave when assigned conflicting goals (Truth-Seeking vs. Deception).
- **Behavioral Statistics:** Track granular metrics like voting accuracy, movement patterns, and discussion persuasion to quantify agent performance.
- **Fault Tolerance:** Study how honest agents reach consensus (voting out impostors) despite active disinformation from Byzantine actors.

## Technologies
- **Languages**: Python 3.10+
- **LLM Backend**: `transformers`, `torch` (Local Execution via CUDA/CPU)
- **Agent Logic**:  `HonestAgent` and `ByzantineAgent` classes
- **Simulation Engine**:  `GameEngine` with state management and logging
- **Data Storage**: CSV-based statistical logging for post-game analysis

## Project Structure

```text
/agents
    honest_agent.py        # Logic for Crewmates: Deduction, Alibi checking, Voting
    byzantine_agent.py     # Logic for Impostors: Deception, Tagging (Kills), Deflection
    base_agent.py          # Shared agent interfaces

/config
    settings.py            # Global game settings (Map layout, Round counts, Role distribution)

/core
    state.py               # Manages the "World View" (Locations, Bodies, Occupants, Stats)
    logger.py              # Handles game logging and CSV export
    llm.py                 # Wrapper for Hugging Face Transformers (Model loading & Generation)

/game
    game_engine.py         # Main loop: Movement Phase -> Discussion Phase -> Voting

/logs                      # Generated game logs and stats
    /Game_1234/            # Unique folder per game session
        game_stats.csv     # Final outcome and detailed player metrics

main.py                    #  to launch the simulation
