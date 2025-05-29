<script>
  import Router from 'svelte-spa-router';
  import Home from './pages/Home.svelte';
  import About from './pages/About.svelte';
  import Photos from './pages/Photos.svelte';
  import History from './pages/History.svelte';
  import Letters from './pages/Letters.svelte'; // 추가


  const routes = {
    '/': Home,
    '/about': About,

    '/photos': Photos,
    '/history': History,
      '/letters': Letters, // 추가
  };
</script>

<Router {routes} />
