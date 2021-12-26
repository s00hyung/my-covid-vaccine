<script>
    import { onMount } from "svelte";
    import Chart from "chart.js";

    export let doses = [];

    function stringToDate(dateInString) {
        // 2021-12-12
        var year = dateInString.substring(0, 4);
        var month = dateInString.substring(5, 7);
        var day = dateInString.substring(8, 10);
        return new Date(year, month - 1, day);
    }

    let datasets = [
        {
            label: "My First dataset",
            backgroundColor: "rgb(255, 99, 132)",
            borderColor: "rgb(255, 99, 132)",
            data: [{ x: 10, y: 10 }],
        },
    ];

    onMount(async () => {
        var ctx = document.getElementById("myChart").getContext("2d");
        var chart = new Chart(ctx, {
            type: "line",
            data: {
                datasets: datasets,
            },
            options: {},
        });
    });
</script>

<canvas id="myChart" />
<button class="button is-success is-light is-fullwidth">Compute</button>
