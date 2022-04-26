<script>
  export let id;
  // global store
  import { addToCart } from '../stores/cart';
  import globalStore from '../stores/globalStore';
  import products from '../stores/defaultProducts';
  import Loading from '../components/Loading.svelte';
  import { Link } from 'svelte-routing';
  $: product = $products.find((item) => item.id === parseInt(id));
</script>

<svelte:head>
  <title>{!product ? 'single product' : product.title}</title>
</svelte:head>

{#if !product}
  <Loading />
{:else}
  <section class="single-product">
    <!-- back to products -->
    <Link to="/products" class="btn btn-primary">back to products</Link>
    <!-- single product container -->
    <div class="single-product-container">
      <article class="single-product-img">
        <img src={product.image} alt={product.title} />
      </article>
      <article>
        <h1>{product.title}</h1>
        <h2>${product.price}</h2>
        <p>{product.description}</p>
        <button
          class="btn btn-primary btn-block"
          on:click={() => {
            addToCart(product);
            globalStore.toggleItem('cart', true);
          }}>add to cart</button
        >
      </article>
    </div>
  </section>
{/if}
