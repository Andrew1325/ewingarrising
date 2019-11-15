<script>
import Arrow from './Arrow.svelte'
import { onMount } from 'svelte'

	let visible = false;
  let second = false
  
  onMount(() => {
      let arrowDiv = document.querySelector('#arrow')
      
      setTimeout(function() {
        visible = true
      }, 1200)

      setTimeout(() => {
        arrowDiv.style.opacity = '1'
      }, 26000)
    }
  )

	function typewriter(node, { speed = 65 }) {
		const valid = (
			node.childNodes.length === 1 &&
			node.childNodes[0].nodeType === 3
		)
		
		if (!valid) {
			throw new Error(`This transition only works on elements with a single text node child`)
		}
		
		const text = node.textContent
		const duration = text.length * speed

		return {
			duration,
			tick: t => {
				const i = ~~(text.length * t)
				node.textContent = text.slice(0, i)
				if (i === text.length - 1) {
					setTimeout(() => {
						second = true 
					}, 2000);
				}
			}
		};
	}
</script>

<style>
  p {
    color: white;
    margin: 0;
    font-family: 'Roboto Slab', serif;
    font-weight: 100;
    font-size: 1.9rem;
    text-align: center;
    padding: 0 15%;
  }
  .container {
    width: 100vw;
    position: relative;
    top: 20%;
  }

  @media only screen and (max-width: 600px) {
    p {
      font-size: 1.1rem;
    }
    .container {
      top: 16%;
    }
  }

  @media only screen and (min-width: 601px) and (max-width: 920px) {
    p {
      font-size: 1.1rem;
    }
    .container {
      top: 12%;
    }
  }
  
</style>
<div class="container">
  {#if visible}
    <p in:typewriter>
      In September, October and November 2019 the community of Ewingar was devestated by a series of out of control bushfires that destroyed numerous homes, other structures, countless animals and miles of fencing.
    </p>
  {/if}
  <br><br>
  {#if second}
    <p in:typewriter>
      The people of Ewingar were knocked down. But with a unity unique to this community, efforts began to lift up the worst affected, lift up the whole community.
    </p>
  {/if}
</div>
<div class="arrow" id="arrow">
  <div class="arrow--animate">
    <div class="line"></div>
    <div class="arrow--head"></div>
    <small class="scroll">
      scroll...
    </small>
  </div>
</div>
