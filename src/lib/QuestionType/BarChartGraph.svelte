<script>
	import ApexCharts from "apexcharts";
	export let data;

	let barChartRef;

	let options = {
		chart: {
			type: "bar",
			height: 250,
		},
		fill:{
			colors: [], // will be updated by chart function
		},
		tooltip: {
			enabled: false,
		},
		series: [
			{
				data: data.responses,
			},
		],
		xaxis: {
			categories: data.labels,
		},
	};

	function chart(node) {
		const computedColor = getComputedStyle(node).color;
		options.fill.colors = [computedColor];
		const chart = new ApexCharts(node, options);
		chart.render();

		return {
			destroy() {
				chart.destroy();
			},
		};
	}
</script>

<div class="text-teal-800" use:chart></div>
