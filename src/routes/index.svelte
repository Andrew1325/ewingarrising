<script>
  import Intro from '../components/Intro.svelte'
  import Second from '../components/Second.svelte'
  import Third from '../components/Third.svelte'
  import Fourth from '../components/Fourth.svelte'
  import Fifth from '../components/Fifth.svelte'
  import { onMount } from 'svelte'

  let oldScroll = 0
  let ind = 0
  let slides

  async function scrolling(){ 
      var st = window.pageYOffset || document.documentElement.scrollTop
      if (st > oldScroll) {
        if (ind === 4) {
          return
        }
        document.removeEventListener('scroll', scrolling);
        await setTimeout(function() {
          slides[ind].style.transform = 'translate(0%, -110%)'
          ind++
        }, 100)
        setTimeout(function() {
          slides[ind].style.transform = 'translate(0%, 0%)'
          slides[ind-1].style.opacity = '0'
          slides[ind-1].style.transform = 'translate(-110%, 0%)'
        }, 800)
        setTimeout(function() {
          slides[ind-1].style.opacity = '1'
          st = window.pageYOffset || document.documentElement.scrollTop
          oldScroll = st <= 0 ? 0 : st; // For Mobile or negative scrolling
          document.addEventListener('scroll', scrolling);
        }, 2500)
        
      } else {
        if (ind === 0) {
          return
        }
        document.removeEventListener('scroll', scrolling);
        await setTimeout(function() {
          slides[ind].style.transform = 'translate(0%, 110%)'
          ind--
        }, 100)
        setTimeout(function() {
          slides[ind].style.transform = 'translate(0%, 0%)'
          slides[ind+1].style.opacity = '0'
          slides[ind+1].style.transform = 'translate(-110%, 0%)' 
        }, 800)
        setTimeout(function() {
          slides[ind+1].style.opacity = '1'
          st = window.pageYOffset || document.documentElement.scrollTop
          oldScroll = st <= 0 ? 0 : st; // For Mobile or negative scrolling
          document.addEventListener('scroll', scrolling);
        }, 2500)
      } 
    }
  
  onMount(() => {
    window.scrollTo(0, 20000)
    slides = [
      document.querySelector('#start'),
      document.querySelector('#one'),
      document.querySelector('#two'),
      document.querySelector('#three'),
      document.querySelector('#four')
    ]
    
    setTimeout(function() {
      slides[ind].style.transform = 'translateX(0px)'
    }, 500)
    
    setTimeout(function() {
      document.addEventListener("scroll", scrolling);
    }, 2500)
  })
</script>

<style>
  .all {
    position: relative;
    height: 10000vh;
  }
  .absy {
    position: fixed;
    height: 102vh;
    width: 100vw;
    top: 0;
    background-color: rgba(0, 0, 255, 0);
    z-index: 12;
  }
  .slidey {
    width: 100%;
    height: 100%;
    transform: translate(-110%, 0%);
    box-shadow: 10px 0px 30px black;
    transition: transform .6s 0s ease;
    opacity: 1;
  }
  #start {
    background-color: black;
  }
  #one {
    background-color: black;
  }
  #two {
    background-color: black;
  }
  #three {
    background-color: black;
  }
  #four {
    background-color: white;
  }
  .slidey--content {
    font-family: sans-serif;
    font-size: 4rem;
    text-align: center;
    letter-spacing: 1.2rem;
    color: blueviolet;
  }

</style>

<svelte:head>
	<title>Ewingar Rising</title>
</svelte:head>

<div class="all">
  <div class="absy">
    <div id="start" class="slidey">
      <Intro />
    </div>
  </div>
  <div class="absy">
    <div id="one" class="slidey">
      <Second />
    </div>
  </div>
  <div class="absy">
    <div id="two" class="slidey">
      <Third />
    </div>
  </div>
  <div class="absy">
    <div id="three" class="slidey">
      <Fourth />
    </div>
  </div>
  <div class="absy">
    <div id="four" class="slidey">
      <Fifth />
    </div>
  </div>    
</div>
