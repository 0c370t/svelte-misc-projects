<script>
    import Container from "../components/Container.svelte";

    let inputValues = [];
    for (let i = 0; i < 1002; i++) {
        inputValues.push(Math.random().toString(36).substring(2, 12) + Math.random().toString(36).substring(2, 12));
    }
</script>
<Container>
    <p>
        This is a demonstration of massive state / state update performance using a component state in Svelte.
    </p>
    <p>
        Our current Forms implementation is very similar to how this is implemented; a single massive state that updates
        every time you write in a box.
    </p>
    <hr/>
    <ul>
        {#each inputValues as v, i}
            <li>
                <label>
                    <span>Input #{i}</span>
                    <input bind:value={v} type="text"/>
                    {v}
                </label>
            </li>
        {/each}
    </ul>
</Container>
<style>
    ul {
        font-size: 0.9em;
        list-style: none;
        display: flex;
        flex-wrap: wrap;
    }

    li {
        min-width: 32%;
        margin-bottom: 0.5em;
        margin-right:1em;
        line-height: 2em;
        height: 2em;
    }

    label > span {
        width: 10ch;
        display: block;
        float: left;
    }

    hr {
        margin: 1em;
        border: none;
        border-top: 1px solid #676778;
    }
</style>