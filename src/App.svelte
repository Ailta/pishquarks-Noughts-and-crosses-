<script>
  import svelteLogo from './assets/svelte.svg'
  import viteLogo from '/vite.svg'
  import Counter from './lib/Counter.svelte'
	
	let tile = ['', '', '', '', '', '', '', '', ''];
	
	let round = 0;
	function increment() {
		round += 1;
	}
	function clearTable() {
		tile = ['', '', '', '', '', '', '', '', ''];
	}
	
	let playerOne = '×';
	let playerTwo = '+';
	let playerOneWins = 0;
	let playerTwoWins = 0;
	
	function play(id) {
		console.log(id);
		if (round%2 == 0){
			tile[id] = '×';
		} else {
			tile[id] = '+';
		}
		increment();
		
		let count = [0, 0, 0, 0, 0, 0];
		for (let i = 0; i < 3; i++){
			/* (tile[0 + i] == '|' && tile[3 + i] == '|' && tile[6 + i] == '|'){
				console.log('babum');
			}*/
			
			
			// For x
			let x = i;
			if (tile[x] == '×'){
				count[0] -= -1;
			}
			if (tile[3+x] == '×'){
				count[1] -= -1;
			}
			if (tile[6+x] == '×'){
				count[2] -= -1;
			}
			
			// For +
			if (tile[x] == '+'){
				count[3] -= -1;
			}
			if (tile[3+x] == '+'){
				count[4] -= -1;
				console.log(0);
			}
			if (tile[6+x] == '+'){
				count[5] -= -1;
			}
			
			// For x
			let y = x*3;
			if (tile[y] == '×'){
				count[0] -= -1;
			}
			if (tile[1+y] == '×'){
				count[1] -= -1;
			}
			if (tile[2+y] == '×'){
				count[2] -= -1;
			}
			
			// For +
			if (tile[y] == '+'){
				count[3] -= -1;
			}
			if (tile[1+y] == '+'){
				count[4] -= -1;
				console.log(1);
			}
			if (tile[2+y] == '+'){
				count[5] -= -1;
			}
		}
		
		if (count[0] == 2 && count[1] == 2 && count[2] == 2 ||
			count[0] == 2 && count[1] == 2 && count[2] == 4 ||
			count[0] == 3 && count[1] == 2 && count[2] == 3 ||
			count[0] == 4 && count[1] == 2 && count[2] == 2){
			console.log('bumba');
		}
		
		if (count[3] == 4 && count[4] == 1 && count[5] == 1 ||
			count[3] == 1 && count[4] == 4 && count[5] == 1 ||
			count[3] == 1 && count[4] == 1 && count[5] == 4){
			console.log('babum');
		}
		
		console.log(count);
		
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
