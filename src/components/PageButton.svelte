<script>
    let { title, href, onclick } = $props();
</script>

<a {href} class="block grow">
    <button class="bg-gray-950 rounded-xl p-4 text-2xl font-bold container cursor-pointer hover:bg-gray-900"
        onclick={onclick}
    >
        {title}
    </button>
</a>