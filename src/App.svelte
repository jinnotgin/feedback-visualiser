
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

<main class="max-w-screen-md mx-auto my-6" on:dragover={handleDragOver} on:drop={handleDrop} >
  <SurveyContainer surveyData={data}/>
</main>
