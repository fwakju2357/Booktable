<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>PINK RECORD: BOOK ALBUM SHOP</title>
    <link rel="stylesheet" href="style.css">
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=DM+Serif+Display&family=Noto+Sans+KR:wght@300;400;500;700&display=swap" rel="stylesheet">
</head>
<body>

    <nav class="shop-nav">
        <div class="logo">🌸 PINK RECORD SHOP</div>
        <div class="subtitle">BOOKS AS MUSIC ALBUMS</div>
    </nav>

    <main id="main-page">
        <header class="shop-header">
            <h1 class="brand-title">Today's Playlist Book</h1>
            <p class="brand-subtitle">마음의 주파수를 맞추는 이번 수련회 북테이블 추천 앨범</p>
        </header>
        
        <div class="album-grid" id="book-list">
            </div>
    </main>

    <section id="detail-page" class="hidden">
        <div class="detail-container">
            <button id="back-btn">← BACK TO SHOP</button>
            
            <div class="player-layout">
                <div class="player-visual">
                    <div class="cd-case">
                        <img id="detail-img" src="" alt="앨범 재킷">
                        <div class="cd-circle-overlay"></div>
                    </div>
                </div>
                
                <div class="player-info">
                    <div class="track-tag">TRACK INFORMATION</div>
                    <h2 id="detail-title">책 제목</h2>
                    
                    <div class="meta-table">
                        <div class="meta-row">
                            <span class="meta-label">ARTIST / 저자</span>
                            <span id="detail-author" class="meta-value"></span>
                        </div>
                        <div class="meta-row">
                            <span class="meta-label">LABEL / 출판사</span>
                            <span id="detail-publisher" class="meta-value"></span>
                        </div>
                        <div class="meta-row">
                            <span class="meta-label">PRICE / 가격</span>
                            <span id="detail-price" class="meta-value"></span>
                        </div>
                        <div class="meta-row">
                            <span class="meta-label">DJ / 추천인</span>
                            <span id="detail-referrer" class="meta-value"></span>
                        </div>
                    </div>
                    
                    <div class="liner-notes">
                        <h3>LINER NOTES (추천 이유)</h3>
                        <p id="detail-description"></p>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <script>
        // 23권의 데이터가 온전하게 포함된 도서 데이터 리스트입니다.
        const books = [
            {
                "id": 1,
                "title": "하나님은 누구를 사랑하실까?",
                "referrer": "이하임",
                "image": "book1.jpg",
                "author": "필 비셔",
                "publisher": "IVP",
                "price": "12,600원",
                "description": "동화책임에도 새친구나 말씀이 어려운 자들이 쉽게 이해하기 쉽도록 그림책으로 되어 있어 더욱 인상에 깊은 책이기에 추천합니다!"
            },
            {
                "id": 2,
                "title": "스타벅스로 가는 예수님",
                "referrer": "이하임",
                "image": "book2.jpg",
                "author": "김진국",
                "publisher": "세상의 아침",
                "price": "13,500원",
                "description": "사실 이런 책이 될런지 모르겠지만, 예수님을 어렵게 생각하지 않고, 현대의 예수님과 열두 제자들이 어떤 이들일까? 가볍게 생각할 수 있는 책이라 추천하게 되었습니다!"
            },
            {
                "id": 3,
                "title": "팬인가 제자인가",
                "referrer": "김주은",
                "image": "book3.jpg",
                "author": "카일 아이들먼",
                "publisher": "두란노",
                "price": "13,500원",
                "description": "고등학교 시절에 읽은 책인데, 내가 진정으로 예수님을 따르는 제자인가, 아니면 그저 예수님을 좋아하는 팬인가라는 질문을 던지며 스스로의 신앙을 점검해 볼 수 있게 해 준 책입니다."
            },
            {
                "id": 4,
                "title": "지선아 사랑해",
                "referrer": "장하림",
                "image": "book4.jpg",
                "author": "이지선",
                "publisher": "문학동네",
                "price": "12,600원",
                "description": "갑작스러운 사고로 온몸에 화상을 입었음에도 불구하고 하나님을 원망하지 않고 오히려 그 안에서 감사와 사랑을 발견해 나가는 이지선 작가님의 고백이 담긴 책입니다. 고난 속에서도 변함없는 하나님의 신실하심과 일하심을 느낄 수 있어 신앙의 도전과 깊은 감동을 주기 때문에 적극 추천합니다."
            },
            {
                "id": 5,
                "title": "스크루테이프의 편지",
                "referrer": "장하림",
                "image": "book5.jpg",
                "author": "C.S. 루이스",
                "publisher": "홍성사",
                "price": "11,700원",
                "description": "노련한 악마 스크루테이프가 조카 악마 웜우드에게 인간을 유혹하고 신앙을 무너뜨리는 방법에 대해 조언하는 편지 형식의 책입니다. 우리의 일상 속에서 마주하는 사소한 유혹과 영적 침체의 원인을 날카롭고 위트 있게 짚어내어, 스스로의 신앙생활을 돌아보고 영적 분별력을 기르는 데 큰 도움이 되기에 추천합니다."
            },
            {
                "id": 6,
                "title": "한 책 사람",
                "referrer": "임현준",
                "image": "book6.jpg",
                "author": "돈 휘트니",
                "publisher": "CH북스",
                "price": "9,900원",
                "description": "그리스도인들이 하나님의 말씀인 성경을 어떻게 대하고 읽어야 하는지에 대해 깊이 있게 다루는 책입니다. 하나님의 말씀을 사모하고 삶의 중심에 두고자 하는 모든 그리스도인들에게 도전을 줍니다."
            },
            {
                "id": 7,
                "title": "팀 켈러의 탕부 하나님",
                "referrer": "정하은",
                "image": "book7.jpg",
                "author": "팀 켈러",
                "publisher": "두란노",
                "price": "10,800원",
                "description": "누가복음 15장의 '탕자의 비유'를 통해 두 아들 모두가 각자의 방식으로 아버지로부터 멀어져 있음을 보여주며, 복음의 진정한 본질을 깨닫게 해줍니다. 은혜에 진심이신 하나님의 사랑을 느끼고 싶으시다면 추천합니다."
            },
            {
                "id": 8,
                "title": "순전한 기독교",
                "referrer": "김주영",
                "image": "book8.jpg",
                "author": "C.S. 루이스",
                "publisher": "홍성사",
                "price": "11,700원",
                "description": "기독교 신앙의 핵심과 본질을 논리적이고도 명쾌하게 풀어낸 기독교 변증의 고전입니다. 믿음의 기초를 튼튼히 하고 신앙을 지성적으로 이해하고 싶은 분들께 강력히 추천합니다."
            },
            {
                "id": 9,
                "title": "보이지 않는 하나님을 믿는다는 것",
                "referrer": "유세윤",
                "image": "book9.jpg",
                "author": "필립 얀시",
                "publisher": "청림출판",
                "price": "14,400원",
                "description": "신앙생활을 하면서 마주하는 의심과 갈등, 그리고 하나님의 침묵 속에서 어떻게 믿음을 지켜나가야 하는지를 깊이 있고 솔직하게 다룬 책입니다. 눈에 보이지 않는 하나님을 신뢰하는 여정에 깊은 위로와 통찰을 줍니다."
            },
            {
                "id": 10,
                "title": "그 청년 바보의사",
                "referrer": "유세윤",
                "image": "book10.jpg",
                "author": "안수현",
                "publisher": "두란노",
                "price": "11,700원",
                "description": "군 복무 중 서른셋의 젊은 나이로 세상을 떠난 의사 안수현의 삶을 담은 책입니다. 병원 안팎에서 만나는 이들에게 그리스도의 사랑을 온전히 전하며 진정한 제자의 삶이 무엇인지 깊은 울림과 도전을 줍니다."
            },
            {
                "id": 11,
                "title": "래디컬",
                "referrer": "안희정",
                "image": "book11.jpg",
                "author": "데이비드 플랫",
                "publisher": "두란노",
                "price": "13,500원",
                "description": "현대 기독교가 잃어버린 복음의 급진적인 본질을 일깨우며, 안락한 삶 안주에서 벗어나 예수님의 제자로서의 진짜 삶을 살아가도록 촉구하는 책입니다. 타성에 젖은 신앙에 강력한 도전을 선사합니다."
            },
            {
                "id": 12,
                "title": "예수님이라면 어떻게 하실까",
                "referrer": "안희정",
                "image": "book12.jpg",
                "author": "찰스 쉘던",
                "publisher": "크리스천다이제스트",
                "price": "10,800원",
                "description": "선택과 결정의 순간마다 '예수님이라면 어떻게 하실까?'라는 질문을 던지며 삶의 방식을 바꾸어 나가는 성도들의 이야기를 담은 소설입니다. 일상 속에서 주님의 뜻을 구하며 살아가는 구체적인 그리스도인의 삶을 도전합니다."
            },
            {
                "id": 13,
                "title": "목적이 이끄는 삶",
                "referrer": "황은찬",
                "image": "book13.jpg",
                "author": "릭 워렌",
                "publisher": "디모데",
                "price": "15,300원",
                "description": "인간이 창조된 목적과 삶의 진정한 의미를 성경적 원리를 바탕으로 명확히 제시해 주는 책입니다. 매일 한 장씩 읽으며 삶의 방향성을 하나님께 고정하도록 돕는 신앙의 나침반 같은 도서입니다."
            },
            {
                "id": 14,
                "title": "내면세계의 질서와 영적 성장",
                "referrer": "유예본",
                "image": "book14.jpg",
                "author": "고든 맥도날드",
                "publisher": "IVP",
                "price": "13,500원",
                "description": "분주하고 복잡한 현대 사회 속에서 무너지기 쉬운 우리의 내면세계를 어떻게 관리하고 정돈해야 하는지 가이드해 주는 영적 지침서입니다. 내면의 질서를 바로잡아 건강한 영적 성장을 이루고자 하는 청년들에게 추천합니다."
            },
            {
                "id": 15,
                "title": "상처 입은 치유자",
                "referrer": "유예본",
                "image": "book15.jpg",
                "author": "헨리 나우엔",
                "publisher": "두란노",
                "price": "9,000원",
                "description": "자신의 상처와 외로움을 숨기지 않고 오히려 타인을 치유하는 통로로 삼으시는 하나님의 은혜를 다룹니다. 상처받은 이 세상을 살아가는 우리 모두가 서로를 어떻게 돌보며 소망을 전해야 하는지 일깨워줍니다."
            },
            {
                "id": 16,
                "title": "하나님의 모략",
                "referrer": "이요셉",
                "image": "book16.jpg",
                "author": "달라스 윌라드",
                "publisher": "복있는사람",
                "price": "25,200원",
                "description": "예수님이 선포하신 하나님 나라의 복음이 오늘날 우리의 실제 삶 속에서 어떻게 구현될 수 있는지 깊이 있는 영성과 지성으로 풀어낸 명저입니다. 제자로서의 제자도를 회복하고 싶은 분들께 깊은 통찰을 선사합니다."
            },
            {
                "id": 17,
                "title": "영적 형성",
                "referrer": "이요셉",
                "image": "book17.jpg",
                "author": "헨리 나우엔",
                "publisher": "포이에마",
                "price": "12,600원",
                "description": "하나님과의 관계 속에서 우리의 영혼이 어떻게 형성되고 자라가는지, 그 내면의 여정을 돕는 은혜로운 지침서입니다. 일상의 소소한 자리에서 하나님의 임재를 누리며 영적으로 성숙해지길 원하는 분들께 추천합니다."
            },
            {
                "id": 18,
                "title": "새 신자가 가장 궁금해하는 기독교 핵심 질문 42",
                "referrer": "홍세미",
                "image": "book18.jpg",
                "author": "이재철",
                "publisher": "홍성사",
                "price": "11,700원",
                "description": "기독교 신앙을 가지면서 가질 수 있는 실제적이고 본질적인 질문 42가지를 명쾌하고 성경적인 답변으로 정리해 준 책입니다. 신앙의 기초를 다지고 궁금증을 해결하고 싶으신 분들께 추천합니다."
            },
            {
                "id": 19,
                "title": "제자도",
                "referrer": "정찬우",
                "image": "book19.jpg",
                "author": "존 스토트",
                "publisher": "IVP",
                "price": "9,900원",
                "description": "이 시대 속에서 예수 그리스도를 온전히 따르는 '참된 제자'의 삶의 특징 8가지를 명확하게 제시하는 책입니다. 타협 없는 성경적 제자도의 기준을 세우고 실천하고자 하는 그리스도인들의 필독서입니다."
            },
            {
                "id": 20,
                "title": "선교사들",
                "referrer": "정찬우",
                "image": "book20.jpg",
                "author": "양국주",
                "publisher": "서서평",
                "price": "18,000원",
                "description": "척박했던 조선 땅에 찾아와 자신의 목숨과 청춘을 바쳐 복음의 씨앗을 뿌린 신실한 선교사들의 생생한 발자취와 헌신을 기록한 책입니다. 복음의 빚진 자로서 우리의 신앙과 사명을 되돌아보게 만듭니다."
            },
            {
                "id": 21,
                "title": "조선인보다 조선을 더 사랑한 선교사들",
                "referrer": "장하은",
                "image": "book21.jpg",
                "author": "양국주",
                "publisher": "서서평",
                "price": "13,500원",
                "description": "낯설고 가난한 조선 땅을 품고 눈물과 사랑으로 헌신했던 믿음의 선교사들의 일대기를 담았습니다. 그들의 사랑 덕분에 오늘날 우리가 복음을 누릴 수 있음을 기억하게 하며 가슴 뜨거운 은혜를 선물하는 책입니다."
            },
            {
                "id": 22,
                "title": "우리가 하나님을 오해했다",
                "referrer": "김주은",
                "image": "book22.jpg",
                "author": "김형국",
                "publisher": "비아토르",
                "price": "11,700원",
                "description": "우리가 무의식중에 가지고 있는 하나님에 대한 잘못된 편견과 오해들을 성경을 통해 교정해 주고, 참되신 하나님의 성품을 만나도록 인도하는 책입니다. 왜곡된 신앙관을 깨뜨리고 하나님과의 인격적인 관계를 회복하도록 돕습니다."
            },
            {
                "id": 23,
                "title": "하나님의 임재 연습",
                "referrer": "임현준",
                "image": "book23.jpg",
                "author": "로렌스 형제",
                "publisher": "두란노",
                "price": "6,300원",
                "description": "주방의 소소한 가사 노동 속에서도 늘 하나님의 임재를 구하고 주님과 동행했던 로렌스 형제의 거룩한 일상 영성을 담은 고전입니다. 거창한 자리가 아닌 바로 지금 나의 평범한 일상 속에서 하나님을 예배하는 방법을 가르쳐 줍니다."
            }
        ];

        const mainPage = document.getElementById('main-page');
        const detailPage = document.getElementById('detail-page');
        const bookList = document.getElementById('book-list');
        const backBtn = document.getElementById('back-btn');

        // 메인 화면에 23권의 CD 앨범 카드 생성
        function renderBooks() {
            bookList.innerHTML = '';
            books.forEach(book => {
                const albumCard = document.createElement('div');
                albumCard.className = 'album-card';
                albumCard.onclick = () => showDetail(book);

                albumCard.innerHTML = `
                    <div class="album-case-wrapper">
                        <div class="album-cover-box">
                            <img src="${book.image}" alt="${book.title} 표지" class="album-img">
                            <div class="album-vinyl-effect"></div>
                        </div>
                    </div>
                    <div class="album-details">
                        <div class="album-title">${book.title}</div>
                        <div class="album-referrer">💡 Selector: ${book.referrer}</div>
                    </div>
                `;
                bookList.appendChild(albumCard);
            });
        }

        // 상세 정보 출력
        function showDetail(book) {
            document.getElementById('detail-img').src = book.image;
            document.getElementById('detail-title').innerText = book.title;
            document.getElementById('detail-author').innerText = book.author;
            document.getElementById('detail-publisher').innerText = book.publisher;
            document.getElementById('detail-price').innerText = book.price;
            document.getElementById('detail-referrer').innerText = book.referrer;
            document.getElementById('detail-description').innerText = book.description;

            mainPage.classList.add('hidden');
            detailPage.classList.remove('hidden');
            window.scrollTo(0, 0);
        }

        backBtn.onclick = () => {
            detailPage.classList.add('hidden');
            mainPage.classList.remove('hidden');
        };

        renderBooks();
    </script>
</body>
</html>
