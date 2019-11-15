<script>
  import { onMount } from 'svelte'

  let opac = 0

  $: arrowOpac = opac

  onMount(() => {
    const options = {
      root: null,
      thresholds: 0.75,
      rootMargin: '0px'
    }

    const lines = document.querySelectorAll('.lines')

    const observer = new IntersectionObserver((entries, observer) => {
      entries.forEach(entry => {
        if (entry.isIntersecting) {
          const logo = document.querySelector('.logo')
          const title = document.querySelector('.thisis')
          const content = document.querySelector('.content')
          console.log(entry.target.classList[1])
          entry.target.classList.add(`${entry.target.classList[1]}--animation`)
          logo.classList.add('logo--animation')
          title.classList.add('thisis--animation')
          content.classList.add('content--animation')

          setTimeout(() => {
            opac = 1
          }, 6000)
        }
      })
    }, options)
    lines.forEach(section => {
      observer.observe(section)
    })
    
  })
</script>

<style>
  .thisis {
    font-size: 2.6rem;
    position: absolute;
    top: 12%;
    left: 50%;
    transform: translate(-50%, -50%);
    opacity: 0;
    padding: 12px 8px;
  }
  .thisis--animation {
    -webkit-animation-name: logoin;
    animation-name: logoin;
    -webkit-animation-duration: 1.8s;
    animation-duration: 1.8s;
    animation-delay: 1s;
    -webkit-animation-delay: 1s;
    animation-iteration-count: 1;
    -webkit-animation-fill-mode: forwards;
    animation-fill-mode: forwards;
  }

  .content {
    position: absolute;
    top: 78%;
    left: 50%;
    width: 90vw;
    transform: translate(-50%, -50%);
    opacity: 0;
  }
  .content--animation {
    -webkit-animation-name: logoin;
    animation-name: logoin;
    -webkit-animation-duration: .9s;
    animation-duration: .9s;
    animation-delay: 4.4s;
    -webkit-animation-delay: 4.4s;
    animation-iteration-count: 1;
    -webkit-animation-fill-mode: forwards;
    animation-fill-mode: forwards;
  }

  p {
    color: white;
    margin: 0;
    font-family: 'Roboto Slab', serif;
    font-weight: 100;
    font-size: 1.9rem;
    text-align: center;
    padding: 0 15%;
  }

  .logo {
    position: absolute;
    top: 40%;
    left: 50%;
    transform: translate(-50%, -50%);
    opacity: 0;
  }
  .logo--animation {
    -webkit-animation-name: logoin;
    animation-name: logoin;
    -webkit-animation-duration: 2.8s;
    animation-duration: 2.8s;
    animation-delay: 3.2s;
    -webkit-animation-delay: 3.2s;
    animation-iteration-count: 1;
    -webkit-animation-fill-mode: forwards;
    animation-fill-mode: forwards;
  }

  .lines {
    position: absolute;
    background-color: white;
    opacity: 0;
  }

  .left {
    top: 2vh;
    left: 2vh;
    width: 1px;
    height: 1px;
  }
  .left--animation {
    -webkit-animation-name: leftborder;
    animation-name: leftborder;
    -webkit-animation-duration: .9s;
    animation-duration: .9s;
    animation-delay: 1s;
    -webkit-animation-delay: 1s;
    animation-iteration-count: 1;
    -webkit-animation-fill-mode: forwards;
    animation-fill-mode: forwards;
  }

  .bottom {
    top: 98vh;
    left: 2vh;
    width: 1px;
    height: 1px;
  }
  .bottom--animation {
    -webkit-animation-name: bottomborder;
    animation-name: bottomborder;
    -webkit-animation-duration: .9s;
    animation-duration: .9s;
    animation-delay: 1.9s;
    -webkit-animation-delay: 1.9s;
    animation-iteration-count: 1;
    -webkit-animation-fill-mode: forwards;
    animation-fill-mode: forwards;
  }

  .right {
    bottom: 4vh;
    right: 2vh;
    width: 1px;
    height: 1px;
  }
  .right--animation {
    -webkit-animation-name: rightborder;
    animation-name: rightborder;
    -webkit-animation-duration: .9s;
    animation-duration: .9s;
    animation-delay: 3.2s;
    -webkit-animation-delay: 3.2s;
    animation-iteration-count: 1;
    -webkit-animation-fill-mode: forwards;
    animation-fill-mode: forwards;
  }

  .top {
    top: 2vh;
    right: 2vh;
    width: 1px;
    height: 1px;
  }
  .top--animation {
    -webkit-animation-name: topborder;
    animation-name: topborder;
    -webkit-animation-duration: .9s;
    animation-duration: .9s;
    animation-delay: 4.1s;
    -webkit-animation-delay: 4.1s;
    animation-iteration-count: 1;
    -webkit-animation-fill-mode: forwards;
    animation-fill-mode: forwards;
  }

  .classUser {
    position: absolute;
    top: 0;
    left: 0;
    height: 0px;
    width: 0px;
    overflow: hidden;
    display: none;
  }

  @media only screen and (max-width: 600px) {
    .thisis {
      font-size: 1.6rem;
    }
    .content {
      font-size: 1.1rem;
    }
    .logo img{
      width: 60vw;
    }
  }

  @media only screen and (min-width: 601px) and (max-width: 920px) {
    .thisis {
      font-size: 1.6rem;
    }
    .content {
      font-size: 1.1rem;
    }
    .logo img{
      width: 20vw;
    }
  }

  @keyframes logoin {
    0% {
      opacity: 0;
    }
    100% {
      opacity: 1;
    }
  }

  @keyframes leftborder {
    0% {
      opacity: 0;
    }
    1% {
      opacity: 1;
      height: 1px;
    }
    100% {
      opacity: 1;
      height: 96vh;
    }
  }

  @keyframes bottomborder {
    0% {
      opacity: 0;
    }
    1% {
      opacity: 1;
      width: 1px;
    }
    100% {
      opacity: 1;
      width: calc(100vw - 4vh);
    }
  }

  @keyframes rightborder {
    0% {
      opacity: 0;
    }
    1% {
      opacity: 1;
      height: 1px;
    }
    100% {
      opacity: 1;
      height: 96vh;
    }
  }

  @keyframes topborder {
    0% {
      opacity: 0;
    }
    1% {
      opacity: 1;
      width: 1px;
    }
    100% {
      opacity: 1;
      width: calc(100vw - 4vh);
    }
  }

</style>

<p class="thisis">
  THIS IS...
</p>
<div class="logo">
  <img src="/logoRising.svg" alt="Ewingar Rising Logo">
</div>
<p class="content">
  Bushfire Benefit Concert 2019
  <br>
  <small>
    Local and interstate artists; Kids corner with dirtgirl, jumping castle, puppet show and more; Food; Licenced bar - no BYO; Markets; Camping.
  </small>
  <br>
  November 22 - 24 2019
</p>
<div class="lines left"></div>
<div class="lines bottom"></div>
<div class="lines right"></div>
<div class="lines top"></div>
<div class="classUser top--animation left--animation right--animation bottom--animation logo--animation thisis--animation content--animation"></div>

<div class="arrow" id="arrow" style="opacity: {arrowOpac}">
  <div class="arrow--animate">
    <div class="line"></div>
    <div class="arrow--head"></div>
    <small class="scroll">
      scroll...
    </small>
  </div>
</div>
