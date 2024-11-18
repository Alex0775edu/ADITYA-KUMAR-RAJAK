# ADITYA-KUMAR-RAJAK
TIC TAC TOE GAME BY ADITYA KUMAR RAJAK 

<DOCTYPE html>
<html lang="en">
<head>
    
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Tic Tac Toe GAME BY ADITYA KUMAR RAJAK</title>
    <style>
        body {
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            font-family: Arial, sans-serif;
        }
        #board {
            display: grid;
            grid-template-columns: repeat(3, 100px);
            grid-template-rows: repeat(3, 100px);
            gap: 5px;
        }
        .cell {
            width: 100px;
            height: 100px;
            display: flex;
            justify-content: center;
            align-items: center;
            font-size: 24px;
            cursor: pointer;
            border: 1px solid #000;
        }
    </style>
</head>
<body>
    
    
    <div id="board"></div>
    <script>
        const boardElement = document.getElementById('board');
        let currentPlayer = 'X';
        const board = ['', '', '', '', '', '', '', '', ''];

        function createBoard() {
            board.forEach((cell, index) => {
                const cellElement = document.createElement('div');
                cellElement.classList.add('cell');
                cellElement.textContent = cell;
                cellElement.addEventListener('click', () => handleCellClick(index));
                boardElement.appendChild(cellElement);
            });
        }

        function handleCellClick(index) {
            if (board[index] === '') {
                board[index] = currentPlayer;
                renderBoard();
                if (checkWinner()) {
                    setTimeout(() => alert(`${currentPlayer} wins!`), 10);
                    resetGame();
                } else if (board.every(cell => cell !== '')) {
                    setTimeout(() => alert("It's a tie!"), 10);
                    resetGame();
                }
                currentPlayer = currentPlayer === 'X' ? 'O' : 'X';
            }
        }

        function renderBoard() {
            const cells = document.querySelectorAll('.cell');
            cells.forEach((cell, index) => {
                cell.textContent = board[index];
            });
        }

        function checkWinner() {
            const winningCombinations = [
                [0, 1, 2],
                [3, 4, 5],
                [6, 7, 8],
                [0, 3, 6],
                [1, 4, 7],
                [2, 5, 8],
                [0, 4, 8],
                [2, 4, 6]
            ];
            return winningCombinations.some(combination => {
                return combination.every(index => board[index] === currentPlayer);
            });
        }

        function resetGame() {
            board.fill('');
            renderBoard();
            currentPlayer = 'X';
        }

        createBoard();
    </script>
    
</body>
</html>