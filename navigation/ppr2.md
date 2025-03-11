---
layout: page
title: Write Up 
permalink: /ppr2/
---


# **Chess Game Analysis Feature Write-up**
_A detailed breakdown of how my chess analysis feature meets **AP CSP CPT and PPR requirements**._

---

# **Part 1: Create Performance Task (CPT) Requirements**

## **1️⃣ Program Purpose and Function**
This project is a **Chess Game Analysis Tool** that allows users to **upload PGN files**, **navigate through chess moves**, and **evaluate board positions** using the **Stockfish chess engine**. The system is composed of:

- **Frontend:** Built using `Chessboard.js` and `Chess.js` to display the **chessboard** and **moves dynamically**.
- **Backend:** **Flask-based API** that handles **move evaluations** using **Stockfish AI**.
- **Database:** **Stores user moves, evaluations, and game history**.

Users can **step through game moves**, **view AI-generated evaluations**, and **track move quality** (e.g., **"Brilliant," "Blunder"**). The tool supports **full CRUD operations**, allowing users to **add, edit, and delete moves dynamically**.

---

## **2️⃣ Data Abstraction (List Usage)**
The system **stores move history and evaluations** using **lists and structured data storage**.

### **Storing Move Data in a List**
```python
move_history = []

def store_move(move, evaluation):
    move_history.append({"move": move, "evaluation": evaluation})
```

✔ **Stores move history as a list of dictionaries.**  
✔ **Each dictionary contains a move and its evaluation score.**  

### **Retrieving Move Data from a List**
```javascript
const moveList = [];

function addMove(move, evaluation) {
    moveList.push({ move: move, evaluation: evaluation });
    updateMoveTable();
}
```
✔ **Retrieves stored move data for display.**  
✔ **Ensures smooth UI updates when moves are added.**  

---

## **3️⃣ Algorithm Implementation (Sequencing, Selection, Iteration)**
### **Sequencing**
1. **User uploads a PGN file.**
2. **Program parses the moves and updates the board.**
3. **When a move is selected, the backend evaluates it.**
4. **Stockfish AI returns a best move and evaluation.**
5. **The frontend displays the evaluation dynamically.**

### **Selection**
```python
if eval_score > 100:
    status = "Brilliant"
elif eval_score < -100:
    status = "Blunder"
else:
    status = "Neutral"
```

✔ **Uses conditionals to classify move quality.**  

### **Iteration**
```javascript
moveList.forEach(move => {
    console.log(`Move: ${move.move}, Evaluation: ${move.evaluation}`);
});
```
✔ **Loops through stored moves and logs them dynamically.**  

---

## **4️⃣ Program Output**
The program provides both **visual and textual outputs**.

### **Chessboard Display Updates**
```javascript
board.position(game.fen());
```

### **Move Evaluations Displayed in UI**
```javascript
statusEl.textContent = `Evaluation: ${data.evaluation}, Best Move: ${data.best_move}`;
```

✔ **Outputs board position and Stockfish evaluations dynamically.**  

---

# **Part 2: Personalized Project Reference (PPR) Requirements**

## **1️⃣ Student-Developed Procedure**
### **Procedure Name:** `evaluate_position`  
This function **evaluates a chess position** using **Stockfish AI**.

#### **Procedure Implementation**
```python
def evaluate_position(fen, depth=15):
    """Evaluates a chess position using Stockfish."""
    stockfish.set_fen_position(fen)
    best_move = stockfish.get_best_move()
    eval_score = stockfish.get_evaluation()["value"]

    status = categorize_evaluation(eval_score)

    return {"best_move": best_move, "evaluation": eval_score, "status": status}
```
✔ **Demonstrates sequencing:** Calls Stockfish functions in a **logical order**.  
✔ **Uses selection:** The function **categorizes moves** based on evaluation scores.  
✔ **Implements iteration:** **Stockfish searches the move tree recursively** using a specified search depth.  

---

## **2️⃣ Calling the Procedure**
### **Frontend Calls the Evaluation API**
```javascript
async function fetchEvaluation(fen) {
    const response = await fetch("/api/evaluation", {
        method: "POST",
        headers: { "Content-Type": "application/json" },
        body: JSON.stringify({ fen: fen })
    });
    const data = await response.json();
    updateEvaluationUI(data);
}
```
✔ **Sends FEN notation to backend for analysis.**  
✔ **Receives evaluation data and updates the UI dynamically.**  

---

## **3️⃣ Storing Data in a List (Collection Usage)**
The **chess moves and evaluations** are stored in a structured format using lists and database models.

```python
class Move(db.Model):
    id = db.Column(db.Integer, primary_key=True)
    notation = db.Column(db.String(10))
    score = db.Column(db.Float)
    status = db.Column(db.String(20))
    played = db.Column(db.Boolean, default=False)

    def __init__(self, notation, score, status, played=False):
        self.notation = notation
        self.score = score
        self.status = status
        self.played = played
```

✔ **Abstracts move storage into a structured model.**  
✔ **Uses a list-based structure to efficiently manage moves.**  

---

## **4️⃣ Using Data from a List**
The stored moves are dynamically retrieved and displayed for analysis.

```javascript
const moveList = [];

function addMove(move, evaluation) {
    moveList.push({ move: move, evaluation: evaluation });
    updateMoveTable();
}
```
✔ **Accesses move data dynamically to update UI components.**  
✔ **Ensures that move data remains up-to-date during game analysis.**  

---

## **5️⃣ Commenting & Acknowledgments**
- The project includes **clear inline comments** explaining function roles.
- Uses **open-source libraries** (`Chess.js`, `Stockfish`).
- **Acknowledgments:** Inspired by online chess analysis tools.

---

## **Conclusion**
**CPT and PPR requirements:**

✔ **Handling input dynamically** (**PGN uploads, user interactions**).  
✔ **Utilizing lists to store move history and evaluations.**  
✔ **Implementing a well-structured student-developed procedure.**  
✔ **Applying sequencing, selection, and iteration.**  
✔ **Providing clear and interactive outputs dynamically.**  

