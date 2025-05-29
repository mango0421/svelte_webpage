<script>
    import NavBar from '../components/NavBar.svelte';

    const photoGroups = [
        {
            date: '2025-03-21',
            photos: [
                {
                    src: '/assets/photos/photo1.jpg',
                    caption: '봄맞이 학교 대청소',
                    likes: 0,
                    comments: []
                },
                {
                    src: '/assets/photos/photo2.jpg',
                    caption: '교내 벚꽃길 걷기',
                    likes: 0,
                    comments: []
                }
            ]
        },
        {
            date: '2025-04-15',
            photos: [
                {
                    src: '/assets/photos/photo3.jpg',
                    caption: '지역 아동센터 봉사',
                    likes: 0,
                    comments: []
                }
            ]
        }
    ];

    function addLike(photo) {
        photo.likes++;
    }

    function addComment(photo, comment) {
        if (comment.trim()) {
            photo.comments.push(comment.trim());
        }
    }
</script>

<NavBar />

<section class="gallery-section">
    <h1>📸 활동 사진</h1>
    {#each photoGroups as group}
        <div class="photo-group">
            <h2>{group.date}</h2>
            <div class="gallery">
                {#each group.photos as photo}
                    <div class="photo-card">
                        <img src={photo.src} alt="활동 사진" />
                        <p class="caption">{photo.caption}</p>
                        <button on:click={() => addLike(photo)}>❤️ 좋아요 {photo.likes}</button>
                        <div class="comments">
                            <h4>💬 댓글</h4>
                            <ul>
                                {#each photo.comments as c}
                                    <li>{c}</li>
                                {/each}
                            </ul>
                            <input placeholder="댓글 작성..." bind:this={photo.inputEl} on:keydown={(e) => e.key === 'Enter' && addComment(photo, e.target.value) && (e.target.value = '')} />
                        </div>
                    </div>
                {/each}
            </div>
        </div>
    {/each}
</section>

<style>
    .gallery-section {
        padding: 2rem;
        max-width: 1200px;
        margin: 0 auto;
    }

    h1 {
        font-size: 2rem;
        margin-bottom: 1.5rem;
        text-align: center;
        color: #0f172a;
    }

    .photo-group {
        margin-bottom: 2.5rem;
    }

    .photo-group h2 {
        font-size: 1.3rem;
        margin-bottom: 1rem;
        color: #374151;
    }

    .gallery {
        display: grid;
        grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
        gap: 1rem;
    }

    .photo-card {
        border-radius: 8px;
        overflow: hidden;
        box-shadow: 0 4px 8px rgba(0,0,0,0.1);
        background-color: #fff;
        padding: 1rem;
    }

    .photo-card img {
        width: 100%;
        height: 200px;
        object-fit: cover;
        display: block;
        transition: transform 0.3s ease;
    }

    .photo-card img:hover {
        transform: scale(1.05);
    }

    .caption {
        font-size: 0.95rem;
        color: #333;
        margin: 0.5rem 0;
    }

    button {
        background: none;
        border: none;
        color: #f97316;
        font-weight: bold;
        cursor: pointer;
        margin-bottom: 0.5rem;
    }

    .comments {
        border-top: 1px solid #eee;
        padding-top: 0.5rem;
    }

    .comments ul {
        list-style: none;
        padding-left: 0;
        margin: 0.5rem 0;
    }

    .comments li {
        font-size: 0.9rem;
        margin-bottom: 0.3rem;
    }

    .comments input {
        width: 100%;
        padding: 0.3rem;
        font-size: 0.9rem;
        border: 1px solid #ccc;
        border-radius: 4px;
    }
</style>
