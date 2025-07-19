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
        background-color: #ea4f11;
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
        background-color: #7a2115;
        padding: 2rem;
        border: 6px solid #3e474e;
        border-radius: 2rem;
        box-shadow: 16px 16px #e27823;
    }

    h1 {
        font-size: 3rem;
        margin: 0;
        color: #3e474e;
        text-shadow: 1px 1px 0 #e27823;
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
