<script lang="ts">
    export let percent: number = 50;
    $: style = `background: linear-gradient(to right, var(--good-color), var(--good-color) ${percent}%, var(--block-background) ${percent}%, var(--block-background));`;
</script>

<div {style} />

<style lang="scss">
    div {
        height: 24px;
        width: 120px;
        border: 1px solid var(--good-color);
        border-radius: 12px;
    }
</style>
