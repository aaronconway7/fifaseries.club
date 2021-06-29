<script>
    // const netlifyIdentity = require('netlify-identity-widget')
    import { onMount } from 'svelte'
    import netlifyIdentity from 'netlify-identity-widget'

    onMount(() => {
        netlifyIdentity.init()
        netlifyIdentity.open()
        netlifyIdentity.on('login', user => console.log('login', user))
    })
</script>

<svelte:head>
    <title>Fifa Series</title>
</svelte:head>

<h1>⚽ Fifa Series</h1>
