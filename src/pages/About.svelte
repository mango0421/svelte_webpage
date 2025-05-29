<script>
    import NavBar from '../components/NavBar.svelte';
</script>

<NavBar />

<section class="about-section">
    <div class="container">
        <h1>우리는 누구인가요?</h1>

        <div class="intro-block">

            <div class="image">
                <img src="/기봉단푸앙이.png" alt="기획봉사단 캐릭터" />
            </div>

            <div class="text">
                <p>
                    <strong>CAU_Together 기획봉사단</strong><br />
                    CAU Together 기획봉사단은 '같이의 가치' 실현을 목적으로 봉사 활동의 수동적인 참여자였던 학생이 직접 주체가 되어,
                    재학생을 위한 본교 봉사 프로그램을 기획하고 진행하는 중앙대학교 사회봉사단 소속 단체입니다. 운영부, 영상홍보부, 총무부,
                    총 3개의 부서로 구성되어 매 학기 봉사 프로그램 기획팀을 새롭게 구성하며, 교내봉사 프로그램 활성화와 지역사회에 선한 영향력을
                    환원하려는 목적 하에 활동하고 있습니다.
                </p>
            </div>


        </div>

        <h2>주요 활동</h2>
        <ul>
            <li>✔ 지역 사회 아동 대상 교육 봉사</li>
            <li>✔ 기획 워크숍 및 발표회</li>
            <li>✔ 청년 문제 해결 캠페인 기획</li>
            <li>✔ 학교 연계 프로젝트 참여</li>
        </ul>

        <h2>우리의 비전</h2>
        <p>
            단순한 봉사 활동을 넘어서, <em>‘스스로 문제를 정의하고 해결하는 힘’</em>을 기르는 것이 우리의 궁극적인 비전입니다.
            함께 고민하고 실천하며 사회에 긍정적인 영향을 남기는 봉사문화를 만들어가고 있습니다.
        </p>
    </div>
</section>


<style>

    .intro-block {
        display: flex;
        align-items: center;
        justify-content: space-between;
        gap: 2rem;
        margin-top: 1rem;
        flex-wrap: wrap;
    }

    .intro-block .text {
        flex: 1 1 60%;
    }

    .intro-block .image {
        flex: 1 1 35%;
        display: flex;
        justify-content: center;
    }

    .intro-block .image img {
        max-width: 100%;
        height: auto;
        max-height: 280px;
    }


    .about-section {
        padding: 3rem 2rem;
        max-width: 900px;
        margin: 0 auto;
        line-height: 1.7;
    }

    .container {
        background-color: #f9f9f9;
        padding: 2rem;
        border-radius: 12px;
        box-shadow: 0 2px 10px rgba(0,0,0,0.05);
    }

    h1 {
        font-size: 2.2rem;
        margin-bottom: 1rem;
        color: #0f172a;
    }

    h2 {
        margin-top: 2rem;
        font-size: 1.5rem;
        color: #f97316;
    }

    p {
        font-size: 1.05rem;
        color: #333;
        margin-top: 0.5rem;
    }

    ul {
        list-style: none;
        padding-left: 1rem;
        margin-top: 0.5rem;
    }

    li {
        margin-bottom: 0.5rem;
        font-weight: 500;
    }

    em {
        color: #2563eb;
        font-style: normal;
        font-weight: bold;
    }
</style>
