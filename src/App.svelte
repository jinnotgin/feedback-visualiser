
<script>
  import SurveyContainer from './lib/SurveyContainer.svelte';
  import defaultData from '#assets/data.json';

  let data = defaultData; // Initialize data variable with default data

  async function getFileData(file) {
    try {
      let response = await fetch(URL.createObjectURL(file)); // URL.createObjectURL creates a blob url from the file object
      return await response.json(); // Get the JSON content of the file
    } catch (err) {
      console.error('Error:', err);
    }
  };

  function handleDragOver(event){
    event.preventDefault();
    event.dataTransfer.dropEffect = 'move';
  };

  async function handleDrop(event) {
    event.preventDefault();

    // Get the file that was dropped
    let file = event.dataTransfer.files[0];

    if(file && file.name.endsWith('.json')){
      const fileData = await getFileData(file);
      // ValidateData before updating the data variable
      if (fileData && fileData.name && fileData.period && fileData.categories) {
        data = fileData;
      } else {
        console.error('Invalid JSON file');
      }
    }
  };
</script>

<div
	role="button"
	tabindex="0"
	on:dragover={handleDragOver}
	on:drop={handleDrop}
	on:dragleave={handleDragLeave}
	class="fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center text-white text-4xl z-10 transition-all duration-300 pointer-events-none' {isDragOver
		? ''
		: 'hidden'}"
>
	Drop your file here
</div>

<main
	class="max-w-screen-md mx-auto my-6 relative"
	on:dragover={handleDragOver}
>
	<SurveyContainer surveyData={data} />
</main>
