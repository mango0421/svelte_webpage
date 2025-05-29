<script>
    import { onMount } from 'svelte';

    let current = 0;

    const images = [
        '/assets/slider1.jpg',
        '/assets/slider2.jpg',
        '/assets/slider3.jpg',
        '/assets/slider4.jpg',
        '/assets/slider5.jpg',
        '/assets/slider6.jpg',
        '/assets/slider7.jpg',
        '/assets/slider8.jpg',
        '/assets/slider9.jpg'


    ];

    let interval;

    onMount(() => {
        interval = setInterval(() => {
            current = (current + 1) % images.length;
        }, 3000);

        return () => clearInterval(interval);
    });
</script>

<div class="slider">
    {#each images as img, index}
        <img src={img} alt="slide" class:selected={index === current} />
    {/each}
</div>

<style>
    .slider {
        position: relative;
        width: 100%;
        height: 100%;
        max-height: 100vh;
        overflow: hidden;
        display: flex;
        align-items: center;
        justify-content: center;
        background-color: #000; /* 이미지 없을 때 대비 */
    }

    img {
        position: absolute;
        width: 100%;
        height: 100%;
        object-fit: cover; /* 이미지가 프레임에 맞게 확대/축소 */
        opacity: 0;
        transition: opacity 0.8s ease-in-out;
    }

    img.selected {
        opacity: 1;
        z-index: 1;
    }
</style>
