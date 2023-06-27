<script>
	import ZONES from './Zones.json'

	let FireZones = ZONES.ZONES

	let input = ''

	let currentZone = []

	let disZone = ''

	let darkMode = true;


	let bgColor = '#222728'
	let color = 'white'
	let invert = '100'

	function findZone(){
		currentZone = FireZones.filter(z => {
			if (z.ZONE.length > 0) {
				return z.ZONE == input.toUpperCase()
			} else {
				return null
			}
		})

		disZone = currentZone[0]['ZONE']

		currentZone = currentZone[0]
		
		console.log(currentZone)	
	}

	function toggleDarkMode(){
		darkMode = !darkMode;

		if (darkMode == true){
			bgColor = '#222728'
			color = 'white'
			invert = '100'
		} else {
			bgColor = '#ffffff'
			color = 'black'
			invert = '0'
		}

	}

	
</script>





<main style='color: {color}; background-color: {bgColor};'>
	<div id='header'>

		<svg id="logo" data-name="Layer 1" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 1773.62 555.5"><defs><style>.cls-1{isolation:isolate;font-size:504.31px;font-family:FuturaPT-ExtraBold, Futura PT;font-weight:800;}.cls-1,.cls-2{fill:#ff3e00;}</style></defs><text class="cls-1" transform="translate(322.23 420.34)">FWFD</text><path class="cls-2" d="M253.48,255.82c-12.34-5.07-16.76-23.25-16-29.79.29-3,.74-5.28,0-6.13-2.88-3.38-9.05,4.28-13.74,10.94L202.87,258l-1.23,1.56a51.5,51.5,0,0,0-10.45,41.85c4.65,22.71,30.39,39,54,34.13s43.32-23.18,38.7-45.88C280.43,272.75,271.42,263.21,253.48,255.82Z" transform="translate(-84.14 2.28)"/><path class="cls-2" d="M322.94,90.07a553.6,553.6,0,0,0-173.51,0L84.14,102.24V229.45c0,101.72,43.41,193.26,140.89,222.31l11.16,3.33,11.15-3.33c97.5-29.05,139.54-118.67,139.54-220.39V104.13ZM334.2,282.79c0,49.32-46.71,94.23-98,94.23s-98-44.91-98-94.23c0-36.65,22-61.53,39.63-81.5,18.79-21.27,32.08-42.54,27.72-55.86-1.95-6-3.9-10.67-2.72-12.74,4.61-8.22,19.66,2.23,32.41,14.05,20.83,19.35,32.17,45.24,32.34,82.38a5.28,5.28,0,0,0,4.21,5.32,5,5,0,0,0,.86.08,5.09,5.09,0,0,0,5.09-5.09c0-.12.14-1.34.14-2.08,0-3.65.72-25.37,1.74-27.51a7.62,7.62,0,0,1,11.68-2.52l3.23,2.63c24.85,20.66,39.68,51.62,39.68,82.76Z" transform="translate(-84.14 2.28)"/></svg>
		
		<input type="text" bind:value={input} on:input={findZone} placeholder="ZONE (ex:S0100)">

		<h3>{disZone}</h3>
		<div id="colorkey">
			<h5 class="sevenofour">704 Engine</h5>
			<h5 class="sevenofive">705 Engine</h5>
			<h5 class="sevenosix">706 Engines</h5>
		</div>
		
	</div>
	
	{#if currentZone['1E'] !== undefined}
		<div id='output'>
			<div class='units'>
				<h4>ENGINES</h4>
				<ol>
					<li>ENGINE: {currentZone['1E']}</li>
					<li>ENGINE: {currentZone['2E']}</li>
					<li>ENGINE: {currentZone['3E']}</li>
					<li class="fourth">ENGINE: {currentZone['4E']}</li>
					<li class="fifth">ENGINE: {currentZone['5E']}</li>
					<li class="seventh">ENGINE: {currentZone['6E']}</li>
					<li class="seventh">ENGINE: {currentZone['7E']}</li>
					<li>ENGINE: {currentZone['8E']}</li>
					<li>ENGINE: {currentZone['9E']}</li>
				</ol>
			</div>
			
			<div class='units'>
				<h4>TRUCKS</h4>
				<ol>
					<li>TRUCK: {currentZone['1T']}</li>
					<li>TRUCK: {currentZone['2T']}</li>
					<li>TRUCK: {currentZone['3T']}</li>
					<li>TRUCK: {currentZone['4T']}</li>
				</ol>
			</div>

			<div class='units'>
				<h4>BATALLION</h4>
				<ol>
					<li>BATALLION: {currentZone['1BC']}</li>
					<li>BATALLION: {currentZone['2BC']}</li>
					<li>BATALLION: {currentZone['3BC']}</li>
					<li>BATALLION: {currentZone['4BC']}</li>
				</ol>
			</div>

			<div class='units'>
				<h4>LUCAS TOOL</h4>
				<ol>
					<li>ENGINE: {currentZone['1HE']}</li>
					<li>ENGINE: {currentZone['2HE']}</li>
					<li>ENGINE: {currentZone['3HE']}</li>
					{#if currentZone['4HE'] != undefined}
						<li>ENGINE: {currentZone['4HE']}</li>
					{/if}
				</ol>
			</div>

			<div class='units'>
				<h4>RAFT</h4>
				<ol>
					<li>ENGINE: {currentZone['1RT']}</li>
					<li>ENGINE: {currentZone['2RT']}</li>
					<li>ENGINE: {currentZone['3RT']}</li>
				</ol>
			</div>

		</div>
	{/if}

	<button id='footer' style="filter: invert({invert}%);" on:click={toggleDarkMode}>
		<svg id="toggleDark" data-name="Layer 1" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 442.14 442.14"><path d="M489.31,428.43A204.75,204.75,0,0,1,284.54,223.66,202.33,202.33,0,0,1,312.6,121.92,225.38,225.38,0,1,0,591.1,400.4a203.3,203.3,0,0,1-101.79,28Z" transform="translate(-148.96 -121.92)"/></svg>
	</button>

</main>






<style>
	@import url('https://fonts.googleapis.com/css2?family=Braah+One&family=Open+Sans:wght@500;800&display=swap');
	main {
		/* text-align: center; */
		padding: 0;
		width: 100%;
		height:100%;
		margin: 0 0;
		display: flex;
		flex-direction: column;
		justify-content: flex-start;
		flex-basis: auto;
		font-family: 'Open Sans', sans-serif;
	}
	
	#logo{
		max-height: 80px;
		margin: 0 auto;
	}
	#header{
		display: flex;
		flex-direction: column;
		justify-content: center;
	}
	#colorkey{
		display: flex;
		flex-direction: row;
		justify-content: center;
	
	}

	.sevenofour{
		padding: 0 20px;
		color: #c2a008;
		font-size: 18px;
	}
	.sevenofive{
		padding: 0 20px;
		color: #f74f17;
		font-size: 18px;
	}
	.sevenosix{
		padding: 0 20px;
		color: #ff0000;
		font-size: 18px;
	}

	input{
		max-width: 30%;
		margin: 20px auto;
	}

	

	/* h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 400;
		text-align: center;
	} */

	h3 {
		color: #ff3e00;
		font-family: 'Open Sans', sans-serif;
		text-transform: uppercase;
		font-size: 2em;
		font-weight: 500;
		text-align: center;
		margin-bottom: 5px;
	}

	#output{
		max-width: 80%;
		margin: 0 auto;
		display: flex;
		flex-direction: row;
		justify-content: center;
	}

	.fourth{
		color: #c2a008;
	}
	.fifth{
		color: #f74f17;
	}
	.seventh{
		color: #ff0000;
	}
	.units{
		padding: 0 25px 0 25px;
		font-weight: 400;
	}

	ol{
		padding: 0;
	}

	#footer{
		margin: 0 auto;
		display: flex;
		flex-direction: row;
		justify-content: center;
		width: 30px;
		background: none;
		border: none;
		outline: none;
		justify-self: flex-end;
	}

	#toggleDark{
		max-height: 25px;
		margin: 0 auto;
		justify-self: center;
	}
	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>