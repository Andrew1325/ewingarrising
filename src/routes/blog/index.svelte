<script context="module">

	export function preload({ params, query }) {
		return this.fetch(`blog.json`).then(r => r.json()).then(posts => {
			return { posts };
		});
  }
  
  
</script>

<script>
  import { onMount } from 'svelte'
  export let posts;

  let oldScroll = 0

  function scrolling(){ 
      var st = window.pageYOffset || document.documentElement.scrollTop
      if (st > oldScroll){
        // downscroll code
        console.log('going down ' + st + ' ' + oldScroll)
        document.removeEventListener('scroll', scrolling);
        setTimeout(function() {
          st = window.pageYOffset || document.documentElement.scrollTop
          oldScroll = st <= 0 ? 0 : st; // For Mobile or negative scrolling
          document.addEventListener('scroll', scrolling);
        }, 2500)
      } else {
        // upscroll code
        console.log('going up')
        document.removeEventListener('scroll', scrolling);
        setTimeout(function() {
          st = window.pageYOffset || document.documentElement.scrollTop
          oldScroll = st <= 0 ? 0 : st; // For Mobile or negative scrolling
          document.addEventListener('scroll', scrolling);
        }, 2500)
      }
      
    }
  
  onMount(() => {
    window.scrollTo(0, 20000)
    document.addEventListener("scroll", scrolling);
  })
</script>

<style>
	ul {
		margin: 0 0 1em 0;
		line-height: 1.5;
  }
  .all {
    position: relative;
    height: 10000vh;
  }
</style>

<svelte:head>
	<title>Blog</title>
</svelte:head>

<h1>Recent posts</h1>

<div class="all">
  <ul>
    {#each posts as post}
      <!-- we're using the non-standard `rel=prefetch` attribute to
          tell Sapper to load the data for the page as soon as
          the user hovers over the link or taps it, instead of
          waiting for the 'click' event -->
      <li><a rel='prefetch' href='blog/{post.slug}'>{post.title}</a></li>
    {/each}
  </ul>
</div>