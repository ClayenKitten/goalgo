<script lang="ts">
    let articles = [
        { title: "Статья 1", description: "Описание 1" },
        { title: "Статья 2", description: "Описание 2" },
        { title: "Статья 3", description: "Описание 3" },
        { title: "Статья 4", description: "Описание 4" },
        { title: "Статья 5", description: "Описание 5" },
        { title: "Статья 5", description: "Описание 5" },
        { title: "Статья 5", description: "Описание 5" },
        { title: "Статья 5", description: "Описание 5" },
        { title: "Статья 5", description: "Описание 5" },
        { title: "Статья 5", description: "Описание 5" },
        { title: "Статья 5", description: "Описание 5" },
        { title: "Статья 5", description: "Описание 5" },
        { title: "Статья 5", description: "Описание 5" },
        { title: "Статья 5", description: "Описание 5" },
        { title: "Статья 5", description: "Описание 5" },
        { title: "Статья 5", description: "Описание 5" },
        { title: "Статья 5", description: "Описание 5" },
        { title: "Статья 5", description: "Описание 5" },
        { title: "Статья 5", description: "Описание 5" },
        { title: "Статья 5", description: "Описание 5" }
    ];
</script>

<main>
    {#each articles as article}
        <article>
            <h2>{article.title}</h2>
            <p class="description">{article.description}</p>
        </article>
    {/each}
</main>

<style lang="scss">
    main {
        flex: 1 0 0;
        display: grid;
        grid-template-columns: 1fr 1fr 1fr;
        grid-auto-rows: 200px;
        gap: 20px 20px;
        align-items: stretch;

        > article {
            display: flex;
            flex-direction: column;
            padding: 32px 40px;
            gap: 20px;
            border-radius: 12px;
            background-color: var(--block-background);
        }

        padding-right: 24px;
        margin-right: -24px;
        scrollbar-color: var(--text) transparent;
        overflow-y: scroll;
    }
</style>
