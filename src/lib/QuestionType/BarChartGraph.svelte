<script>
	import ApexCharts from "apexcharts";
	export let data;

	var options = {
		chart: {
			type: "bar",
			height: 250,
		},
		fill: {
			colors: ["#00544f"],
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
		const chart = new ApexCharts(node, options);
		chart.render();

		return {
			destroy() {
				chart.destroy();
			},
		};
	}
</script>

<div use:chart></div>
