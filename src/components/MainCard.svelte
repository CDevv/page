<script>
    import ProfilePic from "./ProfilePic.svelte";
    import MainInfo from "./MainInfo.svelte";
    import PageButton from "./PageButton.svelte";
    import { fade } from "svelte/transition";
    let { children } = $props();

    let pageVisible = $state(true);
    function enter() {
        pageVisible = true;
    }
    function leave() {
        pageVisible = false;
        return false;
    }
</script>

<div class="bg-gray-900 rounded-xl p-6 flex flex-col gap-5">
    <div id="main-info" class="flex flex-col lg:flex-row items-center">
        <ProfilePic />
        <MainInfo />
    </div>
    <div id="navbar" class="grid auto-cols-auto grid-flow-row lg:grid-flow-col gap-5">
        <PageButton title="Home" href="/" onclick={leave}/>
        <PageButton title="Projects" href="/projects" onclick={leave}/>
        <PageButton title="Blogs" href="/blogs" onclick={leave}/>
        <PageButton title="Links" href="/links" onclick={leave}/>
        <PageButton title="Contact" href="/contact" onclick={leave}/>
    </div>
    {#if pageVisible}
        <div id="page-content" in:fade out:fade onoutrostart={enter}>
            {@render children()}
        </div>
    {/if}
</div>
