<script>
    import NavBar from '../components/NavBar.svelte';
    import { onMount } from 'svelte';

    const membersByMonth = {
        1: [{ name: '단원 1', image: '/assets/members/1.jpg' }],
        2: [{ name: '단원 2', image: '/assets/members/2.jpg' }, { name: '단원 3', image: '/assets/members/3.jpg' }],
        3: [{ name: '단원 4', image: '/assets/members/4.jpg' }],
        4: [{ name: '단원 5', image: '/assets/members/5.jpg' }],
        5: [{ name: '단원 6', image: '/assets/members/6.jpg' }],
        6: [{ name: '단원 7', image: '/assets/members/7.jpg' }],
        7: [{ name: '단원 8', image: '/assets/members/8.jpg' }],
        8: [{ name: '단원 9', image: '/assets/members/9.jpg' }],
        9: [{ name: '단원 10', image: '/assets/members/10.jpg' }],
        10: [{ name: '단원 11', image: '/assets/members/11.jpg' }],
        11: [{ name: '단원 12', image: '/assets/members/12.jpg' }],
        12: [{ name: '단원 13', image: '/assets/members/13.jpg' }]
    };

    let selectedMember = null;
    let letters = {};
    let newTitle = '';
    let newContent = '';
    let selectedLetter = null;

    onMount(() => {
        const stored = localStorage.getItem('letters');
        if (stored) {
            letters = JSON.parse(stored);
        }
    });

    function selectMember(member) {
        selectedMember = member;
        selectedLetter = null;
        newTitle = '';
        newContent = '';
    }

    function submitLetter() {
        if (newTitle.trim() && newContent.trim()) {
            if (!letters[selectedMember.name]) letters[selectedMember.name] = [];
            letters[selectedMember.name].push({ title: newTitle.trim(), content: newContent.trim() });
            localStorage.setItem('letters', JSON.stringify(letters));
            newTitle = '';
            newContent = '';
        }
    }

    function deleteLetter(index) {
        letters[selectedMember.name].splice(index, 1);
        localStorage.setItem('letters', JSON.stringify(letters));
        selectedLetter = null;
    }
</script>

<NavBar />

<main class="container">
    {#if selectedMember}
        <div class="letter-view">
            <img src={selectedMember.image} alt="사진" class="member-photo" />
            <h2>{selectedMember.name}에게 쓴 편지들</h2>
            <ul class="letter-list">
                {#each letters[selectedMember.name] || [] as letter, i}
                    <li on:click={() => selectedLetter = { ...letter, index: i }} class:selected={selectedLetter?.index === i}>
                        {letter.title}
                    </li>
                {/each}
            </ul>

            {#if selectedLetter}
                <div class="letter-content">
                    <h3>{selectedLetter.title}</h3>
                    <p>{selectedLetter.content}</p>
                    <button on:click={() => deleteLetter(selectedLetter.index)}>삭제</button>
                </div>
            {/if}

            <textarea bind:value={newTitle} placeholder="제목을 입력하세요"></textarea>
            <textarea bind:value={newContent} placeholder="내용을 입력하세요..."></textarea>
            <button on:click={submitLetter}>작성하기</button>
            <button on:click={() => (selectedMember = null)}>뒤로가기</button>
        </div>
    {:else}
        <h2>🎂 생일자 목록 (월별)</h2>
        {#each Object.entries(membersByMonth) as [month, members]}
            <h3>{month}월</h3>
            <div class="gallery">
                {#each members as member}
                    <div class="member-card" on:click={() => selectMember(member)}>
                        <img src={member.image} alt={member.name} />
                        <p>{member.name}</p>
                    </div>
                {/each}
            </div>
        {/each}
    {/if}
</main>

<style>
    .container {
        padding: 2rem;
    }

    h2, h3 {
        margin-bottom: 1rem;
    }

    .gallery {
        display: grid;
        grid-template-columns: repeat(auto-fill, minmax(120px, 1fr));
        gap: 1rem;
        margin-bottom: 2rem;
    }

    .member-card {
        background-color: #f3f4f6;
        padding: 1rem;
        text-align: center;
        cursor: pointer;
        border: 1px solid #ccc;
        border-radius: 8px;
        transition: background-color 0.2s;
    }

    .member-card:hover {
        background-color: #e5e7eb;
    }

    .member-card img {
        width: 80px;
        height: 80px;
        object-fit: cover;
        border-radius: 50%;
        margin-bottom: 0.5rem;
    }

    .letter-view {
        max-width: 600px;
        margin: 0 auto;
        text-align: center;
    }

    .member-photo {
        width: 100px;
        height: 100px;
        object-fit: cover;
        border-radius: 50%;
        margin-bottom: 1rem;
    }

    .letter-list {
        list-style: none;
        padding-left: 0;
        margin-bottom: 1rem;
    }

    .letter-list li {
        cursor: pointer;
        margin: 0.3rem 0;
        padding: 0.3rem 0.5rem;
        border-radius: 4px;
    }

    .letter-list li.selected {
        background-color: #f97316;
        color: white;
    }

    .letter-content {
        background: #fff7ed;
        padding: 1rem;
        border-radius: 8px;
        margin-bottom: 1rem;
    }

    textarea {
        width: 100%;
        height: 80px;
        margin-bottom: 1rem;
        padding: 0.5rem;
        font-size: 1rem;
        border-radius: 4px;
        border: 1px solid #ccc;
    }

    button {
        margin: 0.5rem;
        padding: 0.5rem 1rem;
        font-weight: bold;
        border: 2px solid #f97316;
        background-color: white;
        color: #f97316;
        border-radius: 4px;
        cursor: pointer;
    }

    button:hover {
        background-color: #f97316;
        color: white;
    }
</style>
