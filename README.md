<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Tic Tac Toe</title>
  <style>
    body {
      margin: 0;
      padding: 0;
      background-color: #f7f7f7;
    }
    
    #container {
      width: 300px;
      margin: 50px auto;
      padding: 10px;
      border: 1px solid #ccc;
      border-radius: 5px;
      box-shadow: 0 2px 5px rgba(0,0,0,0.3);
      background-color: #fff;
    }
    
    #message {
      text-align: center;
      font-size: 24px;
      margin-bottom: 10px;
    }
    
    #board {
      width: 100%;
      height: 300px;
      display: flex;
      flex-wrap: wrap;
      justify-content: space-between;
    }
    
    .cell {
      width: calc(33.33% - 10px);
      height: 100px;
      margin-bottom: 10px;
      border-radius: 5px;
      background-color: #eee;
      font-size: 72px;
      font-weight: bold;
      text-align: center;
      line-height: 100px;
      cursor: pointer;
      box-shadow: 0 2px 5px rgba(0,0,0,0.3);
    }
    
    .cell:hover {
      background-color: #ddd;
    }
    
    .cell:active {
      box-shadow: none;
    }
    
    .player-1 {
      color: #f44336;
    }
    
    .player-2 {
      color: #2196f3;
    }
  </style>
</head>
<body>
  <div id="container">
    <div id="message"></div>
    <div id="board">
      <div class="cell" onclick="play(0)"></div>
      <div class="cell" onclick="play(1)"></div>
      <div class="cell" onclick="play(2)"></div>
      <div class="cell" onclick="play(3)"></div>
      <div class="cell" onclick="play(4)"></div>
      <div class="cell" onclick="play(5)"></div>
      <div class="cell" onclick="play(6)"></div>
      <div class="cell" onclick="play(7)"></div>
      <div class="cell" onclick="play(8)"></div>
    </div>
  </div>
<script>
  let player1Name = prompt("Enter the name of Player 1:");
let player2Name = prompt("Enter the name of Player 2:");
let currentPlayer = 1;
let board = ['', '', '', '', '', '', '', '', ''];

document.getElementById('message').innerHTML = player1Name + "'s turn";

function play(index) {
  if (board[index] === '') {
    const cell = document.getElementsByClassName('cell')[index];
    board[index] = currentPlayer === 1 ? 'X' : 'O';
    cell.innerHTML = board[index];
    cell.classList.add('player-' + currentPlayer);
    
    if (checkWin()) {
      endGame(currentPlayer);
    } else if (checkTie()) {
      endGame(0);
    } else {
      currentPlayer = currentPlayer === 1 ? 2 : 1;
      document.getElementById('message').innerHTML = currentPlayer === 1 ? player1Name + "'s turn" : player2Name + "'s turn";
    }
  }
}

  
  function endGame(winner) {
  const messageElement = document.getElementById('message');
  if (winner === 0) {
    messageElement.innerHTML = "It's a tie!";
  } else {
    const winnerName = winner === 1 ? player1Name : player2Name;
    messageElement.innerHTML = winnerName + " wins!";
  }
  disableBoard();
}

function disableBoard() {
  const cells = document.getElementsByClassName('cell');
  for (let i = 0; i < cells.length; i++) {
    cells[i].removeAttribute('onclick');
  }
}

  
  function checkWin() {
    const winCombinations = [
      [0, 1, 2], [3, 4, 5], [6, 7, 8], // Rows
      [0, 3, 6], [1, 4, 7], [2, 5, 8], // Columns
      [0, 4, 8], [2, 4, 6] // Diagonals
    ];
    for (let i = 0; i < winCombinations.length; i++) {
      const [a, b, c] = winCombinations[i];
      if (board[a] !== '' && board[a] === board[b] && board[a] === board[c]) {
        return true;
      }
    }
    return false;
  }
  
  function checkTie() {
    for (let i = 0; i < board.length; i++) {
      if (board[i] === '') {
        return false;
      }
    }
    return true;
  }
</script>
  
