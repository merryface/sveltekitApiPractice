<script context="module">
  export async function load({ fetch }) {
    const res = await fetch('https://jsonplaceholder.typicode.com/posts')
    const articles = await res.json()

    if (res.ok) {
      return {
        props: {
          articles
        }
      }
    }

    return {
      status: res.status,
      error: new Error('Could not fetch articles')
    }
  }
</script>

<script>
  import '../../styles/articles/index.scss'

  export let articles;
</script>

<div class="Articles">
  <h1 class="Articles__title">Fake Space Articles</h1>
  <p class="Articles__text">Here are some articles about Space... not really actually. Although maybe I could sort that out one day...</p>

  <ul class="Articles__list">
    {#each articles as article}
    <a sveltekit:prefetch href={`/articles/${article.id}`}><li class="Articles__list-item">{ article.title }</li></a>
    {/each}
  </ul>
</div>

