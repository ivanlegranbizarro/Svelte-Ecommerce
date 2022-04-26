<script>
  import Hero from '../components/Hero.svelte';
  import { Link } from 'svelte-routing';
  // featured products
  import Featured from '../components/Products/Featured.svelte';
</script>

<Hero>
  <Link class="btn btn-primary btn-hero">shop now</Link>
</Hero>
<Featured title="featured products"/>
