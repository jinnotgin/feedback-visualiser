<script>
  export let data;
</script>

<ul class="text-response-list flex flex-col gap-2">
  {#if data.responses.length > 0}
  <div class="text-xs mt-2 mb-2">{data.responses.length} response<span class={data.responses.length > 1  ? "" : "hidden"}>s</span></div>
  {:else}
  <div>There are no responses to this question.</div>
  {/if}
  {#each data.responses as response, index}
    <li class="bg-gray-50 p-3 rounded-lg text-sm border-2 border-gray-100 whitespace-pre-line">{response}</li>
  {/each}
</ul>