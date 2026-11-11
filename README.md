[index.html](https://github.com/user-attachments/files/34696116/index.html)
<!DOCTYPE html>
<html lang="ko">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>플레이어 라운지 | 게임 커뮤니티</title>
  <!-- Tailwind CSS CDN -->
  <script src="https://cdn.tailwindcss.com"></script>
  <script>
    tailwind.config = {
      darkMode: 'class',
      theme: {
        extend: {
          colors: {
            brand: {
              50: '#f0f7ff',
              100: '#e0effe',
              500: '#3b82f6',
              600: '#2563eb',
              700: '#1d4ed8',
            }
          }
        }
      }
    }
  </script>
  <style>
    @import url('https://fonts.googleapis.com/css2?family=Orbitron:wght@500;600;700;800&family=Rajdhani:wght@400;500;600;700&display=swap');

    :root {
      color-scheme: dark;
      --void: #080710;
      --surface: rgba(17, 15, 33, .84);
      --surface-raised: rgba(24, 21, 44, .9);
      --line: rgba(168, 145, 223, .14);
      --muted: #9691ac;
      --paper: #eeebff;
      --violet: #8a2be2;
      --pink: #ff007f;
      --cyan: #00ffff;
      --mono: 'Orbitron', 'Rajdhani', 'Pretendard', 'Segoe UI', sans-serif;
      --display: 'Rajdhani', 'Pretendard', 'Segoe UI', sans-serif;
    }

    * { scrollbar-color: #492278 #100e1b; }
    html { min-height: 100%; background: var(--void); }
    body.bg-slate-50 {
      isolation: isolate;
      position: relative;
      min-height: 100vh;
      overflow-x: hidden;
      background-color: var(--void);
      background-image:
        radial-gradient(ellipse at 8% 1%, rgba(138, 43, 226, .22), transparent 31rem),
        radial-gradient(ellipse at 100% 12%, rgba(255, 0, 127, .12), transparent 29rem),
        radial-gradient(ellipse at 65% 95%, rgba(0, 255, 255, .075), transparent 30rem),
        linear-gradient(rgba(163, 128, 226, .047) 1px, transparent 1px),
        linear-gradient(90deg, rgba(163, 128, 226, .047) 1px, transparent 1px);
      background-size: auto, auto, auto, 54px 54px, 54px 54px;
      color: var(--paper);
      font-family: var(--display);
    }
    body::before,
    body::after {
      position: fixed;
      z-index: -1;
      pointer-events: none;
      content: '';
    }
    body::before {
      inset: -15% -45%;
      background: linear-gradient(115deg, transparent 38%, rgba(138, 43, 226, .035) 48%, rgba(0, 255, 255, .05) 50%, transparent 58%);
      background-size: 100% 100%;
      animation: grid-drift 23s linear infinite;
    }
    body::after {
      inset: 0;
      opacity: .14;
      background: repeating-linear-gradient(0deg, transparent 0, transparent 3px, rgba(0, 0, 0, .28) 4px, rgba(0, 0, 0, .28) 5px);
    }
    @keyframes grid-drift {
      from { transform: translateX(-12%); }
      to { transform: translateX(12%); }
    }
    ::selection { background: rgba(255, 0, 127, .38); color: #fff; }
    header.sticky {
      background: rgba(8, 7, 16, .86);
      border-color: rgba(0, 255, 255, .13);
      box-shadow: 0 1px rgba(0, 255, 255, .08), 0 12px 40px rgba(0, 0, 0, .38);
    }
    header .max-w-6xl { min-height: 76px; }
    header a.group > div:first-child {
      border-radius: 12px;
      background: linear-gradient(145deg, #a046ff, #741bd4 58%, #fb168f);
      box-shadow: 0 0 21px rgba(138, 43, 226, .55), inset 0 1px rgba(255, 255, 255, .27);
    }
    header a.group > div:last-child span:first-child,
    header a.group:hover > div:last-child span:first-child {
      color: #f8f2ff;
      text-shadow: 0 0 18px rgba(196, 126, 255, .52);
    }
    header a.group > div:last-child span:last-child { color: #a9a0be; letter-spacing: .13em; }
    main { position: relative; z-index: 1; }
    .game-discovery {
      position: relative;
      overflow: visible;
      padding: 1.7rem;
      color: var(--paper);
      background:
        radial-gradient(ellipse at 0% 0%, rgba(138, 43, 226, .19), transparent 52%),
        radial-gradient(ellipse at 100% 100%, rgba(0, 255, 255, .09), transparent 48%),
        linear-gradient(133deg, rgba(20, 15, 39, .93), rgba(11, 12, 27, .92));
      border: 1px solid rgba(176, 113, 255, .31);
      border-radius: 18px;
      box-shadow: 0 18px 60px rgba(0, 0, 0, .38), 0 0 34px rgba(138, 43, 226, .11), inset 0 1px rgba(255, 255, 255, .055);
      backdrop-filter: blur(18px);
    }
    .game-discovery::before {
      position: absolute;
      top: -1px;
      left: 18px;
      width: 94px;
      height: 2px;
      background: linear-gradient(90deg, var(--pink), var(--violet), var(--cyan));
      box-shadow: 0 0 15px var(--violet);
      content: '';
    }
    .game-discovery h2,
    #currentBoardTitle,
    #editorPageTitle,
    #detailTitle {
      color: #f8f4ff;
      font-family: var(--mono);
      letter-spacing: .025em;
      text-shadow: 0 0 24px rgba(175, 98, 255, .21);
    }
    .game-discovery p { color: #aaa5bd; }
    #gameSearchInput { min-height: 48px; }
    #gameSearchInput:focus,
    #searchInput:focus,
    #postForm input:focus,
    #postForm textarea:focus,
    #postForm select:focus {
      border-color: var(--cyan);
      box-shadow: 0 0 0 3px rgba(0, 255, 255, .12), 0 0 19px rgba(0, 255, 255, .12);
    }
    #gameSearchSubmit {
      position: relative;
      overflow: hidden;
      color: #090812;
      background: linear-gradient(115deg, #ba71ff, #9b42ee 52%, #ff52b1);
      box-shadow: 0 5px 19px rgba(138, 43, 226, .3);
    }
    #gameSearchSubmit:hover {
      color: white;
      background: linear-gradient(115deg, #cc93ff, #9d43f0 48%, #ff278f);
    }
    #popularGameButtons button {
      border-color: rgba(182, 149, 229, .23);
      background: rgba(17, 15, 34, .74);
      color: #e2d9f6;
      letter-spacing: .015em;
    }
    #popularGameButtons button::before { content: '▸ '; color: var(--cyan); }
    #popularGameButtons button:hover {
      border-color: var(--cyan);
      background: rgba(0, 255, 255, .08);
      color: white;
      box-shadow: 0 0 17px rgba(0, 255, 255, .13);
    }
    #popularGameButtons button span { color: #9d96b3; }
    #boardHeaderSection > div:first-child {
      border-color: rgba(150, 128, 193, .19);
    }
    #boardTabsNav { gap: .35rem; padding: 0 0 .45rem; }
    #boardTabsNav button {
      position: relative;
      margin: .25rem .05rem 0;
      padding: .68rem .9rem;
      color: #aaa3bd;
      border: 1px solid transparent;
      border-radius: 9px;
      transition: color .2s, border-color .2s, background .2s, box-shadow .2s, transform .2s;
    }
    #boardTabsNav button:hover {
      color: white;
      border-color: rgba(177, 110, 255, .24);
      background: rgba(138, 43, 226, .09);
      transform: translateY(-2px);
    }
    #boardTabsNav button.border-blue-600 {
      color: #f0dcff !important;
      border-color: rgba(173, 104, 255, .42);
      background: linear-gradient(125deg, rgba(138, 43, 226, .23), rgba(255, 0, 127, .07));
      box-shadow: 0 0 19px rgba(138, 43, 226, .14), inset 0 0 12px rgba(138, 43, 226, .08);
    }
    #boardTabsNav button.text-blue-600 { color: #f0dcff !important; }
    #boardTabsNav button.border-blue-600::after {
      position: absolute;
      right: 12px;
      bottom: -7px;
      left: 12px;
      height: 2px;
      background: linear-gradient(90deg, var(--violet), var(--pink), var(--cyan));
      box-shadow: 0 0 12px rgba(255, 0, 127, .55);
      content: '';
    }
    #boardTabsNav button > span:first-child { filter: drop-shadow(0 0 5px rgba(202, 141, 255, .38)); }
    #boardTabsNav button span.rounded-full {
      color: #cac2dc;
      background: rgba(145, 124, 180, .15);
    }
    #boardTabsNav button.border-blue-600 span.rounded-full {
      color: #fff;
      background: rgba(138, 43, 226, .43);
    }
    #currentBoardDesc, footer, footer p, .text-slate-400, .text-slate-500 { color: var(--muted) !important; }
    #listView > div:first-of-type,
    #detailView article,
    #detailView > section,
    #editorView > div:nth-child(2) {
      color: var(--paper);
      background: linear-gradient(145deg, rgba(21, 18, 38, .91), rgba(13, 12, 25, .92));
      border-color: var(--line);
      box-shadow: 0 19px 48px rgba(0, 0, 0, .24), inset 0 1px rgba(255, 255, 255, .045);
      backdrop-filter: blur(17px);
    }
    #postListContainer > article {
      position: relative;
      background: linear-gradient(105deg, rgba(23, 19, 42, .62), rgba(13, 12, 25, .2));
      transition: background .2s, box-shadow .2s, transform .2s;
    }
    #postListContainer > article:hover {
      z-index: 1;
      background: linear-gradient(105deg, rgba(55, 27, 80, .72), rgba(16, 23, 40, .82));
      box-shadow: inset 3px 0 var(--cyan), 0 0 28px rgba(138, 43, 226, .12);
      transform: translateY(-2px);
    }
    #postListContainer h2,
    #detailAuthorName,
    #detailCommentsCount,
    #commentSectionCount { color: #f0eaff; }
    #postListContainer article:hover h2 { color: #e8caff; text-shadow: 0 0 15px rgba(182, 117, 255, .35); }
    #postListContainer article > div:last-child { color: #958eaa; }
    #postListContainer article > div:first-child > div:first-child > span:first-child,
    #detailBoardBadge {
      display: inline-flex;
      align-items: center;
      gap: .3rem;
      border-radius: 4px;
      font-family: var(--mono);
      font-size: .66rem;
      letter-spacing: .055em;
      text-transform: uppercase;
    }
    #postListContainer article > div:first-child > div:first-child > span:first-child::before {
      content: '◆';
      font-size: .5rem;
    }
    #postListContainer article > div:first-child > div:first-child > span:first-child.bg-rose-50 {
      color: #ff83bd !important;
      border-color: rgba(255, 0, 127, .37) !important;
      background: rgba(255, 0, 127, .105) !important;
    }
    #postListContainer article > div:first-child > div:first-child > span:first-child.bg-blue-50,
    #postListContainer article > div:first-child > div:first-child > span:first-child.bg-slate-100 {
      color: #c9a0ff !important;
      border-color: rgba(157, 83, 242, .38) !important;
      background: rgba(138, 43, 226, .12) !important;
    }
    #postListContainer article > div:first-child > div:first-child > span:first-child.bg-amber-50 {
      color: #ffd980 !important;
      border-color: rgba(255, 191, 71, .35) !important;
      background: rgba(255, 190, 71, .095) !important;
    }
    #postListContainer article > div:first-child > div:first-child > span:first-child.bg-emerald-50 {
      color: #82f2d5 !important;
      border-color: rgba(0, 255, 187, .31) !important;
      background: rgba(0, 255, 187, .08) !important;
    }
    #postListContainer article > div:first-child > div:first-child > span:nth-child(2) {
      border-radius: 4px;
      color: #81f4ff !important;
      border-color: rgba(0, 255, 255, .25) !important;
      background: rgba(0, 255, 255, .065) !important;
    }
    #detailView article .border-slate-100,
    #detailView section .border-slate-100 { border-color: rgba(165, 143, 209, .15); }
    #detailTitle { color: #f4edff; }
    #detailContent,
    #commentListContainer p { color: #d3cde1; }
    #commentListContainer > div {
      border: 1px solid rgba(166, 139, 211, .11);
      background: rgba(31, 26, 48, .7);
    }
    #commentListContainer > div:hover { background: rgba(44, 34, 65, .82); }
    footer {
      position: relative;
      background: rgba(8, 7, 16, .78);
      border-color: rgba(153, 124, 204, .15);
      backdrop-filter: blur(13px);
    }
    input, textarea, select {
      color: #f1ecff !important;
      background-color: rgba(11, 10, 23, .89) !important;
      border-color: rgba(165, 143, 209, .23) !important;
      color-scheme: dark;
    }
    input::placeholder, textarea::placeholder { color: #78728e !important; }
    input:focus, textarea:focus, select:focus {
      border-color: rgba(0, 255, 255, .66) !important;
      outline: none;
      box-shadow: 0 0 0 3px rgba(0, 255, 255, .1), 0 0 17px rgba(0, 255, 255, .1) !important;
    }
    button {
      transition: filter .2s, transform .2s, box-shadow .2s, background-color .2s, color .2s, border-color .2s;
    }
    button:not(:disabled):hover {
      filter: brightness(1.13);
      transform: translateY(-2px);
      box-shadow: 0 0 17px rgba(138, 43, 226, .2), 0 0 11px rgba(0, 255, 255, .07);
    }
    button:active:not(:disabled) { transform: translateY(0) scale(.98); }
    #authNavContainer button,
    main > div:first-child > div:first-child > button,
    #postForm button[type="submit"],
    #commentFormWrapper button {
      color: #fff;
      border: 1px solid rgba(179, 105, 255, .3);
      background: linear-gradient(120deg, #7923ce, #542095);
      box-shadow: 0 5px 17px rgba(117, 39, 193, .2);
    }
    #authNavContainer button:hover,
    main > div:first-child > div:first-child > button:hover,
    #postForm button[type="submit"]:hover,
    #commentFormWrapper button:hover {
      border-color: rgba(0, 255, 255, .72);
      box-shadow: 0 0 23px rgba(138, 43, 226, .38), 0 0 14px rgba(0, 255, 255, .12);
    }
    #gameSearchResults {
      color: var(--paper);
      background: rgba(16, 14, 31, .98);
      border-color: rgba(0, 255, 255, .28);
      box-shadow: 0 18px 40px rgba(0, 0, 0, .45), 0 0 21px rgba(138, 43, 226, .15);
      backdrop-filter: blur(18px);
    }
    #gameSearchResults button { border-color: rgba(170, 147, 211, .12); }
    #gameSearchResults button:hover { background: rgba(138, 43, 226, .15); }
    #gameSearchResults button span:first-child { color: #f2eaff; }
    #authorActionButtons button {
      border: 1px solid rgba(168, 145, 223, .2);
      background: rgba(31, 25, 47, .82);
    }
    #authorActionButtons button:hover {
      border-color: rgba(0, 255, 255, .5);
      color: #f4eaff;
    }
    #clearSearchBtn { color: #aaa3ba; }
    #clearSearchBtn:hover { color: var(--cyan); }
    .custom-scrollbar::-webkit-scrollbar { width: 6px; height: 6px; }
    .custom-scrollbar::-webkit-scrollbar-track { background: #100e1b; }
    .custom-scrollbar::-webkit-scrollbar-thumb { background: #523079; border-radius: 4px; }
    .custom-scrollbar::-webkit-scrollbar-thumb:hover { background: #9751dc; }
    .bg-white, .bg-slate-50, .bg-slate-100, .bg-blue-50, .bg-rose-50, .bg-amber-50,
    .bg-emerald-50, .bg-indigo-50, .bg-violet-50 {
      background-color: rgba(28, 24, 46, .83) !important;
    }
    .bg-blue-50.text-blue-700,
    .bg-blue-100.text-blue-700 {
      color: #81f4ff !important;
      background-color: rgba(0, 255, 255, .1) !important;
    }
    .bg-rose-50.text-rose-700,
    .bg-rose-100.text-rose-700,
    .bg-rose-50.text-rose-600 {
      color: #ff83bd !important;
      background-color: rgba(255, 0, 127, .11) !important;
    }
    .bg-amber-50.text-amber-700 {
      color: #ffd980 !important;
      background-color: rgba(255, 190, 71, .1) !important;
    }
    .bg-emerald-50.text-emerald-700,
    .bg-emerald-50.text-emerald-900 {
      color: #82f2d5 !important;
      background-color: rgba(0, 255, 187, .095) !important;
    }
    .text-slate-900, .text-slate-800, .text-slate-700, .text-slate-600 { color: #e9e3f6 !important; }
    .text-blue-700, .text-blue-600 { color: #cb9bff !important; }
    .text-rose-700, .text-rose-600 { color: #ff75b7 !important; }
    .text-amber-700, .text-amber-600 { color: #ffd176 !important; }
    .text-emerald-700, .text-emerald-600 { color: #79f4d0 !important; }
    .border-slate-100, .border-slate-200, .border-slate-300 { border-color: rgba(168, 145, 223, .15) !important; }
    .border-blue-100, .border-blue-200 { border-color: rgba(0, 255, 255, .25) !important; }
    .border-rose-100, .border-rose-200 { border-color: rgba(255, 0, 127, .26) !important; }
    .border-amber-100, .border-amber-200 { border-color: rgba(255, 190, 71, .24) !important; }
    .border-emerald-100, .border-emerald-200 { border-color: rgba(0, 255, 187, .24) !important; }
    #loginModal, #registerModal, #confirmModal {
      background-color: rgba(4, 3, 10, .76);
      backdrop-filter: blur(12px);
    }
    #loginModal > div, #registerModal > div, #confirmModal > div {
      color: var(--paper);
      background: linear-gradient(145deg, rgba(28, 22, 48, .98), rgba(12, 11, 25, .99));
      border-color: rgba(174, 108, 255, .28) !important;
      box-shadow: 0 28px 90px rgba(0, 0, 0, .64), 0 0 40px rgba(138, 43, 226, .13);
    }
    #loginModal h2, #registerModal h2, #confirmModal h3 { color: #f6f0ff; font-family: var(--mono); }
    #loginModal form button[type="submit"], #registerModal form button[type="submit"] {
      color: #fff;
      background: linear-gradient(115deg, #922ee2, #6e22b7 58%, #dc187d);
      box-shadow: 0 0 24px rgba(138, 43, 226, .2);
    }
    #postListContainer a[href="http://localhost:3000"] {
      border: 1px solid rgba(0, 255, 255, .4);
      background: linear-gradient(115deg, #7923ce, #542095 58%, #bd176e);
      box-shadow: 0 0 21px rgba(138, 43, 226, .26);
    }
    #toastContainer > div {
      border-color: rgba(175, 145, 221, .23);
      box-shadow: 0 12px 32px rgba(0, 0, 0, .4), 0 0 20px rgba(138, 43, 226, .12);
      backdrop-filter: blur(14px);
    }
    @media (max-width: 640px) {
      header .max-w-6xl { min-height: 66px; }
      .game-discovery { padding: 1.2rem; }
      #boardTabsNav button { padding: .58rem .68rem; }
      #postListContainer > article { padding: 1rem; }
    }
    @media (prefers-reduced-motion: reduce) {
      *, *::before, *::after {
        animation-duration: .01ms !important;
        animation-iteration-count: 1 !important;
        scroll-behavior: auto !important;
        transition-duration: .01ms !important;
      }
    }
  </style>
</head>
<body class="bg-slate-50 text-slate-800 min-h-screen flex flex-col antialiased selection:bg-blue-100 selection:text-blue-700">

  <!-- ==================== 네비게이션 헤더 ==================== -->
  <header class="sticky top-0 z-40 bg-white/95 backdrop-blur border-b border-slate-200 shadow-xs">
    <div class="max-w-6xl mx-auto px-4 sm:px-6 h-16 flex items-center justify-between gap-4">
      <!-- 로고 -->
      <a href="javascript:void(0)" onclick="app.navigateToList('all')" class="flex items-center gap-2.5 group">
        <div class="w-10 h-10 rounded-xl bg-gradient-to-tr from-blue-600 to-indigo-600 flex items-center justify-center text-white shadow-md shadow-blue-500/20 group-hover:scale-105 transition-transform">
          <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 20H5a2 2 0 01-2-2V6a2 2 0 012-2h10a2 2 0 012 2v1m2 13a2 2 0 01-2-2V7m2 13a2 2 0 002-2V9a2 2 0 00-2-2h-2m-4-3H9M7 16h6M7 8h6v4H7V8z"/>
          </svg>
        </div>
        <div class="flex flex-col">
          <span class="whitespace-nowrap font-bold text-lg leading-tight text-slate-900 group-hover:text-blue-600 transition-colors">플레이어 라운지</span>
          <span class="text-xs text-slate-500 font-medium">게임 커뮤니티</span>
        </div>
      </a>

      <!-- 우측 사용자 인증 바 -->
      <div id="authNavContainer" class="flex items-center gap-3">
        <!-- JS로 동적 렌더링 -->
      </div>
    </div>
  </header>

  <!-- ==================== 메인 컨텐츠 영역 ==================== -->
  <main class="max-w-6xl mx-auto px-4 sm:px-6 py-6 w-full flex-1">
    
    <!-- 1. 게시판 탭 바 & 검색 바 (목록 화면에서 표시) -->
    <div id="boardHeaderSection" class="mb-6 space-y-4">
      <!-- 상단 탭 메뉴 -->
      <div class="flex items-center justify-between border-b border-slate-200 overflow-x-auto custom-scrollbar pb-1">
        <nav class="flex gap-2 sm:gap-4 shrink-0" id="boardTabsNav">
          <!-- JS로 동적 생성 -->
        </nav>
        <button onclick="app.openEditor()" class="hidden md:inline-flex items-center gap-1.5 px-4 py-2 bg-blue-600 hover:bg-blue-700 active:scale-95 text-white text-sm font-semibold rounded-lg shadow-sm shadow-blue-500/30 transition-all">
          <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 4v16m8-8H4"/>
          </svg>
          새 글 작성
        </button>
      </div>

      <section id="gameSearchSection" class="game-discovery space-y-3">
        <div class="flex flex-col lg:flex-row lg:items-end justify-between gap-3">
          <div>
            <h2 class="text-lg font-bold">어떤 게임 이야기를 찾고 있나요?</h2>
            <p class="text-xs mt-1">모바일과 PC 게임을 검색해 플레이어의 대화와 공략을 둘러보세요.</p>
          </div>
          <div class="relative w-full sm:max-w-md">
            <div class="flex gap-2">
              <input id="gameSearchInput" type="search" autocomplete="off" placeholder="예: 원신, 마인크래프트, 발로란트"
                     oninput="app.searchGames(this.value)"
                     onkeydown="if(event.key==='Enter'){event.preventDefault();app.applyGameSearch();}"
                     class="min-w-0 flex-1 px-3.5 py-2.5 text-sm bg-white border border-slate-300 rounded-lg focus:outline-none focus:border-blue-500 focus:ring-2 focus:ring-blue-100 shadow-xs">
              <button id="gameSearchSubmit" onclick="app.applyGameSearch()" class="px-4 py-2.5 text-sm font-bold rounded-lg transition">게임 검색</button>
            </div>
            <div id="gameSearchResults" class="hidden absolute z-30 top-full mt-1 w-full bg-white border border-slate-200 rounded-lg shadow-lg overflow-hidden"></div>
          </div>
        </div>
        <div id="popularGameButtons" class="flex gap-2 overflow-x-auto custom-scrollbar pb-1"></div>
      </section>

      <!-- 보조 툴바: 게시판 설명 & 정렬 및 검색 -->
      <div class="flex flex-col sm:flex-row sm:items-center justify-between gap-3 pt-2">
        <div>
          <h1 id="currentBoardTitle" class="text-xl font-bold text-slate-900 flex items-center gap-2">
            전체 게시글
          </h1>
          <p id="currentBoardDesc" class="text-xs text-slate-500 mt-0.5">
            등록된 모든 게시글을 최신순으로 확인하세요.
          </p>
        </div>

        <div class="flex items-center gap-2">
          <!-- 검색창 -->
          <div class="relative w-full sm:w-64">
            <input type="text" id="searchInput" placeholder="제목, 내용, 작성자 검색..."
                   onkeyup="if(event.key==='Enter') app.handleSearch()"
                   class="w-full pl-9 pr-8 py-2 text-sm bg-white border border-slate-300 rounded-lg focus:outline-none focus:border-blue-500 focus:ring-2 focus:ring-blue-100 transition-all shadow-xs">
            <svg class="w-4 h-4 text-slate-400 absolute left-3 top-2.5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M21 21l-6-6m2-5a7 7 0 11-14 0 7 7 0 0114 0z"/>
            </svg>
            <button id="clearSearchBtn" onclick="app.clearSearch()" class="hidden absolute right-2.5 top-2.5 text-slate-400 hover:text-slate-600">
              <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"/>
              </svg>
            </button>
          </div>

          <!-- 정렬 셀렉트 -->
          <select id="sortSelect" onchange="app.handleSortChange(this.value)"
                  class="bg-white border border-slate-300 text-slate-700 text-sm rounded-lg px-3 py-2 focus:outline-none focus:border-blue-500 focus:ring-2 focus:ring-blue-100 transition shadow-xs">
            <option value="newest">최신순</option>
            <option value="views">조회수순</option>
            <option value="comments">댓글 많은순</option>
          </select>

          <!-- 모바일용 글쓰기 버튼 -->
          <button onclick="app.openEditor()" class="md:hidden inline-flex items-center justify-center p-2 bg-blue-600 text-white rounded-lg shadow-sm">
            <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 4v16m8-8H4"/>
            </svg>
          </button>
        </div>
      </div>
    </div>

    <!-- ==================== 뷰 1: 게시글 목록 (List View) ==================== -->
    <div id="listView" class="space-y-4">
      <div class="bg-white rounded-xl border border-slate-200 shadow-xs overflow-hidden">
        <div id="postListContainer" class="divide-y divide-slate-100">
          <!-- JS로 동적 게시글 리스트 렌더링 -->
        </div>
      </div>

      <!-- 페이지네이션 컨트롤 -->
      <div id="paginationContainer" class="flex items-center justify-center gap-1.5 py-4">
        <!-- JS로 동적 페이지 버튼 생성 -->
      </div>
    </div>

    <!-- ==================== 뷰 2: 게시글 상세 (Detail View) ==================== -->
    <div id="detailView" class="hidden space-y-6">
      <!-- 상단 액션 바 -->
      <div class="flex items-center justify-between">
        <button onclick="app.backToList()" class="inline-flex items-center gap-1 text-sm font-medium text-slate-600 hover:text-slate-900 transition-colors">
          <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M10 19l-7-7m0 0l7-7m-7 7h18"/>
          </svg>
          게시판 목록으로 돌아가기
        </button>

        <!-- 작성자 권한 컨트롤 (본인인 경우에만 표시) -->
        <div id="authorActionButtons" class="hidden items-center gap-2">
          <button onclick="app.openEditorForEdit()" class="inline-flex items-center gap-1 px-3 py-1.5 bg-slate-100 hover:bg-slate-200 text-slate-700 text-xs font-semibold rounded-lg transition">
            <svg class="w-3.5 h-3.5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15.232 5.232l3.536 3.536m-2.036-5.036a2.5 2.5 0 113.536 3.536L6.5 21.036H3v-3.572L16.732 3.732z"/>
            </svg>
            수정
          </button>
          <button onclick="app.confirmDeletePost()" class="inline-flex items-center gap-1 px-3 py-1.5 bg-rose-50 hover:bg-rose-100 text-rose-600 text-xs font-semibold rounded-lg transition">
            <svg class="w-3.5 h-3.5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 7l-.867 12.142A2 2 0 0116.138 21H7.862a2 2 0 01-1.995-1.858L5 7m5 4v6m4-6v6m1-10V4a1 1 0 00-1-1h-4a1 1 0 00-1 1v3M4 7h16"/>
            </svg>
            삭제
          </button>
        </div>
      </div>

      <!-- 본문 카드 -->
      <article class="bg-white rounded-2xl border border-slate-200 shadow-sm p-6 sm:p-8 space-y-6">
        <!-- 헤더 정보 -->
        <div class="border-b border-slate-100 pb-5 space-y-3">
          <div class="flex items-center gap-2">
            <span id="detailBoardBadge" class="px-2.5 py-0.5 text-xs font-semibold rounded-md"></span>
            <span id="detailGameBadge" class="hidden px-2.5 py-0.5 text-xs font-semibold rounded-md bg-blue-50 text-blue-700 border border-blue-100"></span>
            <span id="detailDate" class="text-xs text-slate-400"></span>
          </div>
          <h1 id="detailTitle" class="text-2xl sm:text-3xl font-bold text-slate-900 leading-snug break-words"></h1>
          
          <div class="flex items-center justify-between text-xs text-slate-500 pt-2">
            <div class="flex items-center gap-2.5">
              <div id="detailAuthorAvatar" class="w-8 h-8 rounded-full bg-blue-100 text-blue-700 flex items-center justify-center font-bold text-sm"></div>
              <div>
                <p id="detailAuthorName" class="font-semibold text-slate-800 text-sm"></p>
                <p id="detailAuthorSub" class="text-slate-400 text-[11px]"></p>
              </div>
            </div>
            <div class="flex items-center gap-3">
              <span class="flex items-center gap-1" title="조회수">
                <svg class="w-4 h-4 text-slate-400" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 12a3 3 0 11-6 0 3 3 0 016 0z"/>
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M2.458 12C3.732 7.943 7.523 5 12 5c4.478 0 8.268 2.943 9.542 7-1.274 4.057-5.064 7-9.542 7-4.477 0-8.268-2.943-9.542-7z"/>
                </svg>
                <span id="detailViews">0</span>
              </span>
              <span class="flex items-center gap-1" title="댓글수">
                <svg class="w-4 h-4 text-slate-400" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M8 12h.01M12 12h.01M16 12h.01M21 12c0 4.418-4.03 8-9 8a9.863 9.863 0 01-4.255-.949L3 20l1.395-3.72C3.512 15.042 3 13.574 3 12c0-4.418 4.03-8 9-8s9 3.582 9 8z"/>
                </svg>
                <span id="detailCommentsCount">0</span>
              </span>
            </div>
          </div>
        </div>

        <!-- 본문 텍스트 -->
        <div id="detailContent" class="text-slate-700 leading-relaxed text-base sm:text-lg min-h-[160px] whitespace-pre-wrap break-words"></div>
      </article>

      <!-- 댓글 영역 -->
      <section class="bg-white rounded-2xl border border-slate-200 shadow-sm p-6 sm:p-8 space-y-6">
        <div class="flex items-center justify-between border-b border-slate-100 pb-4">
          <h2 class="text-lg font-bold text-slate-900 flex items-center gap-2">
            <span>댓글</span>
            <span id="commentSectionCount" class="text-blue-600 bg-blue-50 text-xs px-2 py-0.5 rounded-full font-semibold">0</span>
          </h2>
        </div>

        <!-- 댓글 입력 폼 -->
        <div id="commentFormWrapper" class="space-y-2">
          <!-- 비로그인시 가이드 or 로그인시 입력창 렌더링 -->
        </div>

        <!-- 댓글 목록 -->
        <div id="commentListContainer" class="space-y-4 pt-2">
          <!-- 동적 렌더링 -->
        </div>
      </section>
    </div>

    <!-- ==================== 뷰 3: 글 작성 및 수정 (Editor View) ==================== -->
    <div id="editorView" class="hidden space-y-6">
      <div class="flex items-center justify-between">
        <h1 id="editorPageTitle" class="text-2xl font-bold text-slate-900">새 게시글 작성</h1>
        <button onclick="app.cancelEditor()" class="text-sm text-slate-500 hover:text-slate-800 transition">취소하고 돌아가기</button>
      </div>

      <div class="bg-white rounded-2xl border border-slate-200 shadow-sm p-6 sm:p-8 space-y-5">
        <form id="postForm" onsubmit="app.handleSavePost(event)" class="space-y-5">
          <input type="hidden" id="editPostId" value="">

          <!-- 게시판 선택 -->
          <div>
            <label class="block text-xs font-semibold text-slate-600 mb-1.5">게시판 선택 <span class="text-rose-500">*</span></label>
            <select id="formBoardSelect" required class="w-full sm:w-64 px-3.5 py-2.5 text-sm bg-white border border-slate-300 rounded-xl focus:outline-none focus:border-blue-500 focus:ring-2 focus:ring-blue-100 transition shadow-xs font-medium">
              <!-- JS로 옵션 로드 -->
            </select>
          </div>

          <div>
            <label for="formGameInput" class="block text-xs font-semibold text-slate-600 mb-1.5">게임 <span class="text-slate-400 font-normal">선택 사항</span></label>
            <input id="formGameInput" type="text" list="gameCatalogOptions" maxlength="50" autocomplete="off" placeholder="게임을 검색하거나 이름을 직접 입력하세요"
                   class="w-full sm:w-96 px-3.5 py-2.5 text-sm bg-white border border-slate-300 rounded-xl focus:outline-none focus:border-blue-500 focus:ring-2 focus:ring-blue-100 transition shadow-xs">
            <datalist id="gameCatalogOptions"></datalist>
          </div>

          <!-- 제목 -->
          <div>
            <label class="block text-xs font-semibold text-slate-600 mb-1.5">제목 <span class="text-rose-500">*</span></label>
            <input type="text" id="formTitleInput" required placeholder="게시글 제목을 입력해주세요" maxlength="120"
                   class="w-full px-4 py-2.5 text-base bg-white border border-slate-300 rounded-xl focus:outline-none focus:border-blue-500 focus:ring-2 focus:ring-blue-100 transition shadow-xs">
          </div>

          <!-- 본문 -->
          <div>
            <div class="flex items-center justify-between mb-1.5">
              <label class="block text-xs font-semibold text-slate-600">내용 <span class="text-rose-500">*</span></label>
              <span class="text-xs text-slate-400" id="contentLengthHint">0 / 5,000자</span>
            </div>
            <textarea id="formContentInput" required rows="12" maxlength="5000" placeholder="자유롭게 이야기를 작성해보세요. 줄바꿈과 서식이 유지됩니다."
                      oninput="document.getElementById('contentLengthHint').innerText = this.value.length.toLocaleString() + ' / 5,000자'"
                      class="w-full px-4 py-3 text-sm sm:text-base bg-white border border-slate-300 rounded-xl focus:outline-none focus:border-blue-500 focus:ring-2 focus:ring-blue-100 transition shadow-xs leading-relaxed resize-y custom-scrollbar"></textarea>
          </div>

          <!-- 하단 버튼 -->
          <div class="flex items-center justify-end gap-3 pt-4 border-t border-slate-100">
            <button type="button" onclick="app.cancelEditor()" class="px-5 py-2.5 rounded-xl border border-slate-300 text-slate-700 text-sm font-semibold hover:bg-slate-50 transition">
              취소
            </button>
            <button type="submit" id="submitPostBtn" class="px-6 py-2.5 rounded-xl bg-blue-600 hover:bg-blue-700 active:scale-95 text-white text-sm font-semibold shadow-sm shadow-blue-500/30 transition-all">
              게시글 등록
            </button>
          </div>
        </form>
      </div>
    </div>

  </main>

  <!-- ==================== 푸터 ==================== -->
  <footer class="mt-auto border-t border-slate-200 bg-white py-6 text-center text-xs text-slate-400">
    <div class="max-w-6xl mx-auto px-4">
      <p>© 2026 플레이어 라운지. 게임 이야기를 나누는 커뮤니티.</p>
      <p class="mt-1">공지사항 · 자유게시판 · 게임 Q&A · 공략·팁</p>
    </div>
  </footer>

  <!-- ==================== 로그인 모달 ==================== -->
  <div id="loginModal" class="hidden fixed inset-0 z-50 flex items-center justify-center p-4 bg-slate-900/50 backdrop-blur-xs">
    <div class="bg-white rounded-2xl max-w-sm w-full p-6 sm:p-7 shadow-2xl border border-slate-100 space-y-5 animate-in fade-in duration-200">
      <div class="flex items-center justify-between">
        <div>
          <h2 class="text-xl font-bold text-slate-900">로그인</h2>
          <p class="text-xs text-slate-500 mt-0.5">게시판 활동을 시작하세요.</p>
        </div>
        <button onclick="app.closeModal('loginModal')" class="text-slate-400 hover:text-slate-600 p-1">
          <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"/>
          </svg>
        </button>
      </div>

      <form onsubmit="app.handleLogin(event)" class="space-y-3.5">
        <div>
          <label class="block text-xs font-semibold text-slate-600 mb-1">아이디</label>
          <input type="text" id="loginUsername" required placeholder="아이디를 입력하세요"
                 class="w-full px-3.5 py-2 text-sm border border-slate-300 rounded-xl focus:outline-none focus:border-blue-500 focus:ring-2 focus:ring-blue-100 transition">
        </div>
        <div>
          <label class="block text-xs font-semibold text-slate-600 mb-1">비밀번호</label>
          <input type="password" id="loginPassword" required placeholder="비밀번호를 입력하세요"
                 class="w-full px-3.5 py-2 text-sm border border-slate-300 rounded-xl focus:outline-none focus:border-blue-500 focus:ring-2 focus:ring-blue-100 transition">
        </div>
        <button type="submit" class="w-full py-2.5 bg-blue-600 hover:bg-blue-700 text-white rounded-xl font-semibold text-sm shadow-sm transition">
          로그인
        </button>
      </form>

      <div class="text-center pt-2 border-t border-slate-100 text-xs text-slate-500">
        아직 회원이 아니신가요? 
        <button onclick="app.switchModal('loginModal', 'registerModal')" class="text-blue-600 font-bold hover:underline ml-1">회원가입</button>
      </div>
    </div>
  </div>

  <!-- ==================== 회원가입 모달 ==================== -->
  <div id="registerModal" class="hidden fixed inset-0 z-50 flex items-center justify-center p-4 bg-slate-900/50 backdrop-blur-xs">
    <div class="bg-white rounded-2xl max-w-sm w-full p-6 sm:p-7 shadow-2xl border border-slate-100 space-y-5 animate-in fade-in duration-200">
      <div class="flex items-center justify-between">
        <div>
          <h2 class="text-xl font-bold text-slate-900">회원가입</h2>
          <p class="text-xs text-slate-500 mt-0.5">새로운 계정을 생성하세요.</p>
        </div>
        <button onclick="app.closeModal('registerModal')" class="text-slate-400 hover:text-slate-600 p-1">
          <svg class="w-5 h-5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"/>
          </svg>
        </button>
      </div>

      <form onsubmit="app.handleRegister(event)" class="space-y-3.5">
        <div>
          <label class="block text-xs font-semibold text-slate-600 mb-1">아이디</label>
          <input type="text" id="regUsername" required placeholder="영문, 숫자, 밑줄 3~20자" minlength="3" maxlength="20" pattern="[A-Za-z0-9_]{3,20}" autocomplete="username"
                 class="w-full px-3.5 py-2 text-sm border border-slate-300 rounded-xl focus:outline-none focus:border-blue-500 focus:ring-2 focus:ring-blue-100 transition">
        </div>
        <div>
          <label class="block text-xs font-semibold text-slate-600 mb-1">닉네임</label>
          <input type="text" id="regNickname" required placeholder="활동할 닉네임 (2자 이상)" minlength="2" maxlength="15"
                 class="w-full px-3.5 py-2 text-sm border border-slate-300 rounded-xl focus:outline-none focus:border-blue-500 focus:ring-2 focus:ring-blue-100 transition">
        </div>
        <div>
          <label class="block text-xs font-semibold text-slate-600 mb-1">비밀번호</label>
          <input type="password" id="regPassword" required placeholder="8자 이상 입력" minlength="8" maxlength="72" autocomplete="new-password"
                 class="w-full px-3.5 py-2 text-sm border border-slate-300 rounded-xl focus:outline-none focus:border-blue-500 focus:ring-2 focus:ring-blue-100 transition">
        </div>
        <div>
          <label class="block text-xs font-semibold text-slate-600 mb-1">비밀번호 확인</label>
          <input type="password" id="regPasswordConfirm" required placeholder="비밀번호 재입력" minlength="8" maxlength="72" autocomplete="new-password"
                 class="w-full px-3.5 py-2 text-sm border border-slate-300 rounded-xl focus:outline-none focus:border-blue-500 focus:ring-2 focus:ring-blue-100 transition">
        </div>
        <button type="submit" class="w-full py-2.5 bg-blue-600 hover:bg-blue-700 text-white rounded-xl font-semibold text-sm shadow-sm transition">
          가입하기
        </button>
      </form>

      <div class="text-center pt-2 border-t border-slate-100 text-xs text-slate-500">
        이미 계정이 있으신가요? 
        <button onclick="app.switchModal('registerModal', 'loginModal')" class="text-blue-600 font-bold hover:underline ml-1">로그인</button>
      </div>
    </div>
  </div>

  <!-- ==================== 확인 모달 (Confirm Modal) ==================== -->
  <div id="confirmModal" class="hidden fixed inset-0 z-50 flex items-center justify-center p-4 bg-slate-900/50 backdrop-blur-xs">
    <div class="bg-white rounded-2xl max-w-sm w-full p-6 shadow-2xl border border-slate-100 space-y-4">
      <div class="w-12 h-12 rounded-full bg-rose-100 text-rose-600 flex items-center justify-center mx-auto">
        <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 9v2m0 4h.01m-6.938 4h13.856c1.54 0 2.502-1.667 1.732-3L13.732 4c-.77-1.333-2.694-1.333-3.464 0L3.34 16c-.77 1.333.192 3 1.732 3z"/>
        </svg>
      </div>
      <div class="text-center space-y-1">
        <h3 id="confirmModalTitle" class="text-lg font-bold text-slate-900">확인</h3>
        <p id="confirmModalMessage" class="text-xs text-slate-500">정말 진행하시겠습니까?</p>
      </div>
      <div class="grid grid-cols-2 gap-2 pt-2">
        <button onclick="app.closeModal('confirmModal')" class="py-2 px-3 border border-slate-300 text-slate-700 text-sm font-semibold rounded-xl hover:bg-slate-50 transition">
          취소
        </button>
        <button id="confirmModalBtn" class="py-2 px-3 bg-rose-600 hover:bg-rose-700 text-white text-sm font-semibold rounded-xl transition">
          삭제하기
        </button>
      </div>
    </div>
  </div>

  <!-- ==================== 알림 토스트 (Toast Container) ==================== -->
  <div id="toastContainer" class="fixed bottom-5 right-5 z-50 flex flex-col gap-2 max-w-sm w-full pointer-events-none"></div>

  <script src="./app.js" defer></script>
</body>
</html>

