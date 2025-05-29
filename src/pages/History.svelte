<script>
    import NavBar from '../components/NavBar.svelte';

    const history = [
        { year: '2025.03', event: 'CAU_Together 기획봉사단 7기 출범' },
        { year: '2025.05', event: '봉사의 날 프로젝트 ' },
        { year: '2025.05.19', event: '축제 부스 진행' },
        { year: '2025.05.27', event: '사당역 종합 복지관 방문' },
        { year: '2025.07', event: '제주도 출발' }
    ];
</script>

<NavBar />

<section class="history-section">
    <h1>📚 연혁</h1>
    <div class="timeline">
        {#each history as item, i}
            <div class="timeline-item">
                <div class="circle"></div>
                <div class="content">
                    <h2>{item.year}</h2>
                    <p>{item.event}</p>
                </div>
            </div>
        {/each}
    </div>
</section>

<style>
    .history-section {
        max-width: 800px;
        margin: 0 auto;
        padding: 2rem;
    }

    h1 {
        font-size: 2rem;
        text-align: center;
        margin-bottom: 2rem;
        color: #0f172a;
    }

    .timeline {
        position: relative;
        margin-left: 2rem;
        border-left: 3px solid #f97316;
    }

    .timeline-item {
        position: relative;
        padding: 1rem 1rem 1rem 2rem;
        margin-bottom: 1.5rem;
    }

    .circle {
        position: absolute;
        top: 1.2rem;
        left: -0.65rem;
        width: 1rem;
        height: 1rem;
        background: #f97316;
        border-radius: 50%;
    }

    .content h2 {
        font-size: 1.2rem;
        margin: 0 0 0.3rem 0;
        color: #1f2937;
    }

    .content p {
        margin: 0;
        color: #4b5563;
    }
</style>
