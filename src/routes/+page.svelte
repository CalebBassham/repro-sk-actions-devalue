<script>
    import {enhance} from '$app/forms'

    export let data
</script>

<h1>Welcome to SvelteKit</h1>

<time>{data.now.toLocaleString()}</time>

<!-- Obviously this is a little dumb, but it does show the issue. -->
<form method="POST" use:enhance={() => {
    return async ({ result, update }) => {
      switch (result.type) {
        case 'success':
            result.data.now = data.now
            break
        default:
            update()
            break;
    }}
}}>
    <button>Update Time</button>
</form>