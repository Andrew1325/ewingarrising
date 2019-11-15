<script>
  import { onMount } from 'svelte'

  export let delay

  onMount (() => {
    let arrowDiv = document.querySelector('#arrow')

    if (delay !== undefined) {
      console.log('onMount delay '+delay)
        setTimeout(() => {
        arrowDiv.style.opacity = '1'
      }, delay)
    }
  })
</script>

<style>
  .arrow {
    position: absolute;
    bottom: -40px;
    left: 50%;
    transform: translate(-50%, -50%) scale(.5);
    height: 6rem;
    width: 4rem;
    opacity: 0;
  }
  .arrow--animate {
    position: relative;
    -webkit-animation-name: bounceInDown;
    animation-name: bounceInDown;
    -webkit-animation-duration: 1.5s;
    animation-duration: 1.5s;
    animation-delay: 2s;
    -webkit-animation-delay: 2s;
    animation-iteration-count: infinite;
    -webkit-animation-fill-mode: both;
    animation-fill-mode: both;
  }
  @-webkit-keyframes bounceInDown {
    0%, 30%, 45%, 50%, 60% {
      -webkit-transition-timing-function: cubic-bezier(0.215, 0.610, 0.355, 1.000);
      transition-timing-function: cubic-bezier(0.215, 0.610, 0.355, 1.000);
    }
  
    0% {
      opacity: 1;
      -webkit-transform: translate3d(0, -30px, 0);
      transform: translate3d(0, -30px, 0);
    }
  
    30% {
      opacity: 1;
      -webkit-transform: translate3d(0, 25px, 0);
      transform: translate3d(0, 25px, 0);
    }
  
  45% {
    -webkit-transform: translate3d(0, -10px, 0);
    transform: translate3d(0, -10px, 0);
  }
  
  50% {
    -webkit-transform: translate3d(0, 5px, 0);
    transform: translate3d(0, 5px, 0);
  }
  
    60% {
      -webkit-transform: none;
      transform: none;
    }
  }
  
  @keyframes bounceInDown {
    0%, 30%, 45%, 50%, 60% {
      -webkit-transition-timing-function: cubic-bezier(0.215, 0.610, 0.355, 1.000);
      transition-timing-function: cubic-bezier(0.215, 0.610, 0.355, 1.000);
    }
  
    0% {
      opacity: 1;
      -webkit-transform: translate3d(0, -30px, 0);
      transform: translate3d(0, -30px, 0);
    }
  
    30% {
      opacity: 1;
      -webkit-transform: translate3d(0, 25px, 0);
      transform: translate3d(0, 25px, 0);
    }
  
    45% {
      -webkit-transform: translate3d(0, -10px, 0);
      transform: translate3d(0, -10px, 0);
    }
  
    50% {
      -webkit-transform: translate3d(0, 5px, 0);
      transform: translate3d(0, 5px, 0);
    }
  
    60% {
      -webkit-transform: none;
      transform: none;
    }
  } 
  .line {
    position: absolute;
    top: 30%;
    left: 50%;
    transform: translate(-25%, -50%);
    height: 1.4rem;
    width: 1px;
    border-left: 1px solid white;
  }
  .arrow--head {
    position: absolute;
    top: 20%;
    left: 50%;
    transform: translate(-50%, -50%);
    height: 1rem;
    width: 1rem;
    border-right: 1px solid white;
    border-bottom: 1px solid white;
    transform: rotate(45deg);
    transform-origin: top left;
  }

  .scroll {
    font-size: .9rem;
    text-align: center;
    position: absolute;
    top: 75%;
    left: 50%;
    transform: translate(-50%, 240%);
    color: white;
    font-family: 'Roboto Slab', serif;
  }

  @media only screen and (min-width: 601px) and (max-width: 920px) {
    .arrow {
      bottom: 2.5%;
      transform: scale(.5);
    }
  }
</style>

<div class="arrow" id="arrow">
  <div class="arrow--animate">
    <div class="line"></div>
    <div class="arrow--head"></div>
    <small class="scroll">
      scroll...
    </small>
  </div>
</div>