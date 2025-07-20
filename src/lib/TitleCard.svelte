<script>
    let { title, subtitle } = $props();
</script>

<div class="title-card">
    <div class="content">
        <h1>{title}</h1>
        <p>{subtitle}</p>
    </div>
</div>

<style>
    .title-card {
        background-color: #c7877e;
        height: 100vh;
        display: flex;
        justify-content: center;
        align-items: center;
        text-align: center;
        padding: 2rem;
        box-sizing: border-box;
        font-family: "Inter", sans-serif;
    }

    .content {
        max-width: 700px;
        background-color: #735368;
        padding: 2rem;
        border: 6px solid #966d88;
        border-radius: 2rem;
        box-shadow: 16px 16px #5c4253;
    }

    h1 {
        font-size: 3rem;
        margin: 0;
        color: #f3f4e1;
        text-shadow: 1px 1px 0 #dddecb;
    }

    p {
        font-size: 1.3rem;
        color: #542c3b;
        margin-top: 1rem;
    }

    @media (max-width: 600px) {
        h1 {
            font-size: 2.2rem;
        }

        p {
            font-size: 1.1rem;
        }
    }
</style>
