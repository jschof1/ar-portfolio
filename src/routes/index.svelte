<script>
import Content from '$lib/components/Content.svelte';
import airtableJson from 'airtable-json'

const airtable = async () => {
  const animations = await airtableJson({
    auth_key: "keyCDhBnEvApVz4Z6", 
    base_name: "app6L8ES4FTPA0CWc", 
    primary: "tblFrCMA252fNNgpv", 
    view: "Grid view" 
  })
    let gifs = await animations.map((a)=>{
      return a.Gifs[0].url
    })
    $: console.log(gifs)
  return [gifs]
}
let animationPage = airtable()

</script>
{#await animationPage}
<p>...waiting</p>
{:then users}
	{#each animationPage as first}
  <p> hi </p>
    <div class="flex flex-wrap overflow-hidden sm:-mx-3">
      <div class="w-1/4 overflow-hidden sm:my-3 sm:px-3">
          <div id="img_wrap" class="static">
            <img id="animated" alt="static" src="">
            <img id="static" alt="gif" src="">
					</div>
			</div>
		</div>
    {/each}

{/await}
