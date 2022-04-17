<script>
  import '../styles/root/global.scss'
  import Header from '../components/Header.svelte'
</script>

<div class="container">
  <Header />
  <slot />
</div>