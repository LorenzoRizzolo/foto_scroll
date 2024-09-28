<Page name="home">

  <!-- <div class="gallery">
    {#each photos as url}
      <img src={url} alt="Image" />
    {/each}
  </div> -->

  <PhotoBrowser 
    {photos} 
    {thumbs} 
    {swiper} 
    theme="dark" 
    type="page" 
    bind:this={standalone}   
  />

  <Block inset>
    <Button fill onClick={() => standalone.open()}>Open Collage</Button>
  </Block>

</Page>
<script>
  import {
    Page,
    Button,
    Block,
    PhotoBrowser
  } from 'framework7-svelte';

  let standalone;
  let photos = [];
  let thumbs = [];

  let swiper = {
    autoplay: {
      delay: 4000,
    },
    speed: 700,
    spaceBetween: 20
  }
  
  const imageModules = import.meta.glob('../../public/images/*');
  for (const path in imageModules) {
    imageModules[path]().then((mod) => {
      let el = {
        url: mod.default,
        caption: mod.default
      }
      photos.push(el)
      thumbs.push(el)
    });
  }

</script>