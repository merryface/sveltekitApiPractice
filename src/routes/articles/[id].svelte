<script context="module">
  const baseUrl = import.meta.env.VITE_BASE_URL;
  
  export async function load({ fetch, params }) {
    const id = params.id
    const res = await fetch(`${baseUrl}/posts/${id}`)
    const article = await res.json()

    if (res.ok) {
      return {
        props: {
          article
        }
      }
    }

    return {
      status: res.status,
      error: new Error('Could not fetch article')
    }
  }
</script>

<script>
  export let article
</script>

<div class="Article">
  <h1 class="Article__title">{ article.title }</h1>
  <p class="Article__body">{ article.body }</p>
</div>