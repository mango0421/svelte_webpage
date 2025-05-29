<script>
    import NavBar from '../components/NavBar.svelte';
    import ImageSlider from '../components/ImageSlider.svelte';
    import IntroText from '../components/IntroText.svelte';
</script>

<NavBar />

<div class="main">
    <div class="overlay"></div>
    <div class="left">
        <ImageSlider />
    </div>
    <div class="right">
        <IntroText />
    </div>
</div>

<style>
    /* 전체 페이지 스크롤 방지 */
    html, body {
        margin: 0;
        padding: 0;
        overflow: hidden;
        width: 100%;
        height: 100%;
    }

    .main {
        position: relative;
        display: flex;
        flex-wrap: wrap;
        width: 100vw;
        height: 100vh;
        overflow: hidden;

        background-image: url('/background.jpg');
        background-size: cover;
        background-position: center;
        background-repeat: no-repeat;
        background-attachment: fixed;
    }

    .overlay {
        position: absolute;
        inset: 0;
        background-color: rgba(255, 255, 255, 0.75);
        z-index: 0;
    }

    .left,
    .right {
        position: relative;
        z-index: 1;
        flex: 1 1 50%;
        padding: 2rem;
        display: flex;
        align-items: center;
        justify-content: center;
        min-width: 300px;
        box-sizing: border-box;
    }

    .right {
        flex-direction: column;
        align-items: flex-start;
        text-align: left;
    }

    @media (max-width: 768px) {
        .main {
            flex-direction: column;
        }

        .left,
        .right {
            flex: 1 1 100%;
        }

        .right {
            align-items: center;
            text-align: center;
        }
    }
</style>
