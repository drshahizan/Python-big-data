<h2>Chess Games Analysis with Three Python Libraries</h2> 

<img src="https://user-images.githubusercontent.com/95403713/215369088-d53ead7f-c979-42ab-a8c0-44715d81e2f7.jpg" width="500" height="250"/>

<h2>Group Rojak</h2>
<table>
  <tr>
    <th>Name</th>
    <th>Matric</th>
  </tr>
  <tr>
    <th>Eddie Wong Chung Pheng </th>
    <th>A20EC0031</th>
  </tr>
  <tr>
    <th>Vincent Boo Ee Khai</th>
    <th>A20EC0231</th>
  </tr>
    <tr>
    <th>Madihah binti Che Zabri </th>
    <th>A20EC0074</th>
  </tr>
  <tr>
    <th>Nurarissa Dayana binti Mohd Sukri</th>
    <th>A20EC0120</th>
</table>

## Introduction
This dataset contains data for every rated Lichess game played between January 2013 and December 2014. There were approximately 15,000,000 games in total. It includes the players' names, ratings, the winner, the opening, the number of moves, etc. We will conduct an analysis to gain insights on the games and address our research questions. We hope to discover interesting patterns by analysing the various characteristics of each game, including the type of opening employed, the ratings of the players, and more. This data analysis allows us to comprehend the effects of various moves, strategies, and time controls on game outcomes. This research will also compare the performance of three Python libraries: Pandas, Vaex, and Koalas.

## Libraries
1. Pandas
2. Vaex
3. Koalas

<h2>Dataset</h2>
<a href="https://www.kaggle.com/datasets/maca11/chess-games-from-lichess-20132014?select=Lichess_2013_2014_Complete.csv">Kaggle: 15 Million Chess Games from Lichess (2013-2014)</a><br>
The dataset above that we had chosen is data from all rated games played in Lichess from January 2013 to December 2014, in total there are around 15,000,000 games.This dataset consists of 1048576 rows and 16 columns and the size of this dataset is 1.99GB.

<h4>Attribute Information:</h4>
<table>
  <tr>
    <th>Acronym</th>
    <th>Description</th>
  </tr>
  <tr>
    <th>WhiteElo</th>
    <th>Elo of the player with white pieces</th>
  </tr>
    <tr>
    <th>BlackElo</th>
    <th>Elo of the player with black pieces</th>
  </tr>
    <tr>
    <th>WhiteName</th>
    <th>Name of the player with white pieces</th>
  </tr>
    <tr>
    <th>BlackName</th>
    <th>Name of the player with black pieces</th>
  </tr>
    <tr>
    <th>Winner</th>
    <th>Color of the winning pieces. If the game ended in Draw it shows it</th>
  </tr>
    <tr>
    <th>Termination</th>
    <th>How the game ended, it can be: Normal, Time Forfeit, Abandon or Rules infraction</th>
  </tr>
    <tr>
    <th>Site</th>
    <th>URL of the game</th>
  </tr>
    <tr>
    <th>Day</th>
    <th>Day when the game was played</th>
  </tr>
    <tr>
    <th>Month</th>
    <th>Month when the game was played)</th>
  </tr>    
  <tr>
    <th>Year</th>
    <th>Year when the game was played</th>
  </tr>    
  <tr>
    <th>InitialTime</th>
    <th>Time each player has before starting the game in seconds</th>
  </tr>    
  <tr>
    <th>Increment</th>
    <th> Increment in the time after each player makes a move in seconds
</th>
  </tr>
    <tr>
    <th>TimeControl</th>
    <th> Classification of the games based on the estimated duration of a game calculated as InitialTime+ 40*Increment</th>
  </tr>
    <tr>
    <th>Opening</th>
    <th>Opening Name</th>
  </tr>
    <tr>
    <th>ECO</th>
    <th>Classification of the games based on the ECO(Encyclopaedia of Chess Openings) </th>
  </tr>
    <tr>
    <td>Number of Moves</td>
    <td>Number of moves of the game</td>
  </tr>
      <tr>
    <th>FEN</th>
    <th>
    FEN of the game
    <br>
    * stands for Forsyth-Edwards Notation 
    <br>
    *it is the standard notation to describe positions of a chess game
    </th>
  </tr>
</table>
  
  ## Content
  <h5>1. Import Dataset</h5>
  <h5>2. Import Libraries</h5>
  <h5>3. Read Dataset</h5>
  <h5>4. Data Preparation and Cleaning</h5>
  <h5>5. Exploratory Analysis and Visualization</h5>
  
  ## Summary
  
 Wall time comparisons in seconds of the three libraries' performance in completing tasks.
  
| Task | Pandas | Vaex | Koalas |
| ---- | ------ | ---- | ------ |
| Read data | 59.9 | 6.16 | 62.0 |
| View data | 0.000504 | 0.00482 | 0.475 |
| Handle missing data | 0.0805 | - | 48.4 |
| Drop columns | 1.38 | 0.00123 | 0.247 |
| Sort data | 4.59 | 11.7 | 0.471 |
| Compute Mean | 0.0467 | 19.6 | 26.5 |
| Plot Distribution Graph | 1.39 | - | 60.0 |
| Get max of Elo rating | 0.115 | 22.4 | 29.8 |
| Get min of Elo rating data | 0.292 | 11.4 | 27.2 |
| Find data correlation | - | 9.5 | 125.0 |
| Solving Question 1 | 8.34e-6 |  |  |
| Solving Question 2 | 0.0516 | 16.8 | 1.5 |
| Solving Question 3 | 4.69 | 16.5 | 0.374 |
| Solving Question 4 |  |  |  |
| Solving Question 5 | 0.0906 |  |  |
