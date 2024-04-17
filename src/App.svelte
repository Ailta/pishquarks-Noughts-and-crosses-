<script>
  import svelteLogo from './assets/svelte.svg'
  import viteLogo from '/vite.svg'
  import Counter from './lib/Counter.svelte'

  let kruh = 'O';
  let kriz = 'X';
  
	let round = 0;
	function increment() {
		round += 1;
	}
</script>

<main>
<h1>Piškvorec</h1>
<table>
  <tr>
    <td>{kruh}</td>
    <td>{kriz}</td>
    <td>{kriz}</td>
  </tr>
  <tr>
    <td>{kriz}</td>
    <td>{kriz}</td>
    <td>{kriz}</td>
  </tr>
  <tr>
    <td>{kriz}</td>
    <td>{kriz}</td>
    <td>{kriz}</td>
  </tr>
</table>
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
