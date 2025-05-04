# 🕹️ Tic Tac Toe

A simple web-based Tic Tac Toe game built with HTML, CSS, and JavaScript. Play against a friend in a classic 3x3 grid!

## 🚀 Features

- Interactive 3x3 game board
- Two-player gameplay (Player X and Player O)
- Win and draw detection
- Restart button to reset the game
- Responsive and minimal UI

## 📸 Preview

![Tic Tac Toe Screenshot](screenshot.png) <!-- Add a screenshot file to your repo -->

## 🛠️ How to Run Locally

1. **Clone the repository**:
   ```bash
   git clone https://github.com/your-username/tic-tac-toe.git
   cd tic-tac-toe

📋 How to Play
Player X starts the game.

Click on any empty cell to make a move.

Players alternate turns.

The game announces a winner or a draw.

Click Restart Game to play again.

🧩 Future Enhancements
Highlight winning cells

Add AI opponent (easy/hard)

Add score tracking

Make mobile-friendly

📄 License
This project is licensed under the MIT License.



<!DOCTYPE html>
<html>
<head>
    <title>Tic Tac Toe</title>
    <style>
        body { font-family: Arial; text-align: center; }
        .board { display: grid; grid-template-columns: repeat(3, 100px); gap: 5px; margin: 20px auto; width: 310px; }
        .cell { width: 100px; height: 100px; border: 2px solid #000; font-size: 60px; cursor: pointer; }
        button { padding: 10px 20px; font-size: 16px; margin-top: 20px; }
    </style>
</head>
<body>
    <h1>Tic Tac Toe</h1>
    <div id="status">Player X's turn</div>
    <div class="board" id="board"></div>
    <button onclick="resetGame()">Restart Game</button>

    <script>
        let currentPlayer = 'X';
        let board = ['', '', '', '', '', '', '', '', ''];
        const statusDiv = document.getElementById('status');
        const boardDiv = document.getElementById('board');

        // Create board
        for (let i = 0; i < 9; i++) {
            const cell = document.createElement('div');
            cell.className = 'cell';
            cell.setAttribute('data-index', i);
            cell.addEventListener('click', handleCellClick);
            boardDiv.appendChild(cell);
        }

        function handleCellClick(e) {
            const index = e.target.getAttribute('data-index');
            if (board[index] === '' && !checkWinner()) {
                board[index] = currentPlayer;
                e.target.textContent = currentPlayer;
                if (checkWinner()) {
                    statusDiv.textContent = `Player ${currentPlayer} wins!`;
                } else if (board.every(cell => cell !== '')) {
                    statusDiv.textContent = "It's a draw!";
                } else {
                    currentPlayer = currentPlayer === 'X' ? 'O' : 'X';
                    statusDiv.textContent = `Player ${currentPlayer}'s turn`;
                }
            }
        }

        function checkWinner() {
            const winPatterns = [
                [0, 1, 2], [3, 4, 5], [6, 7, 8], // rows
                [0, 3, 6], [1, 4, 7], [2, 5, 8], // columns
                [0, 4, 8], [2, 4, 6]             // diagonals
            ];
            return winPatterns.some(pattern => 
                board[pattern[0]] && 
                board[pattern[0]] === board[pattern[1]] && 
                board[pattern[0]] === board[pattern[2]]
            );
        }

        function resetGame() {
            board = ['', '', '', '', '', '', '', '', ''];
            currentPlayer = 'X';
            statusDiv.textContent = `Player X's turn`;
            document.querySelectorAll('.cell').forEach(cell => cell.textContent = '');
        }
    </script>
</body>
</html> 

   
