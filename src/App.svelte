<script>
	// export let name;
	import Doses from "./components/Doses.svelte";
	import Chart from "./components/Chart.svelte";

	let vaccineTypes = ["Pfizer-BioNTech", "Moderna", "J&J's Janssen"];

	let doses = [{ id: 0, type: vaccineTypes[0], date: "" }];
</script>

<div class="tabs is-centered">
	<ul>
		<li class="is-active"><a>Vaccinator</a></li>
	</ul>
</div>
<section class="section">
	<div class="columns is-centered">
		<div class="column is-half">
			<Doses bind:doses {vaccineTypes} />
		</div>
		<div class="column is-half">
			<Chart bind:doses />
		</div>
	</div>
</section>
