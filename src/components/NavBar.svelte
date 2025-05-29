<nav class="navbar">
    <div class="logo">
        <img src="/assets/logo.png" alt="로고 이미지" class="logo-img" />
        <span class="logo-text">CAU_Together</span>
    </div>

    <div class="menu">
        <a href="#/">홈</a>
        <a href="#/about">소개</a>
        <a href="#/photos">사진</a>
        <a href="#/history">연혁</a>
        <a href="#/letters" class="hover:text-orange-500">단원들끼리</a>

    </div>

    <div class="login">
        <a href="#/login">login</a>
    </div>
</nav>

<style>
    .navbar {
        display: flex;
        align-items: center;
        justify-content: space-between;
        padding: 1rem 3rem;
        width: 100vw;
        background-color: navajowhite;
        box-shadow: 0 2px 4px rgba(0,0,0,0.1);
        position: sticky;
        top: 0;
        z-index: 1000;
        box-sizing: border-box;
    }

    .logo {
        display: flex;
        align-items: center;
        gap: 0.5rem;
    }

    .logo-img {
        height: 32px;
        width: auto;
        display: block;
    }

    .logo-text {
        font-size: 1.5rem;
        font-weight: bold;
        color: #1f2937;
    }

    .menu {
        display: flex;
        flex: 1;
        justify-content: center;
        gap: 4rem;
    }

    .menu a,
    .login a {
        text-decoration: none;
        color: #333;
        font-weight: 500;
        transition: color 0.2s ease;
    }

    .menu a:hover,
    .login a:hover {
        color: #f97316;
    }
</style>
