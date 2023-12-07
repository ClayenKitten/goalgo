<script lang="ts">
</script>

<main>
    <section class="info">
        <h2>Правила, API</h2>
    </section>
    <section class="results">
        <h2>Тестирование вашего решения</h2>
    </section>
</main>

<style lang="scss">
    main {
        flex: 1;
        display: flex;
        gap: 20px;
        align-items: stretch;

        > section {
            display: flex;
            flex-direction: column;
            gap: 20px;
            padding: 32px 40px;
            border-radius: 12px;
            background-color: var(--block-background);
            &.info {
                flex: 0 1 380px;
                display: flex;
                flex-direction: column;
            }
            &.results {
                flex: 1;
            }
        }
    }
</style>
