<script>
  import svelteLogo from './assets/svelte.svg'
  import viteLogo from '/vite.svg'
  import Counter from './lib/Counter.svelte'
	
	let tile = ['', '', '', '', '', '', '', '', ''];
	let plus = [0, 0, 0, 0, 0, 0, 0, 0, 0];
	let krizek = [0, 0, 0, 0, 0, 0, 0, 0, 0];
	
	let round = 0;
	function increment() {
		round += 1;
	}
	function clearTable() {
		tile = ['', '', '', '', '', '', '', '', ''];
		plus = [0, 0, 0, 0, 0, 0, 0, 0, 0];
		krizek = [0, 0, 0, 0, 0, 0, 0, 0, 0];
	}
	
	let playerOne = '×';
	let playerTwo = '+';
	let playerOneWins = 0;
	let playerTwoWins = 0;
	
	function play(id) {
		if (tile[id] == ''){
			if (round%2 == 0){
				tile[id] = playerOne;
			} else {
				tile[id] = playerTwo;
			}
			increment();
		}
		
		for (let i = 0; i<9; i++){
			if (tile[i] == playerOne){
				krizek[i] = 1;
			}
			if (tile[i] == playerTwo){
				plus[i] = 1;
			}
		}
		if(plus[0] == 1 && plus[1] == 1 && plus[2] == 1){
			console.log("Vyhrál Plusák");
			playerOneWins += 1;
		}
		if(plus[3] == 1 && plus[4] == 1 && plus[5] == 1){
			console.log("Vyhrál Plusák");
			playerOneWins += 1;
		}
		if(plus[6] == 1 && plus[7] == 1 && plus[8] == 1){
			console.log("Vyhrál Plusák");
			playerOneWins += 1;
		}
		if(plus[0] == 1 && plus[3] == 1 && plus[6] == 1){
			console.log("Vyhrál Plusák");
			playerOneWins += 1;
		}
		if(plus[1] == 1 && plus[4] == 1 && plus[7] == 1){
			console.log("Vyhrál Plusák");
			playerOneWins += 1;
		}
		if(plus[2] == 1 && plus[5] == 1 && plus[8] == 1){
			console.log("Vyhrál Plusák");
			playerOneWins += 1;
		}

		if(krizek[0] == 1 && krizek[4] == 1 && krizek[8] == 1){
			console.log("Vyhrál Křížník");
			playerTwoWins += 1;
		}
		if(krizek[2] == 1 && krizek[4] == 1 && krizek[6] == 1){
			console.log("Vyhrál Křížník");
			playerTwoWins += 1;
		}
	}
	
</script>

<main>
<h1>Piškvorec</h1>
<p>Kriz & Langer edition<p>
<table>
  <tr>
    <td><button type="button" on:click={() => play(0)}>{tile[0]}</button></td>
    <td><button type="button" on:click={() => play(1)}>{tile[1]}</button></td>
    <td><button type="button" on:click={() => play(2)}>{tile[2]}</button></td>
  </tr>
  <tr>
    <td><button type="button" on:click={() => play(3)}>{tile[3]}</button></td>
    <td><button type="button" on:click={() => play(4)}>{tile[4]}</button></td>
    <td><button type="button" on:click={() => play(5)}>{tile[5]}</button></td>
  </tr>
  <tr>
    <td><button type="button" on:click={() => play(6)}>{tile[6]}</button></td>
    <td><button type="button" on:click={() => play(7)}>{tile[7]}</button></td>
    <td><button type="button" on:click={() => play(8)}>{tile[8]}</button></td>
  </tr>
</table>
<button type="button" on:click={() => clearTable()}>Clear Table</button>
<p>{playerOne} has won: {playerOneWins} times</p>
<p>{playerTwo} has won: {playerTwoWins} times</p>
<p>Player {playerOne}, can only win in diagonal.</p>
<p>Player {playerTwo}, can only win in horizontal and vertical.</p>
</main>

<style>
table{
  border-style: solid;
  border-collapse: collapse;
}
td{
  border-style: solid;
  width: 200px;
  height: 200px; 
}
</style>
