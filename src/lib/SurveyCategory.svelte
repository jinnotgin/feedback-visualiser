<script>
	import SurveyQuestion from "#lib/SurveyQuestion.svelte";

	export let category, name;
</script>

<div class="bg-white mb-6 rounded-lg border-2 border-gray-200">
	<h2 class="text-l bg-violet-800 text-white rounded-t-lg py-3 px-6">
		{category.name}
	</h2>
	<div class="p-6 pb-8 flex flex-col gap-6">
		{#each category.questions as question}
			<SurveyQuestion {question} {name} />
		{/each}
	</div>
</div>
