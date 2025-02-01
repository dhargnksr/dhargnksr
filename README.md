<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>My Life</title>
    <link href="https://fonts.googleapis.com/css2?family=Quicksand:wght@300;400;600&family=Cormorant+Garamond:wght@300;400;700&display=swap" rel="stylesheet">
    <style>
        :root {
            --primary-color: #8b7b6d;
            --secondary-color: #d3c1b1;
            --background-color: #f9f5f1;
            --text-color: #3a3a3a;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Quicksand', sans-serif;
            background-color: var(--background-color);
            color: var(--text-color);
            line-height: 1.7;
            overflow-x: hidden;
        }

        .folklore-overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-image: url('/api/placeholder/1920/1080');
            background-size: cover;
            background-position: center;
            opacity: 0.1;
            z-index: -1;
        }

        .container {
            width: 90%;
            margin: 0 auto;
            max-width: 1200px;
            padding: 80px 0;
        }

        nav {
            position: fixed;
            top: 0;
            width: 100%;
            background: rgba(249, 245, 241, 0.9);
            padding: 20px 0;
            z-index: 1000;
            box-shadow: 0 2px 10px rgba(0,0,0,0.1);
        }

        nav ul {
            display: flex;
            justify-content: center;
            list-style: none;
        }

        nav ul li {
            margin: 0 25px;
        }

        nav ul li a {
            text-decoration: none;
            color: var(--text-color);
            font-weight: 600;
            letter-spacing: 1px;
            transition: color 0.3s ease;
            font-family: 'Cormorant Garamond', serif;
        }

        nav ul li a:hover {
            color: var(--primary-color);
        }

        section {
            min-height: 100vh;
            display: flex;
            align-items: center;
            position: relative;
            background-color: var(--background-color);
        }

        .section-content {
            display: flex;
            gap: 2rem;
            padding: 2rem;
            max-width: 1200px;
            margin: 0 auto;
            align-items: flex-start;
        }
        .image-container {
    width: 100%;
    height: auto;
    position: relative;
    overflow: hidden;
    border-radius: 15px;
    box-shadow: 0 10px 30px rgba(0,0,0,0.1);
    display: block;
    margin: 0;
    padding: 0;
    line-height: 0;
}

.image-container img {
    width: 100%;
    height: auto;
    object-fit: cover;
    display: block;
    transition: transform 0.5s ease;
    margin: 0;
    padding: 0;
}

.image-container:hover img {
    transform: scale(1.1);
}

        .text-content {
            padding: 30px;
            background: rgba(255,255,255,0.7);
            border-radius: 15px;
            flex: 0 0 60%;
            text-align: left;
        }
        .text-content h2 {
            margin-bottom: 1.5rem;
        }

        .text-content ol {
            padding-left: 1.5rem;
            margin: 0;
        }

        .text-content ul {
            padding-left: 2.5rem;  
            margin: 0.5rem 0;
        }

        .text-content li {
            margin-bottom: 0.5rem;
        }

        .text-content h3 {
            margin-top: 1.5rem;
        }

        .text-content ol li:nth-child(4) + ul {
            margin-left: 1rem;
        }
        #home {
        background: linear-gradient(rgba(0, 0, 0, 0.5), rgba(0, 0, 0, 0.5)),
                    url(beb24ec6ee856fcd27b71f0e573c366c.jpg);
        background-size: cover;
        background-position: center;
        background-attachment: fixed;
        min-height: 100vh;
        display: flex;
        align-items: center;
        justify-content: center;
        color: white;
        } 
        #home .quote-section {
        background: rgba(0, 0, 0, 0.3);
        padding: 2rem;
        border-radius: 15px;
        backdrop-filter: blur(5px);
    } 
    #home blockquote {
        color: white;
        text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.5);
    }
    #home h1 {
        color: white;
        font-size: 3em;
        margin: 20px 0;
        text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.5);
    }

        .quote-section {
            text-align: center;
            max-width: 800px;
            margin: 0 auto;
        }

        blockquote {
            font-family: 'Cormorant Garamond', serif;
            font-size: 2em;
            font-style: italic;
            color: var(--primary-color);
            margin-bottom: 20px;
        }

        h1, h2, h3 {
            font-family: 'Cormorant Garamond', serif;
            color: var(--primary-color);
        }

        .achievements-grid {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 20px;
        }

        .contact-links {
            display: flex;
            justify-content: space-around;
            margin-top: 30px;
        }

        .contact-links a {
            text-decoration: none;
            color: var(--text-color);
            transition: color 0.3s ease;
        }

        .contact-links a:hover {
            color: var(--primary-color);
        }

        #music-player {
            position: fixed;
            bottom: 20px;
            right: 20px;
            background: rgba(249, 245, 241, 0.8);
            padding: 10px;
            border-radius: 50px;
            z-index: 1100;
        }
    </style>
</head>
<body>
    <div class="folklore-overlay"></div>
    
    <audio id="backgroundMusic" autoplay loop>
        <source src="Taylor Swift  Fortnight feat Post Malone.mp3" type="audio/mpeg">
    </audio>
    <script>
         document.addEventListener('DOMContentLoaded', () => {
            const music = document.getElementById('backgroundMusic');
            const musicToggle = document.getElementById('musicToggle');

            music.volume = 0.3;

            musicToggle.addEventListener('click', () => {
                if (music.paused) {
                    music.play();
                } else {
                    music.pause();
                }
            });
        });
    </script>

    <div id="music-player">
        <button id="musicToggle">🎵</button>
    </div>

    <nav>
        <ul>
            <li><a href="#home">Beranda</a></li>
            <li><a href="#about">Tentang</a></li>
            <li><a href="#achievements">Prestasi</a></li>
            <li><a href="#contact">Kontak</a></li>
        </ul>
    </nav>

    <section id="home">
        <div class="container quote-section">
            <blockquote>
                "Thought of callin' ya, but you won't pick up
                <br>
                'Nother fortnight lost in America"
            </blockquote>
            <h1>Saya Dharma Prya Gunaksara.</h1>
            <p>Saya adalah seorang Dosen Kimia di Universitas Indonesia</p>
        </div>
    </section>

    <section id="about">
        <div class="container">
            <div class="section-content">
                <div class="image-container">
                    <img src="IMG_2475.jpg" alt="Foto Profil">
                </div>
                <div class="text-content">
                    <h2>Tentang Saya</h2>
                    <ol>
                        <li>Nama Lengkap: Dharma Prya Gunaksara.</li>
                        <li>TTL: Denpasar, 07 November 2007</li>
                        <li>Tempat Tinggal: Denpasar</li>
                        <li>Pendidikan Terakhir:</li>
                            <ul>
                                <li>Sarjana Pendidikan Kimia di Universitas Pendidikan Indonesia</li>
                                <li>Bachelor of Education Wolfram University</li>
                                <li>Master of Education Colorado University</li>
                                <li>Doctor of Philosophy Tsinghua University</li>
                            </ul> 
                        <li>Golongan: Pembina Utama/IVe</li>
                        <li>NIP: 20071107 204511 1 121</li>
                        <li>Publikasi Terakhir: Neuroscience Education Journal</li>
                    </ol>
                </div>
            </div>
        </div>
    </section>

    <section id="achievements">
        <div class="container">
            <h2>Prestasi Saya</h2>
            <div class="achievements-grid">
                <div class="text-content">
                    <ul>
                        <li>Best Practice Award for National Chemistry MGMP, Indonesia (2035)</li>
                        <li>Best Practice Award for National Chemistry MGMP, Indonesia (2036)</li>
                        <li>Outstanding Lecturer in Organic Chemistry, Universitas Indonesia</li>
                        <li>Young Researcher at BRIN in Exact Sciences</li>
                        <li>Neuroscience Professor at Tsinghua University (2027-2029)</li>
                        <li>B.Ed Valedictorian, Wolfram University</li>
                        <li>M.Ed Valedictorian, Colorado University</li>
                        <li>Curator for INNOPA Innovations in Pharmacology and Chemistry (2039-2045)</li>
                        <li>Curator for BRIN Research in Neurology (2040-2045)</li>
                        <li>Co-Scientist in R&D at Paragon Group (2040-present)</li>
                        <li>Curriculum Curator for Chemistry Textbooks, Ministry of Education (2039-present)</li>
                        <li>Curriculum Curator for Science Textbooks, Ministry of Education (2039-present)</li>
                        <li>Head of Deep Learning Curriculum Development (2048-present)</li>
                        <li>Head of Core Committee for Higher Education Environmental Review, Universitas Indonesia (2040-2044)</li>
                        <li>Curator at Bali Maju Innovation Center (2045-present)</li>
                        <li>Young Researcher in Neuroeducation, WHO (2046-present)</li>
                        <li>Young Researcher in Science Education, UNESCO (2048-2055)</li>
                    </ul>
                </div>
                <div class="image-container">
                    <img src= "FullSizeRender - Copy (16).jpg" alt="Piagam Prestasi">
                </div>
            </div>
        </div>
    </section>

    <section id="contact">
        <div class="container">
            <div class="section-content">
                <div class="image-container">
                    <img src="IMG_0869.jpg" alt="Foto Kontak">
                </div>
                <div class="text-content">
                    <h2>Hubungi Saya</h2>
                    <div class="contact-links">
                        <a href="https://instagram.com/dhargnksr" target="_blank">Instagram</a>
                        <a href="https://linkedin.com/in/dharmagunaksara" target="_blank">LinkedIn</a>
                        <a href="mailto:dtrlpw78@gmail.com">Email</a>
                        <a href="https://twitter.com/dhargnksr" target="_blank">Twitter</a>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <script>
        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                e.preventDefault();
                document.querySelector(this.getAttribute('href')).scrollIntoView({
                    behavior: 'smooth'
                });
            });
        });
    </script>
</body>
</html>
