<script>
  import { onMount } from 'svelte'

  let opac = 0
  $: arrowOpac = opac

  let divs = [
    {name: '.tex', anime: 'tex--animation'},
    {name: '.marsh', anime: 'marsh--animation'},
    {name: '.august', anime: 'august--animation'},
    {name: '.watling', anime: 'watling--animation'},
    {name: '.twotears', anime: 'twotears--animation'},
    {name: '.jimmy', anime: 'jimmy--animation'},
    {name: '.haystack', anime: 'haystack--animation'},
    {name: '.red1', anime: 'red1--animation'},
    {name: '.red2', anime: 'red2--animation'},
    {name: '.red3', anime: 'red3--animation'},
    {name: '.red4', anime: 'red4--animation'}
  ]

  onMount(() => {
    const options = {
      root: null,
      thresholds: 0.75,
      rootMargin: '0px'
    }

    const lines = document.querySelector('.tex')

    const observer = new IntersectionObserver((entries, observer) => {
      entries.forEach(entry => {
        if (entry.isIntersecting) {
          
          setTimeout(() => {
            for (let i = 0; i < divs.length; i++) {
              console.log(divs[i].name)
              document.querySelector(divs[i].name).classList.add(divs[i].anime)
            }
          }, 1000)

          setTimeout(() => {
            opac = 1
          }, 6000)
        }
      })
    }, options)
      
    observer.observe(lines)
    
  })

</script>

<style>

  .content {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
  }

  .holder {
    position: relative;
    color: white;
    margin: 0;
    width: max-content;
    font-family: 'Raleway', serif;
    font-weight: 100;
    padding: 10px 0px;
    left: 50%;
    transform: translateX(-50%);
    text-transform: uppercase;
  }

  .holder p {
    opacity: 0;
  }
  

  .tex {
    font-size: 2.3rem;
  }
  .marsh {
    font-size: 1.9rem;
    padding-top: .6rem;
    border-top: 1px solid white;
  }
  .august {
    font-size: 1.6rem;
    padding-top: .6rem;
    border-top: 1px solid white;
  }
  .watling {
    font-size: 1.5rem;
    padding-top: .6rem;
    border-top: 1px solid white;
  }
  .twotears {
    font-size: 1.3rem;
    padding-top: .6rem;
    border-top: 1px solid white;
  }
  .jimmy {
    font-size: 1.2rem;
    padding-top: .6rem;
    border-top: 1px solid white;
  }
  .haystack {
    font-size: 1.4rem;
    padding-top: .6rem;
    border-top: 1px solid white;
  }
  .red {
    font-size: 1.2rem;
    padding-top: .6rem;
    border-top: 1px solid white;
  }
  .red1, .red2, .red3, .red4 {
    color: white;
  }

  @media only screen and (max-width: 600px) {
    .content {
      padding-top: 28px;
    }
    .holder p {
      margin-top: -.8rem;
    }
    .tex {
      font-size: 1.4rem;
    }
    .marsh {
      font-size: 1rem;
      padding-top: .3rem;
      border-top: 1px solid white;
    }
    .august {
      font-size: .9rem;
      padding-top: .3rem;
      border-top: 1px solid white;
    }
    .watling {
      font-size: .75rem;
      padding-top: .3rem;
      border-top: 1px solid white;
    }
    .twotears {
      font-size: .7rem;
      padding-top: .3rem;
      border-top: 1px solid white;
    }
    .jimmy {
      font-size: .6rem;
      padding-top: .3rem;
      border-top: 1px solid white;
    }
    .haystack {
      font-size: .7rem;
      padding-top: .3rem;
      border-top: 1px solid white;
    }
    .red {
      font-size: .6rem;
      padding-top: .3rem;
      border-top: 1px solid white;
    }
  }

  @media only screen and (min-width: 601px) and (max-width: 920px) and (orientation: landscape) {
    .content {
      padding-top: 20px;
    }
    .holder p {
      margin-top: -1rem;
    }
    .tex {
      font-size: 1.4rem;
    }
    .marsh {
      font-size: 1rem;
      padding-top: .3rem;
      border-top: 1px solid white;
    }
    .august {
      font-size: .9rem;
      padding-top: .3rem;
      border-top: 1px solid white;
    }
    .watling {
      font-size: .75rem;
      padding-top: .3rem;
      border-top: 1px solid white;
    }
    .twotears {
      font-size: .7rem;
      padding-top: .3rem;
      border-top: 1px solid white;
    }
    .jimmy {
      font-size: .6rem;
      padding-top: .3rem;
      border-top: 1px solid white;
    }
    .haystack {
      font-size: .7rem;
      padding-top: .3rem;
      border-top: 1px solid white;
    }
    .red {
      font-size: .6rem;
      padding-top: .3rem;
      border-top: 1px solid white;
    }
  }
</style>

<div class="content">
  <div class="holder">
    <p class="tex">Tex Perkins & Matt Walker</p>
  </div>
  <div class="holder">
    <p class="marsh">Marshall Okell &nbsp;&#8226;&nbsp; Col Finley</p>
  </div>
  <div class="holder">
    <p class="august">August river band &nbsp;&#8226;&nbsp; jase lansky</p>
  </div>
  <div class="holder">
    <p class="watling">watling & bates &nbsp;&#8226;&nbsp; mermaid avenue</p>
  </div>
  <div class="holder">
    <p class="twotears">two tears in a bucket &nbsp;&#8226;&nbsp; georgia grae</p>
  </div>
  <div class="holder">
    <p class="jimmy">jimmy willing & the real gone hick-ups</p>
  </div>
  <div class="holder">
    <p class="haystack">haystack mountain hermits</p>
  </div>
  <div class="holder">
    <p class="red red1">red belly black &nbsp;&#8226;&nbsp; the sultans</p>
  </div>
  <div class="holder">
    <p class="red red2">kava groove &nbsp;&#8226;&nbsp; chris harry</p>
  </div>
  <div class="holder">
    <p class="red red3">gary barton &nbsp;&#8226;&nbsp; gravel axe</p>
  </div>
  <div class="holder">
    <p class="red red4">highly strung puppets</p>
  </div>
</div>



<div class="arrow" id="arrow" style="opacity: {arrowOpac}">
  <div class="arrow--animate">
    <div class="line"></div>
    <div class="arrow--head"></div>
    <small class="scroll">
      scroll...
    </small>
  </div>
</div>