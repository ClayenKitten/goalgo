<script lang="ts">
    import CodeMirror from "svelte-codemirror-editor";
    import { python } from "@codemirror/lang-python";
    import { oneDark } from "@codemirror/theme-one-dark";
    import { Timelines, type File } from "$lib";
    import Tabs from "./Tabs.svelte";
    import OptionList from "$lib/OptionList.svelte";
    import Plot from "$lib/Plot.svelte";
    import { writable } from "svelte/store";
    import InfoButton from "$lib/InfoButton.svelte";
    import Progress from "./Progress.svelte";

    let files: File[] = [
        { name: "Sample1.py", content: 'print("Hello world!")' },
        { name: "Sample2.py", content: 'print("Hello sample!")' },
        { name: "Sample3.py", content: 'print("Hello sample!")' },
        { name: "Sample3.py", content: 'print("Hello sample!")' },
        { name: "Sample3.py", content: 'print("Hello sample!")' },
        { name: "Sample3.py", content: 'print("Hello sample!")' },
        { name: "Sample3.py", content: 'print("Hello sample!")' },
        { name: "Sample3.py", content: 'print("Hello sample!")' }
    ];
    let file: File = files[0];
    $: if (!files.includes(file)) file = files[0];

    let selected_graph: string;
    let timeline = Timelines[1];
</script>

<main>
    <section class="upload">
        <div class="tabs">
            <Tabs bind:files bind:selected={file} />
        </div>
        <div class="editor">
            <CodeMirror
                bind:value={file.content}
                lang={python()}
                theme={oneDark}
                styles={{
                    "&": { backgroundColor: "var(--block-background)" },
                }}
            />
        </div>
        <label class="upload-button">
            <input type="file" />
            <div>
                <img src="/icons/file.svg" alt="" />
                <span>Выберите файлы</span>
            </div>
            <span>или перетащите их сюда</span>
        </label>
    </section>
    <section class="results">
        <OptionList options={Timelines} bind:selected={timeline} />
        <hr />
        <Plot data={writable([])} />
        <hr />
        <div class="label">
            <img src="/icons/eye_open.svg" alt="selected graph"/>
            <h1>{selected_graph}</h1>
            <InfoButton />
        </div>
        <div class="stats">
            {#each [{ name: "Стата 1", num: 23.4 }] as value}
                <div>
                    <span>{value.name}</span>
                    <span>{value.num}</span>
                </div>
            {/each}
        </div>
        <div class="algos">
            {#each [0, 1, 2] as algo}
                <img src="/icons/eye_open" alt=""/>
                <span></span>
                <!-- <Progress percent={algo.progress * 100}/> -->
            {/each}
        </div>
        <div class="footer">
            <h1>Выбор периода</h1>
            <div>
                <div>
                    <span>Начало</span>
                    <input type="date" />
                </div>
                <div>
                    <span>Конец</span>
                    <input type="date" />
                </div>
                <button>
                    Запустить
                    <img src="/icons/arrow_back.svg" alt=""/>
                </button>
            </div>
        </div>
    </section>
</main>

<style lang="scss">
    main {
        flex: 1;
        display: flex;
        gap: 20px;
        align-items: stretch;

        > section {
            flex: 1 0 0;
            display: flex;
            overflow-x: hidden;
            flex-direction: column;
            padding: 32px 40px;
            border-radius: 12px;
            background-color: var(--block-background);
            &.upload {
                display: flex;
                flex-direction: column;
                > .tabs {
                    max-width: min-content;
                    overflow-x: scroll;
                }
                > .editor {
                    flex: 1 0 0;
                    overflow-y: scroll;
                    border: 1px solid #56595e;
                }
                > .upload-button {
                    display: flex;
                    flex-direction: column;
                    align-items: center;
                    gap: 4px;
                    margin-top: 20px;
                    cursor: pointer;

                    > input {
                        display: none;
                    }
                    > div {
                        align-self: stretch;
                        display: flex;
                        gap: 4px;
                        display: flex;
                        align-items: center;
                        justify-content: center;

                        background-color: var(--block-background);
                        border: 1px solid var(--good-color);
                        padding: 8px 12px;
                        border-radius: 12px;

                        > span {
                            color: var(--good-color);
                            font-size: 20px;
                            line-height: 22px;
                        }
                    }
                }
            }
            &.results {
                display: flex;
                flex-direction: column;
                justify-content: stretch;
                align-items: stretch;
                > .label {
                    display: flex;
                    align-items: center;
                    gap: 8px;
                    margin: 16px 0;
                    > img {
                        width: 16px;
                        height: 16px;
                    }
                    > h1 {
                        flex: 1;
                        font-weight: normal;
                    }
                }
                > .stats {
                    display: flex;
                    margin-bottom: 20px;
                    > div {
                        display: flex;
                        flex-direction: column;
                        padding: 0 20px;
                        border: 1px solid #57595E;
                        border-radius: 12px;
                        > span:nth-child(2) {
                            font-size: 20px;
                            line-height: 24px;
                        }
                    }
                }
                > .footer {
                    display: flex;
                    flex-direction: column;
                    gap: 8px;
                    > div {
                        display: flex;
                        gap: 20px;
                        > div {
                            display: flex;
                            flex-direction: column;
                        }
                        > button {
                            margin-left: auto;
                            background-color: var(--good-color);
                            border-radius: 12px;
                            padding: 8px 16px;
                        }
                    }
                }
            }
        }
    }
</style>
