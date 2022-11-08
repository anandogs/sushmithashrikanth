<script lang="ts">
import '@splidejs/svelte-splide/css/sea-green';
import image1 from '../images/slideshow/1.png';
import image2 from '../images/slideshow/2.png';
import image3 from '../images/slideshow/3.png';
import image4 from '../images/slideshow/4.png';
import image5 from '../images/slideshow/5.png';
import image6 from '../images/slideshow/6.png';
import image7 from '../images/slideshow/7.png';
import image8 from '../images/slideshow/8.png';
const imageList = [image1, image2, image3, image4, image5, image6, image7, image8];

import { Splide, SplideSlide } from '@splidejs/svelte-splide';
  import { onMount } from 'svelte';
let showArrows = true

onMount(() => {
  let windowWidth = window.innerWidth;
  if (windowWidth < 768) {
    showArrows = false
  }
});

</script>

<section class="w-screen">
    <div class="md:w-[80%] w-full md:m-auto">
    <Splide options={{arrows: showArrows, autoplay:true, interval:4000, rewind:true,}} aria-label="Carousel Images">
      
      {#each imageList as image}
            
        <SplideSlide>
                <!-- svelte-ignore a11y-img-redundant-alt -->
                <img src={image} alt="Carousel Image"/>
            </SplideSlide>
        {/each}
      
    </Splide>
      
    </div>

  </section>