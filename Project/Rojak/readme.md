<h2>Chess Games Analysis with Three Python Libraries</h2> 

<img src="https://user-images.githubusercontent.com/95403713/215369088-d53ead7f-c979-42ab-a8c0-44715d81e2f7.jpg" width="500" height="250"/>

<h2>Group Rojak</h2>
<table>
  <tr>
    <th>Name</th>
    <th>Matric</th>
  </tr>
  <tr>
    <td>Eddie Wong Chung Pheng </td>
    <td>A20EC0031</td>
  </tr>
  <tr>
    <td>Vincent Boo Ee Khai</td>
    <td>A20EC0231</th>
  </tr>
    <tr>
    <td>Madihah binti Che Zabri </td>
    <td>A20EC0074</td>
  </tr>
  <tr>
    <td>Nurarissa Dayana binti Mohd Sukri</td>
    <td>A20EC0120</td>
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
    <td>WhiteElo</td>
    <td>Elo of the player with white pieces</td>
  </tr>
    <tr>
    <td>BlackElo</td>
    <td>Elo of the player with black pieces</td>
  </tr>
    <tr>
    <td>WhiteName</td>
    <td>Name of the player with white pieces</td>
  </tr>
    <tr>
    <td>BlackName</td>
    <td>Name of the player with black pieces</td>
  </tr>
    <tr>
    <td>Winner</td>
    <td>Color of the winning pieces. If the game ended in Draw it shows it</td>
  </tr>
    <tr>
    <td>Termination</td>
    <td>How the game ended, it can be: Normal, Time Forfeit, Abandon or Rules infraction</td>
  </tr>
    <tr>
    <td>Site</td>
    <td>URL of the game</td>
  </tr>
    <tr>
    <td>Day</td>
    <td>Day when the game was played</td>
  </tr>
    <tr>
    <td>Month</td>
    <td>Month when the game was played)</td>
  </tr>    
  <tr>
    <td>Year</td>
    <td>Year when the game was played</td>
  </tr>    
  <tr>
    <td>InitialTime</td>
    <td>Time each player has before starting the game in seconds</td>
  </tr>    
  <tr>
    <td>Increment</td>
    <td> Increment in the time after each player makes a move in seconds</td>
  </tr>
    <tr>
    <td>TimeControl</td>
    <td> Classification of the games based on the estimated duration of a game calculated as InitialTime+ 40*Increment</td>
  </tr>
    <tr>
    <td>Opening</td>
    <td>Opening Name</td>
  </tr>
    <tr>
    <td>ECO</td>
    <td>Classification of the games based on the ECO(Encyclopaedia of Chess Openings) </td>
  </tr>
    <tr>
    <td>Number of Moves</td>
    <td>Number of moves of the game</td>
  </tr>
      <tr>
    <td>FEN</td>
    <td>FEN of the game
    <br>
    * stands for Forsyth-Edwards Notation 
    <br>
    *it is the standard notation to describe positions of a chess game
    </td>
  </tr>
</table>
  
  ## Content
  <h5>1. Import Dataset</h5>
  <h5>2. Import Libraries</h5>
  <h5>3. Data Preparation and Cleaning</h5>
  <h5>4. Exploratory Analysis and Visualization</h5>
  <h5>5. Research Questions</h5>
  
  ## Summary
  
 Wall time comparisons in seconds of the three libraries' performance in completing tasks.
  
| Task | Pandas | Vaex | Koalas |
| ---- | ------ | ---- | ------ |
| Read data | 55.4 | 6.07 | 70.0 |
| View data | 0.00318 | 0.00298 | 0.407 |
| Handle missing data | 16.3 | 87.0 | 49.7 |
| Drop columns | 1.84 | 0.00143 | 0.193 |
| Sort data | 6.87 | 9.6 | 0.33 |
| Compute Mean | 0.0467 | 19.6 | 26.5 |
| Plot Distribution Graph | 1.39 | 23.2 | 58.4 |
| Get max of Elo rating | 0.115 | 22.4 | 29.8 |
| Get min of Elo rating | 0.292 | 11.4 | 27.2 |
| Find data correlation | 5.03 | 9.5 | 125.0 |
| Solving Question 1 | 1.07e-5 | 1.24e-5 | 9.78e-6 |
| Solving Question 2 | 11.8 | 23.0 | 2.15 |
| Solving Question 3 | 4.69 | 16.5 | 0.374 |
| Solving Question 4 | 1.86e-5 | 1.05e-5 | 1.41e-5 |
| Solving Question 5 | 0.0906 | 42.5 | 3.09 |

  ## Conclusion
  * To summarize, **Vaex** is the best in data preparation and cleaning. However, it performed the worst in sorting the data.
  * When performing Exploratory Data Analysis (EDA) with this dataset, **Pandas** is the fastest option rather than using Vaex and Koalas.
  * For most of solving the research questions, we prefer **Koalas** more as it is the fastest library.
  * Therefore, for large dataset, we suggest to use **Vaex** for cleaning data, **Pandas** when performing EDA, and **Koalas** to do more complex task. As there are no library that are the best (have the shortest time), thus we need to choose the library properly in performing each task as mentioned above to utilize the pros of each of the library as the alternatives of pandas.
