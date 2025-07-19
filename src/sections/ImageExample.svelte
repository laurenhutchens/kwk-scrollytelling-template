<script>
    import Scroller from "../lib/Scroller.svelte";
    import ArticleText from "../lib/ArticleText.svelte";
</script>

<div>
    <Scroller layout="right">
        {#snippet sticky()}
            <img class="yavapai-img" src="yavapai.png" alt="The Great Seal of the Yavapai-Apache Nation!" />
        {/snippet}

        {#snippet scrolly()}
            <ArticleText>
                <strong>
                    Your final project might look totally different from this
                    template!
                </strong>
            </ArticleText>

            <ArticleText>It's yours to create.</ArticleText>
        {/snippet}
    </Scroller>
</div>

<style>
    .duck-img {
        width: 25%;
        margin: 0px auto;
    }
</style>
