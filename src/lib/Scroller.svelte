<script>
    // `layout` can be either "right" or "left"
    // `sticky` and `scrolly` are the snippets passed in (see one of the examples)
    let { layout, sticky, scrolly } = $props(); 
</script>

<div class="wrapper {layout}">
    <div class="sticky">
        {@render sticky()}
    </div>

    <div class="scrolly">
        {@render scrolly()}
    </div>
</div>

<style>
    .wrapper {
        background-image: url('/public/sedonaYavapaiBackgroundImage.jpg');
        background-size: cover;
        background-position: center;
        background-repeat: repeat;
        filter: brightness(1.1) contrast (1.2);
        margin-top: 2rem;
        /* Existing styles */
        padding: min(100vh, 30rem) 1rem;
        border-style: solid;
        border-color: #523c4e;
        display: flex;
        flex-direction: row;
        flex-wrap: wrap;
        align-items: flex-start;
    }
    .wrapper::before {
        content: '';
        position: absolute;
        inset: 0;
        z-index: 0;
    }

    .left .scrolly {
        order: 0;
    }
    .left .sticky {
        order: 1;
    }

    .right .scrolly {
        order: 1;
    }
    .right .sticky {
        order: 0;
    }

    .sticky,
    .scrolly {
        display: flex;
        flex-direction: column;
        flex: 1 1; /* Allows growing, shrinking */
        position: relative;
        z-index: 1;
    }

    .sticky {
        position: sticky;
        top: 50vh;
        transform: translateY(-50%);
        display: flex;
        align-items: center;
        justify-content: center;
        z-index: 0;
    }

    .scrolly {
        z-index: 1;
    }

    @media (max-width: 768px) {
        .wrapper {
            flex-direction: column;
            padding: 2rem 1rem;
            width: 100vw;
        }

        .sticky,
        .scrolly {
            flex: 1 1 auto;
            min-width: 100%;
            position: static; /* remove sticky on mobile */
            transform: none;
        }

        .sticky {
            margin-bottom: 2rem;
        }
    }
</style>
