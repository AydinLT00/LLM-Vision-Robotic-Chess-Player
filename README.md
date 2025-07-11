# LLM-Vision-Robotic-Chess-Player
Using a Large Language Model (GPT) to control a UR5e robotic arm for playing chess in a PyBullet simulation.

## **Integrating LLMs and Robotics to Play Chess**

![alt text](https://img.shields.io/badge/License-MIT-yellow.svg)

This project demonstrates how a Large Language Model (LLM) can be used for high-level decision-making to control a robotic arm playing chess. The system interprets human-like commands and strategic goals, translates them into valid chess moves, and executes them with a UR5e robot in a PyBullet simulation.

## **Showcase & Demo**

The LLM was prompted to follow specific opening strategies against a human player.
Giuoco Piano Opening	London System Opening	CLIPORT Vision-Based Move
![alt text](media/giuoco_piano.gif)
![alt text](media/london_system.gif)
![alt text](media/cliport_demo.gif)

## **Key Features**

LLM for Strategy: Utilizes GPT-4o-mini to generate chess moves based on strategic instructions (e.g., "Play the Italian Opening").
Robotic Execution: A UR5e arm with a Robotiq 2F85 gripper performs the physical pick-and-place actions.
Realistic Simulation: Built in PyBullet for accurate physics simulation and collision detection.
Robust Move Validation: Integrates the python-chess library to ensure all LLM-generated moves are legal before execution.
Vision-Language Model (VLM): Includes an experimental module using CLIPORT to determine pick and place coordinates from an image and a text command (e.g., "Pick the black King and place on c2").

## **How It Works**

The system follows a pipeline to translate a strategic goal into a physical action:
![alt text](media/pipeline.png)

Figure: The system pipeline for language-to-action translation (Figure 3.1 from the report).
Prompt Engineering: The LLM is given a detailed prompt containing the game history (PGN), a list of available pieces, and a strategic objective.
LLM Inference: The LLM returns a candidate move in a structured format (e.g., "Pick the white Pawn 3 and place it on e4").
Parsing & Validation: The output is parsed and checked against the python-chess engine to confirm its legality. If the move is illegal, feedback is sent to the LLM for a retry.
Action Execution: The validated move is translated into XYZ coordinates, and the UR5e arm executes the pick-and-place sequence.
Installation & Usage
Clone the repository:

git clone https://github.com/YOUR_USERNAME/LLM-Robotic-Chess-Player.git
cd LLM-Robotic-Chess-Player


Set up a virtual environment:

python -m venv venv
source venv/bin/activate  # On Windows, use `venv\Scripts\activate`

Install dependencies:

pip install -r requirements.txt

Set up your API Key:
Create a .env file in the root directory and add your OpenAI API key:

OPENAI_API_KEY="your_secret_key_here"

The program will load this key. Do not commit the .env file to GitHub.
Run the simulation:

python src/main.py

Project Report
For a detailed explanation of the methodology, experiments, and results, please see the full Project Report.
Acknowledgments
This project was completed as part of a group project at Politecnico di Milano.
Team: Mohsen Ghasemi, Aidin Latifi, Shiyuan Liu
Professor: Loris Roveda
