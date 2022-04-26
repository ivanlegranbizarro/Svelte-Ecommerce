<script>
  import globalStore from '../../stores/globalStore';
  import { fly, fade, blur } from 'svelte/transition';
  import { Link } from 'svelte-routing';
  import CartList from './CartList.svelte';
  import user from '../../stores/user';
</script>

<div class="cart-overlay" transition:blur>
  <!-- cart header -->
  <div class="cart-container" transition:fly={{ x: 100 }}>
    <div class="cart" transition:fade={{ delay: 400 }}>
      <div class="cart-header">
        <button
          class="btn-close"
          on:click={() => {
            globalStore.toggleItem('cart', false);
          }}
        >
          <i class="fas fa-window-close" />
        </button>
        <h2 class="cart-title">your bag</h2>
        <span />
      </div>
      <!-- end cart header -->
      <!-- cart items -->
      <CartList />
      <!-- end cart items -->
      <!-- cart footer -->
      <div class="cart-footer">
        {#if $user.jwt}
          <Link
            to="/checkout"
            class="btn btn-primary btn-block"
            on:click={() => {
              globalStore.toggleItem('cart', false);
            }}>Checkout</Link
          >
        {:else}
          <p class="cart-login">
            in order to checkout please
            <Link
              to="/login"
              on:click={() => {
                globalStore.toggleItem('cart', false);
              }}>Login</Link
            >
          </p>
        {/if}
      </div>
      <!-- end cart footer -->
    </div>
  </div>
</div>
