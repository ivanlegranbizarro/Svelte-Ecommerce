<script>
  import { Link } from 'svelte-routing';
  import user from '../stores/user';
  //logout functionality
  import globalStore from '../stores/globalStore';
</script>

{#if $user.jwt}
  <Link
    to="/"
    class="logout-btn"
    on:click={() => {
      globalStore.toggleItem('sidebar', false);
    }}>Logout</Link
  >
{:else}
  <Link
    to="/"
    class="login-btn"
    on:click={() => {
      globalStore.toggleItem('sidebar', false);
    }}>Login</Link
  >
{/if}
