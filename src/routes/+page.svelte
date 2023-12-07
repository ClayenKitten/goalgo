<script lang="ts">
    import type { ShareInfo } from "$lib";
    import ShareView from "./ShareView.svelte";
    import SharesList from "./SharesList.svelte";

    let selected: ShareInfo | undefined = undefined;
</script>

<main>
    <SharesList bind:selected/>
    {#if selected}
        <ShareView share={selected}/>
    {/if}
</main>

<style lang="scss">
    main {
        flex: 1;
        display: flex;
        gap: 20px;
        align-items: stretch;
    }
</style>
