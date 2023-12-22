<!-- SurveyContainer.svelte -->
<script>
	import SurveyCategory from "#lib/SurveyCategory.svelte";

	// Your survey data
	export let surveyData;
</script>

<h1 class="text-xl mb-4 font-semibold">
	Feedback for {surveyData.name} ({surveyData.period})
</h1>
{#each surveyData.categories as category}
	<SurveyCategory {category} name={surveyData.name} />
{/each}

<svelte:head>
	<title>{surveyData.name} {surveyData.period}: Feedback Visualiser</title>
</svelte:head>
