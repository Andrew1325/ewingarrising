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

    const lines = document.querySelectorAll('.border-top')

    const observer = new IntersectionObserver((entries, observer) => {
      entries.forEach(entry => {

        const content1 = document.querySelector('.content1')
        const content2 = document.querySelector('.content2')
        const content3 = document.querySelector('.content3')
        const borderT = document.querySelector('.border-top')
        const borderL = document.querySelector('.border-left')
        const borderR = document.querySelector('.border-right')
        const borderB = document.querySelector('.border-bottom')

        if (entry.isIntersecting) {

          borderT.classList.add('top-border--animation')
          borderB.classList.add('bottom-border--animation')
          borderL.classList.add('left-border--animation')
          borderR.classList.add('right-border--animation')
          content1.classList.add('content1--animation')
          content2.classList.add('content2--animation')
          content3.classList.add('content3--animation')

          setTimeout(() => {
            opac = 1
          }, 6000)
        } else {
          borderT.classList.remove('top-border--animation')
          borderB.classList.remove('bottom-border--animation')
          borderL.classList.remove('left-border--animation')
          borderR.classList.remove('right-border--animation')
        }
      })
    }, options)
    lines.forEach(section => {
      observer.observe(section)
    })
    
  })
</script>

<style>
  

  .content1 {
    position: absolute;
    top: 13%;
    left: 22%;
    transform: translateX(-500%);
    opacity: 0;
  }
  .content1--animation {
    -webkit-animation-name: content1in;
    animation-name: content1in;
    -webkit-animation-duration: .9s;
    animation-duration: .9s;
    animation-delay: 1.8s;
    -webkit-animation-delay: 1.8s;
    animation-iteration-count: 1;
    -webkit-animation-fill-mode: forwards;
    animation-fill-mode: forwards;
  }

  .content2 {
    position: absolute;
    top: 50%;
    right: 22%;
    transform: translate(500%, -50%);
    opacity: 0;
  }
  .content2--animation {
    -webkit-animation-name: content2in;
    animation-name: content2in;
    -webkit-animation-duration: .9s;
    animation-duration: .9s;
    animation-delay: 3.4s;
    -webkit-animation-delay: 3.4s;
    animation-iteration-count: 1;
    -webkit-animation-fill-mode: forwards;
    animation-fill-mode: forwards;
  }

  .content3 {
    position: absolute;
    bottom: 13%;
    left: 22%;
    transform: translateX(-500%);
    opacity: 0;
  }
  .content3--animation {
    -webkit-animation-name: content1in;
    animation-name: content1in;
    -webkit-animation-duration: .9s;
    animation-duration: .9s;
    animation-delay: 5.2s;
    -webkit-animation-delay: 5.2s;
    animation-iteration-count: 1;
    -webkit-animation-fill-mode: forwards;
    animation-fill-mode: forwards;
  }

  p {
    color: white;
    margin: 0;
    font-family: 'Roboto Slab', serif;
    font-weight: 100;
    font-size: 1.4rem;
    text-align: center;
    padding: 0 15%;
  }

  .logo {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    opacity: 0.15;
  }

  .logo img{
      width: 60vw;
    }

  .border-top {
    position: absolute;
    top: 0%;
    left: 50%;
    transform: translateY(0%) scaleX(1) scaleY(1);
    height: 1px;
    width: 1px;
    background-color: rgba(230, 112, 17);
  }
  .border-left {
    position: absolute;
    top: 50%;
    left: 0%;
    transform: translateX(0%) scaleX(1) scaleY(1);
    height: 1px;
    width: 1px;
    background-color: rgba(230, 112, 17);
  }
  .border-right {
    position: absolute;
    top: 50%;
    right: 0%;
    transform: translateX(0%) scaleX(1) scaleY(1);
    height: 1px;
    width: 1px;
    background-color: rgba(230, 112, 17);
  }
  .border-bottom {
    position: absolute;
    bottom: 7px;
    left: 50%;
    transform: translateY(0%) scaleX(1) scaleY(1);
    height: 1px;
    width: 1px;
    background-color: rgba(230, 112, 17);
  }

  .left-border--animation {
    -webkit-animation-name: left-border;
    animation-name: left-border;
    -webkit-animation-duration: 1.6s;
    animation-duration: 1.6s;
    animation-delay: 1.8s;
    -webkit-animation-delay: 1.8s;
    animation-iteration-count: 1;
    -webkit-animation-fill-mode: forwards;
    animation-fill-mode: forwards;
  }
  .right-border--animation {
    -webkit-animation-name: right-border;
    animation-name: right-border;
    -webkit-animation-duration: 1.6s;
    animation-duration: 1.6s;
    animation-delay: 1.8s;
    -webkit-animation-delay: 1.8s;
    animation-iteration-count: 1;
    -webkit-animation-fill-mode: forwards;
    animation-fill-mode: forwards;
  }

  .top-border--animation {
    -webkit-animation-name: top-border;
    animation-name: top-border;
    -webkit-animation-duration: 1.6s;
    animation-duration: 1.6s;
    animation-delay: 1.8s;
    -webkit-animation-delay: 1.8s;
    animation-iteration-count: 1;
    -webkit-animation-fill-mode: forwards;
    animation-fill-mode: forwards;
  }
  .bottom-border--animation {
    -webkit-animation-name: bottom-border;
    animation-name: bottom-border;
    -webkit-animation-duration: 1.6s;
    animation-duration: 1.6s;
    animation-delay: 1.8s;
    -webkit-animation-delay: 1.8s;
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
    p {
      font-size: 1rem;
    }
  }

  @media only screen and (min-width: 601px) and (max-width: 920px) and (orientation: landscape) {
    p {
      font-size: 1rem;
    }
    .border-bottom {
      bottom: 0px;
    }
  }

  @keyframes content1in {
    0% {
      opacity: 0;
      transform: translateX(-500%);
    }
    75% {
      transform: translateX(0%);
    }
    100% {
      transform: translateX(0%);
      opacity: 1;
    }
  }

  @keyframes content2in {
    0% {
      opacity: 0;
      transform: translate(500%, -50%);
    }
    75% {
      transform: translate(0%, -50%);
    }
    100% {
      transform: translate(0%, -50%);
      opacity: 1;
    }
  }

  @keyframes left-border {
    0% {
      transform: translateX(0%) scaleX(1) scaleY(1);
    }
  
    100% {
      transform: translateX(100%) scaleX(12) scaleY(10000);
    }
  }
  @keyframes right-border {
    0% {
      transform: translateX(0%) scaleX(1) scaleY(1);
    }
  
    100% {
      transform: translateX(-100%) scaleX(12) scaleY(10000);
    }
  }

  @keyframes top-border {
    0% {
      transform: translateY(0%) scaleX(1) scaleY(1);
    }
  
    100% {
      transform: translateY(100%) scaleX(10000) scaleY(12);
    }
  }

  @keyframes bottom-border {
    0% {
      transform: translateY(0%) scaleX(1) scaleY(1);
    }
  
    100% {
      transform: translateY(-12px) scaleX(10000) scaleY(12);
    }
  }

</style>

<div class="logo">
  <img src="/logoRising.svg" alt="Ewingar Rising Logo">
</div>
<div class="content1">
  <p>
    From November 22 - 24 2019 the community of Ewingar will be hosting this event to provide relief for it's residents, both in terms of a chance to party and relax, and also to raise funds for rebuilding.
  </p>
</div>
<div class="content2">\
  <p>
    This event is volunteer-run, with all proceeds to be distributed to those who need it most in our community to recover, rebuild and rise from the ashes. 
  </p>
</div>
<div class="content3">
  <p>
    You can assist the community of Ewingar enourmously simply by coming to this great event, having a great time, spreading the love. With a great list of acts, and heaps of other attactions this will be a weekend to remember.
  </p>
</div>
<div class="border-top"></div>
<div class="border-left"></div>
<div class="border-right"></div>
<div class="border-bottom"></div>
<div class="classUser top-border--animation bottom-border--animation left-border--animation right-border--animation content1--animation content2--animation content3--animation"></div>

<div class="arrow" id="arrow" style="opacity: {arrowOpac}">
  <div class="arrow--animate">
    <div class="line"></div>
    <div class="arrow--head"></div>
    <small class="scroll">
      scroll...
    </small>
  </div>
</div>
