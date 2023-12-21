<script>
import BarChartGraph from '#lib/QuestionType/BarChartGraph.svelte';
  import TextResponseList from '#lib/QuestionType/TextResponseList.svelte';
  
  export let question, name;

  const questionTitleWithName = question.data.title.replace("{name}",name)
</script>

<div class="">
  <h3 class="">{questionTitleWithName}</h3>
  {#if question.type === 'graph'}
    <BarChartGraph data={question.data} />
  {:else if question.type === 'text'}
    <TextResponseList data={question.data} />
  {/if}
</div>