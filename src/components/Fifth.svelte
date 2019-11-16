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

    const lines = document.querySelectorAll('.bord-top')

    const observer = new IntersectionObserver((entries, observer) => {

      const borderT = document.querySelector('.bord-top')
      const borderL = document.querySelector('.bord-left')
      const borderR = document.querySelector('.bord-right')
      const borderB = document.querySelector('.bord-bottom')

      entries.forEach(entry => {

        if (entry.isIntersecting) {

          borderT.classList.add('t-border--animation')
          borderB.classList.add('b-border--animation')
          borderL.classList.add('l-border--animation')
          borderR.classList.add('r-border--animation')

          setTimeout(() => {
            opac = 1
          }, 6000)
        } else {
          borderT.classList.remove('t-border--animation')
          borderB.classList.remove('b-border--animation')
          borderL.classList.remove('l-border--animation')
          borderR.classList.remove('r-border--animation')
        }
      })
    }, options)
    lines.forEach(section => {
      observer.observe(section)
    })
    
  })
</script>

<style>

  p {
    color: black;
    margin: 0;
    font-family: 'Roboto Slab', serif;
    font-weight: 100;
    font-size: 1.4rem;
    text-align: center;
    padding: 0 15%;
  }

  .logoWht {
    position: absolute;
    top: 18%;
    left: 50%;
    transform: translate(-50%, -50%);
  }

  .logoWht img{
      width: 12vw;
    }

  .book {
    position: absolute;
    top: 44%;
    left: 50%;
    transform: translate(-50%, -50%);
    width: 322px;
  }

  .face {
    position: absolute;
    top: 64%;
    left: 50%;
    transform: translate(-50%, -50%);
    width: 322px;
  }

  .bord-top {
    position: absolute;
    top: 0%;
    left: 50%;
    transform: translateY(0%) scaleX(1) scaleY(1);
    height: 1px;
    width: 1px;
    background-color: rgb(0, 0, 0);
  }
  .bord-left {
    position: absolute;
    top: 50%;
    left: 0%;
    transform: translateX(0%) scaleX(1) scaleY(1);
    height: 1px;
    width: 1px;
    background-color: rgb(0, 0, 0);
  }
  .bord-right {
    position: absolute;
    top: 50%;
    right: 0%;
    transform: translateX(0%) scaleX(1) scaleY(1);
    height: 1px;
    width: 1px;
    background-color: rgb(0, 0, 0);
  }
  .bord-bottom {
    position: absolute;
    bottom: 7px;
    left: 50%;
    transform: translateY(0%) scaleX(1) scaleY(1);
    height: 1px;
    width: 1px;
    background-color: rgb(0, 0, 0);
  }

  .l-border--animation {
    -webkit-animation-name: l-border;
    animation-name: l-border;
    -webkit-animation-duration: 1.6s;
    animation-duration: 1.6s;
    animation-delay: 1.8s;
    -webkit-animation-delay: 1.8s;
    animation-iteration-count: 1;
    -webkit-animation-fill-mode: forwards;
    animation-fill-mode: forwards;
  }
  .r-border--animation {
    -webkit-animation-name: r-border;
    animation-name: r-border;
    -webkit-animation-duration: 1.6s;
    animation-duration: 1.6s;
    animation-delay: 1.8s;
    -webkit-animation-delay: 1.8s;
    animation-iteration-count: 1;
    -webkit-animation-fill-mode: forwards;
    animation-fill-mode: forwards;
  }

  .t-border--animation {
    -webkit-animation-name: t-border;
    animation-name: t-border;
    -webkit-animation-duration: 1.6s;
    animation-duration: 1.6s;
    animation-delay: 1.8s;
    -webkit-animation-delay: 1.8s;
    animation-iteration-count: 1;
    -webkit-animation-fill-mode: forwards;
    animation-fill-mode: forwards;
  }
  .b-border--animation {
    -webkit-animation-name: b-border;
    animation-name: b-border;
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
    .logoWht img{
      width: 26vw;
    }
    
  }

  @media only screen and (max-width: 600px) and (orientation: landscape) {
    .bord-bottom {
      bottom: -5px;
    }
    .book, .face {
      width: 244px;
    }
    .book {
      top: 60%;
    }
    .face {
      top: 90%;
    }
    .face svg {
      transform: translateY(-30%)
    }
  }

  @media only screen and (min-width: 601px) and (max-width: 920px) and (orientation: landscape) {
    p {
      font-size: 1rem;
    }
    .bord-bottom {
      bottom: 0px;
    }
    .book {
    width: 282px;
  }

  .face {
    position: absolute;
    top: 80%;
    left: 50%;
    transform: translate(-50%, -50%);
    width: 282px;
  }
  }

  @keyframes contin {
    0% {
      opacity: 0;
      transform: translateY(-500%);
    }
    100% {
      transform: translateY(0%);
      opacity: 1;
    }
  }

  @keyframes l-border {
    0% {
      transform: translateX(0%) scaleX(1) scaleY(1);
    }
  
    100% {
      transform: translateX(100%) scaleX(12) scaleY(10000);
    }
  }
  @keyframes r-border {
    0% {
      transform: translateX(0%) scaleX(1) scaleY(1);
    }
  
    100% {
      transform: translateX(-100%) scaleX(12) scaleY(10000);
    }
  }

  @keyframes t-border {
    0% {
      transform: translateY(0%) scaleX(1) scaleY(1);
    }
  
    100% {
      transform: translateY(100%) scaleX(10000) scaleY(12);
    }
  }

  @keyframes b-border {
    0% {
      transform: translateY(0%) scaleX(1) scaleY(1);
    }
  
    100% {
      transform: translateY(-12px) scaleX(10000) scaleY(12);
    }
  }

</style>

<div class="logoWht">
  <img src="/logoRisingWht.svg" alt="Ewingar Rising Logo">
</div>
<div class="book">
  <p>
    Book now at:
  </p>
  <a href="https://www.eventbrite.com.au/e/ewingar-rising-bushfire-recovery-benefit-tickets-78146222455?aff=ebdshpfprimarybucket" target="_blank">
    <svg viewBox="0 0 200 36"><g fill-rule="evenodd"><path fill="#ff8300" d="M186.292 17.513c2.693-.61 5.381.495 6.878 2.584l-11.905 2.693c.411-2.52 2.333-4.668 5.027-5.277zm6.945 9.91a6.57 6.57 0 0 1-3.98 2.679c-2.711.614-5.417-.51-6.907-2.626l11.941-2.702 1.945-.44 3.72-.841a11.782 11.782 0 0 0-.31-2.372c-1.514-6.426-8.056-10.432-14.612-8.949-6.556 1.484-10.644 7.896-9.13 14.321 1.513 6.426 8.055 10.433 14.611 8.95 3.863-.875 6.868-3.46 8.376-6.751l-5.654-1.269zM165.135 35.118V18.082h-3.677v-5.804h3.677V4.289h6.244v7.989h4.69v5.804h-4.69v17.036zM153.207 35.118h6.03v-22.84h-6.03v22.84zm-.784-30.853c0-2.114 1.667-3.7 3.824-3.7s3.775 1.586 3.775 3.7c0 2.115-1.618 3.748-3.775 3.748s-3.824-1.633-3.824-3.748zM151.108 12.342c-3.083.16-4.901.633-6.75 1.973v-2.037h-6.027v22.84h6.026v-11.2c0-3.524.86-5.529 6.751-5.726v-5.85zM117.507 24.057c.15 3.333 3.051 6.128 6.602 6.128 3.602 0 6.553-2.942 6.553-6.422 0-3.432-2.951-6.373-6.553-6.373-3.55 0-6.452 2.843-6.602 6.128v.539zm-5.88 11.061V1.38l6.03-1.364v13.962c1.863-1.49 4.07-2.115 6.472-2.115 6.864 0 12.355 5.286 12.355 11.918 0 6.583-5.49 11.965-12.355 11.965-2.402 0-4.609-.624-6.472-2.114v1.487h-6.03zM98.792 35.118V17.965h-3.677v-5.687h3.677V4.283l6.244-1.413v9.408h4.69v5.687h-4.69v17.153zM87.742 35.118V22.915c0-4.421-2.403-5.382-4.806-5.382-2.402 0-4.804.913-4.804 5.286v12.299h-6.03v-22.84h6.03v1.699c1.323-.961 2.941-2.115 6.129-2.115 5.098 0 9.511 2.932 9.511 10.092v13.164h-6.03zM56.831 17.513c2.694-.61 5.382.495 6.878 2.584L51.805 22.79c.41-2.52 2.333-4.668 5.026-5.277zm6.945 9.91a6.57 6.57 0 0 1-3.98 2.679c-2.71.614-5.416-.51-6.907-2.626l11.942-2.702 1.945-.44 3.719-.841a11.782 11.782 0 0 0-.31-2.372c-1.514-6.426-8.056-10.432-14.612-8.949-6.556 1.484-10.644 7.896-9.13 14.321 1.514 6.426 8.055 10.433 14.612 8.95 3.863-.875 6.868-3.46 8.375-6.751l-5.654-1.269zM32.238 35.118l-9.365-22.84h6.57l5.933 15.49 5.981-15.49h6.57l-9.364 22.84zM11.05 17.507c2.694-.61 5.382.495 6.879 2.584L6.024 22.785c.41-2.52 2.333-4.668 5.026-5.278zm6.945 9.91a6.57 6.57 0 0 1-3.98 2.68c-2.71.613-5.416-.51-6.907-2.626l11.942-2.702 1.945-.44 3.719-.842a11.782 11.782 0 0 0-.31-2.371c-1.514-6.426-8.055-10.433-14.612-8.95C3.236 13.65-.85 20.063.662 26.489c1.514 6.426 8.056 10.432 14.612 8.949 3.863-.874 6.868-3.46 8.376-6.75l-5.655-1.27z"></path></g></svg>
  </a>
</div>

<div class="face">
  <p>
    find us on:
  </p>
  <a href="https://www.facebook.com/events/ewingar-hall-584-ewingar-road-ewingar-nsw-2469/ewingar-rising-bushfire-recovery-concert/536375966936517/" targer="_blank">
    <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 266 100"><path fill="none" d="M0 0h266v100H0z"/><g fill="#3b5998"><path d="M140.021 49.597c-1.784 0-3.07.585-4.374 1.181v13.486c1.249.119 1.965.119 3.15.119 4.282 0 4.869-1.961 4.869-4.699v-6.441c0-2.022-.671-3.646-3.645-3.646zm-28.438-.736c-2.971 0-3.649 1.631-3.649 3.651v1.135h7.294v-1.135c0-2.02-.678-3.651-3.645-3.651zm-55.09 14.037c0 1.598.754 2.428 2.418 2.428 1.785 0 2.842-.582 4.145-1.18v-3.199h-3.903c-1.848 0-2.66.344-2.66 1.951zm111.191-13.301c-2.976 0-4.007 1.624-4.007 3.646v7.379c0 2.027 1.031 3.656 4.007 3.656 2.968 0 4.007-1.629 4.007-3.656v-7.379c-.001-2.022-1.04-3.646-4.007-3.646zM41.909 71.172h-8.748V49.998H28.79v-7.296h4.372V38.32c0-5.953 2.467-9.492 9.479-9.492h5.838v7.298H44.83c-2.73 0-2.91 1.02-2.91 2.923l-.011 3.652h6.61l-.773 7.296h-5.837v21.175zm29.897.055h-7.291l-.315-1.844c-3.329 1.844-6.3 2.143-8.26 2.143-5.347 0-8.193-3.572-8.193-8.512 0-5.828 3.321-7.908 9.262-7.908h6.047v-1.26c0-2.975-.341-3.848-4.916-3.848h-7.48l.731-7.296h8.176c10.038 0 12.239 3.171 12.239 11.203v17.322zm24.793-20.694c-4.537-.778-5.84-.949-8.023-.949-3.921 0-5.106.865-5.106 4.195v6.299c0 3.33 1.185 4.199 5.106 4.199 2.183 0 3.486-.174 8.023-.955v7.117c-3.974.891-6.563 1.125-8.751 1.125-9.392 0-13.125-4.939-13.125-12.074v-5.111c0-7.141 3.733-12.089 13.125-12.089 2.188 0 4.777.235 8.751 1.13v7.113zm27.376 8.957h-16.042v.588c0 3.33 1.186 4.199 5.106 4.199 3.524 0 5.675-.174 10.204-.955v7.117c-4.368.891-6.644 1.125-10.929 1.125-9.393 0-13.128-4.939-13.128-12.074v-5.844c0-6.243 2.771-11.356 12.396-11.356s12.393 5.054 12.393 11.356v5.844zm28.437.135c0 6.896-1.971 11.926-13.911 11.926-4.312 0-6.841-.379-11.6-1.111V31.02l8.745-1.459V43.35c1.89-.702 4.336-1.059 6.562-1.059 8.746 0 10.203 3.921 10.203 10.222v7.112zm28.033.15c0 5.949-2.456 11.719-12.732 11.719-10.281 0-12.783-5.77-12.783-11.719v-5.744c0-5.952 2.502-11.723 12.783-11.723 10.276 0 12.732 5.771 12.732 11.723v5.744zm28.014 0c0 5.949-2.459 11.719-12.733 11.719-10.281 0-12.783-5.77-12.783-11.719v-5.744c0-5.952 2.502-11.723 12.783-11.723 10.274 0 12.733 5.771 12.733 11.723v5.744zm28.749 11.397h-9.479l-8.017-13.383v13.383h-8.748V31.019l8.748-1.459v25.849l8.017-12.707h9.479l-8.752 13.867 8.752 14.603zm-41.512-21.575c-2.971 0-4.002 1.624-4.002 3.646v7.379c0 2.027 1.031 3.656 4.002 3.656 2.967 0 4.017-1.629 4.017-3.656v-7.379c0-2.022-1.05-3.646-4.017-3.646zM242.201 66.178c1.473 0 2.646 1.201 2.646 2.701 0 1.523-1.174 2.711-2.657 2.711-1.476 0-2.673-1.188-2.673-2.711 0-1.5 1.197-2.701 2.673-2.701h.011zm-.011.42c-1.187 0-2.158 1.021-2.158 2.281 0 1.283.972 2.291 2.169 2.291 1.198.012 2.155-1.008 2.155-2.279s-.957-2.293-2.155-2.293h-.011zm-.503 3.853h-.48v-3.014c.252-.035.492-.07.852-.07.456 0 .754.096.937.227.177.133.272.336.272.623 0 .398-.262.637-.585.734v.023c.263.049.442.287.503.73.07.469.143.648.19.746h-.503c-.071-.098-.144-.373-.204-.77-.07-.383-.264-.527-.648-.527h-.333v1.298zm0-1.668h.348c.394 0 .729-.145.729-.518 0-.264-.19-.527-.729-.527-.157 0-.266.012-.348.023v1.022z"/></g></svg>
  </a>
</div>

<div class="bord-top"></div>
<div class="bord-left"></div>
<div class="bord-right"></div>
<div class="bord-bottom"></div>
<div class="classUser t-border--animation b-border--animation l-border--animation r-border--animation content1--animation content2--animation content3--animation"></div>
