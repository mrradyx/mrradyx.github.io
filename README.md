<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>La Unión TV | Fluidez y Cristal</title>
    
    <link href="https://fonts.googleapis.com/css2?family=Montserrat:ital,wght@0,700;0,900;1,900&family=Poppins:wght@300;400;600&display=swap" rel="stylesheet">
    
    <style>
        /* Paleta Premium: Negro, Blanco y Oro */
        :root {
            --bg-dark: #050508; 
            --accent-gold: #d4af37;
            --accent-glow: rgba(212, 175, 55, 0.3);
            --text-main: #ffffff;
            --text-muted: rgba(255, 255, 255, 0.7);
            /* Transparencias más marcadas para que luzca el fondo */
            --glass-bg: rgba(255, 255, 255, 0.03);
            --glass-border: rgba(255, 255, 255, 0.15);
            --glass-hover: rgba(255, 255, 255, 0.08);
        }

        * { margin: 0; padding: 0; box-sizing: border-box; }

        body {
            font-family: 'Poppins', sans-serif;
            background-color: var(--bg-dark);
            color: var(--text-main);
            line-height: 1.6;
            overflow-x: hidden;
            min-height: 100vh;
            position: relative;
        }

        /* --- FONDO DINÁMICO (Luces flotantes tras el cristal) --- */
        .bg-bubbles {
            position: fixed;
            top: 0; left: 0; width: 100vw; height: 100vh;
            z-index: -1;
            overflow: hidden;
            pointer-events: none;
        }

        .orb {
            position: absolute;
            border-radius: 50%;
            filter: blur(80px); /* Desenfoque extremo para que parezca luz fluida */
            opacity: 0.5;
            animation: floatOrb 15s infinite alternate ease-in-out;
        }

        .orb-1 { width: 40vw; height: 40vw; background: rgba(212, 175, 55, 0.4); top: -10%; left: -10%; }
        .orb-2 { width: 35vw; height: 35vw; background: rgba(255, 255, 255, 0.2); bottom: -10%; right: -10%; animation-delay: -5s; }
        .orb-3 { width: 30vw; height: 30vw; background: rgba(212, 175, 55, 0.2); top: 40%; left: 40%; animation-delay: -10s; }

        @keyframes floatOrb {
            0% { transform: translate(0, 0) scale(1); }
            100% { transform: translate(100px, -100px) scale(1.2); }
        }

        /* --- PANTALLA DE CARGA --- */
        #loader {
            position: fixed; top: 0; left: 0; width: 100%; height: 100vh;
            background-color: var(--bg-dark);
            display: flex; flex-direction: column; justify-content: center; align-items: center;
            z-index: 9999; transition: opacity 0.5s ease, visibility 0.5s;
        }

        .soccer-ball {
            width: 60px; height: 60px; background-color: var(--accent-gold);
            border-radius: 50%; position: relative;
            box-shadow: inset -10px -10px 15px rgba(0,0,0,0.5), 0 0 20px var(--accent-glow);
            background-image: 
                radial-gradient(circle at 50% 50%, #000 20%, transparent 21%),
                radial-gradient(circle at 0% 50%, #000 15%, transparent 16%),
                radial-gradient(circle at 100% 50%, #000 15%, transparent 16%),
                radial-gradient(circle at 50% 0%, #000 15%, transparent 16%),
                radial-gradient(circle at 50% 100%, #000 15%, transparent 16%);
            animation: bounce 0.6s infinite alternate cubic-bezier(0.5, 0.05, 1, 0.5), spin 2s infinite linear;
        }
        @keyframes bounce { from { transform: translateY(0) scaleY(1.05); } to { transform: translateY(-80px) scaleY(0.95); } }
        @keyframes spin { from { transform: rotate(0deg); } to { transform: rotate(360deg); } }

        /* --- CLASE GLASSMORPHISM (Cristal mejorado) --- */
        .glass-panel {
            background: var(--glass-bg);
            /* El blur hace que las luces del fondo se distorsionen como a través del agua */
            backdrop-filter: blur(16px);
            -webkit-backdrop-filter: blur(16px); 
            border: 1px solid var(--glass-border);
            border-radius: 16px;
            box-shadow: 0 10px 40px rgba(0, 0, 0, 0.5), inset 0 2px 5px rgba(255,255,255,0.1);
        }

        /* --- EFECTO DE LETRAS EN BURBUJA --- */
        .letra-burbuja {
            display: inline-block;
            color: transparent;
            /* Simula el borde de jabón/agua de una burbuja */
            -webkit-text-stroke: 1.5px rgba(255,255,255,0.9);
            /* Reflejo interno de la burbuja */
            background: radial-gradient(circle at 30% 30%, #ffffff 0%, rgba(212, 175, 55, 0.5) 40%, transparent 80%);
            -webkit-background-clip: text;
            text-shadow: 0 10px 20px rgba(0,0,0,0.5);
            animation: flotarLetra 3s infinite alternate ease-in-out;
        }
        /* Para hacer que las letras reboten un poco a destiempo */
        .delay-1 { animation-delay: 0.2s; }
        .delay-2 { animation-delay: 0.4s; }
        .delay-3 { animation-delay: 0.6s; }

        @keyframes flotarLetra {
            0% { transform: translateY(0) scale(1); }
            100% { transform: translateY(-6px) scale(1.05); }
        }

        /* --- NAVEGACIÓN --- */
        nav {
            position: sticky; top: 0; z-index: 100;
            display: flex; justify-content: space-between; align-items: center;
            padding: 15px 5%;
            background: rgba(5, 5, 8, 0.6);
            backdrop-filter: blur(25px);
            border-bottom: 1px solid var(--glass-border);
        }

        .logo {
            font-family: 'Montserrat', sans-serif; font-size: 28px; font-weight: 900;
            text-transform: uppercase; font-style: italic; display: flex; align-items: center; gap: 5px;
        }

        /* --- HERO --- */
        .hero {
            text-align: center; padding: 100px 20px;
            position: relative; z-index: 10;
        }

        .hero h1 {
            font-family: 'Montserrat', sans-serif; font-size: 3.5rem;
            text-transform: uppercase; font-weight: 900; margin-bottom: 15px;
            text-shadow: 0 4px 20px rgba(0,0,0,0.8);
        }

        .hero p { color: var(--text-muted); font-size: 1.15rem; max-width: 600px; margin: 0 auto; }

        /* --- CONTENEDOR GENERAL Y TÍTULOS --- */
        .container { max-width: 1200px; margin: 0 auto; padding: 50px 20px; position: relative; z-index: 10; }

        .section-title {
            font-family: 'Montserrat', sans-serif; font-size: 2.2rem;
            text-transform: uppercase; margin-bottom: 40px;
            display: flex; align-items: center; gap: 15px;
        }
        .section-title span.resalte { color: var(--accent-gold); }

        /* --- TARJETAS DE PARTIDOS --- */
        .matches-grid {
            display: grid; grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
            gap: 25px; margin-bottom: 60px;
        }

        .match-card {
            padding: 25px; display: flex; justify-content: space-between; align-items: center;
            transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
        }
        .match-card:hover {
            background: var(--glass-hover); transform: translateY(-10px);
            border-color: var(--accent-gold);
            box-shadow: 0 20px 40px rgba(0,0,0,0.7), 0 0 20px var(--accent-glow);
        }

        .team { display: flex; flex-direction: column; align-items: center; width: 35%; text-align: center; }
        .crest {
            width: 60px; height: 60px; border-radius: 50%;
            display: flex; align-items: center; justify-content: center;
            font-family: 'Montserrat', sans-serif; font-weight: 900; font-size: 18px;
            color: var(--text-main); border: 2px solid var(--accent-gold);
            margin-bottom: 12px; background: rgba(212, 175, 55, 0.1);
        }
        .team-name { font-size: 0.95rem; font-weight: 600; }
        .score-box { display: flex; flex-direction: column; align-items: center; width: 30%; }
        .status { font-size: 0.75rem; color: var(--accent-gold); text-transform: uppercase; font-weight: 600; margin-bottom: 8px; }
        .score { font-family: 'Montserrat', sans-serif; font-size: 2.2rem; font-weight: 900; color: #fff; text-shadow: 0 0 10px rgba(255,255,255,0.3); }

        /* --- PANEL DISCIPLINARIO --- */
        .disciplinary-panel {
            border-left: 5px solid var(--accent-gold); padding: 30px; margin-bottom: 60px;
        }
        .disciplinary-panel h3 { font-family: 'Montserrat', sans-serif; color: var(--accent-gold); text-transform: uppercase; margin-bottom: 15px; }
        .disciplinary-panel ul { margin-left: 20px; color: var(--text-muted); font-size: 1rem; line-height: 1.8; }
        .disciplinary-panel li strong { color: #fff; }

        /* --- ESTADÍSTICAS --- */
        .stats-grid { display: grid; grid-template-columns: 2fr 1fr; gap: 30px; margin-bottom: 60px; }
        @media (max-width: 900px) { .stats-grid { grid-template-columns: 1fr; } }

        .table-container { overflow-x: auto; padding: 20px; }
        table { width: 100%; border-collapse: collapse; text-align: center; }
        th { color: var(--accent-gold); font-size: 0.85rem; text-transform: uppercase; padding: 15px 10px; font-weight: 600; border-bottom: 1px solid var(--glass-border); }
        td { padding: 15px 10px; border-bottom: 1px solid rgba(255,255,255,0.05); font-size: 0.95rem; }
        tr:hover td { background-color: var(--glass-hover); }
        .team-cell { text-align: left; font-weight: 600; }
        .pos { font-weight: 900; color: var(--accent-gold); }

        .scorers-list { padding: 25px; }
        .scorer-item { display: flex; justify-content: space-between; align-items: center; padding: 15px 0; border-bottom: 1px solid var(--glass-border); }
        .scorer-item:last-child { border-bottom: none; }
        .scorer-info { display: flex; flex-direction: column; }
        .scorer-name { font-weight: 600; font-size: 1.05rem; }
        .scorer-team { font-size: 0.85rem; color: var(--accent-gold); }
        .goals { font-family: 'Montserrat', sans-serif; font-weight: 900; font-size: 1.6rem; color: #fff; }

        /* --- COLLAGE DE FOTOS --- */
        .collage-grid { display: grid; grid-template-columns: repeat(3, 1fr); gap: 20px; align-items: stretch; margin-bottom: 50px; }
        .collage-item { display: flex; justify-content: center; align-items: center; overflow: hidden; transition: transform 0.4s ease; padding: 10px; }
        .collage-item:hover { transform: scale(1.03); z-index: 10; border-color: var(--accent-gold); box-shadow: 0 15px 30px rgba(0,0,0,0.8); }
        .collage-item.destacado { grid-column: span 2; grid-row: span 2; }
        .collage-item iframe { max-width: 100% !important; border-radius: 8px; background: transparent; }

        @media (max-width: 900px) {
            .collage-grid { grid-template-columns: 1fr; }
            .collage-item.destacado { grid-column: span 1; grid-row: span 1; }
        }

        footer { text-align: center; padding: 40px; color: var(--text-muted); font-size: 0.85rem; border-top: 1px solid var(--glass-border); text-transform: uppercase; letter-spacing: 1px; backdrop-filter: blur(10px); }
    </style>
</head>
<body>

    <!-- ORBES FLOTANTES DE FONDO -->
    <div class="bg-bubbles">
        <div class="orb orb-1"></div>
        <div class="orb orb-2"></div>
        <div class="orb orb-3"></div>
    </div>

    <!-- PANTALLA DE CARGA -->
    <div id="loader">
        <div class="soccer-ball"></div>
        <p style="margin-top: 30px; font-family: 'Montserrat'; font-weight: 700; letter-spacing: 3px; color: var(--accent-gold);">CARGANDO...</p>
    </div>

    <nav>
        <div class="logo">
            La Unión 
            <!-- Aplicando el efecto burbuja en el TV -->
            <span class="letra-burbuja delay-1">T</span><span class="letra-burbuja delay-2">V</span>
        </div>
    </nav>

    <header class="hero">
        <h1>
            EL FÚTB<span class="letra-burbuja delay-3">O</span>L DE <br>
            <span style="color: var(--accent-gold);">ALTO CALIBRE</span>
        </h1>
        <p>Transparencia total en la cancha. Sigue el desempeño del fútbol amateur, estadísticas y las mejores galerías de Tlaquepaque y todo Jalisco.</p>
    </header>

    <div class="container">
        
        <h2 id="resultados" class="section-title"><span class="resalte">Últimos</span> Resultad<span class="letra-burbuja delay-1">o</span>s</h2>
        
        <div class="matches-grid">
            <div class="match-card glass-panel">
                <div class="team"><div class="crest">DT</div><span class="team-name">Tlaquepaque</span></div>
                <div class="score-box"><span class="status">Final</span><div class="score">2 - 1</div></div>
                <div class="team"><div class="crest">RC</div><span class="team-name">Cuervos</span></div>
            </div>
            <div class="match-card glass-panel">
                <div class="team"><div class="crest">GF</div><span class="team-name">Galácticos</span></div>
                <div class="score-box"><span class="status">Final</span><div class="score">5 - 4</div></div>
                <div class="team"><div class="crest">LR</div><span class="team-name">La Reta FC</span></div>
            </div>
        </div>

        <div class="disciplinary-panel glass-panel">
            <h3>C<span class="letra-burbuja delay-2">o</span>misión Disciplinaria</h3>
            <ul>
                <li><strong>Jugador:</strong> Carlos Méndez (Cuervos) - Suspensión de 1 partido (Roja directa).</li>
                <li><strong>Aviso de Liga:</strong> Próxima semana se adelantan los horarios por mantenimiento de la cancha 2.</li>
            </ul>
        </div>

        <h2 id="estadisticas" class="section-title"><span class="resalte">Números</span> Oficiales</h2>
        
        <div class="stats-grid">
            <div class="table-container glass-panel">
                <table>
                    <thead>
                        <tr><th>Pos</th><th>Equipo</th><th>JJ</th><th>JG</th><th>JE</th><th>JP</th><th>PTS</th></tr>
                    </thead>
                    <tbody>
                        <tr><td><span class="pos">1</span></td><td class="team-cell">Tlaquepaque</td><td>4</td><td>4</td><td>0</td><td>0</td><td><strong>12</strong></td></tr>
                        <tr><td><span class="pos">2</span></td><td class="team-cell">Galácticos</td><td>4</td><td>3</td><td>1</td><td>0</td><td><strong>10</strong></td></tr>
                        <tr><td><span class="pos">3</span></td><td class="team-cell">Cuervos</td><td>4</td><td>2</td><td>0</td><td>2</td><td><strong>6</strong></td></tr>
                    </tbody>
                </table>
            </div>

            <div class="scorers-list glass-panel">
                <h3 style="color: var(--accent-gold); margin-bottom: 15px; text-transform: uppercase; font-size: 1.1rem;">Top Goleadores</h3>
                <div class="scorer-item">
                    <div class="scorer-info"><span class="scorer-name">A. Ruiz</span><span class="scorer-team">Tlaquepaque</span></div>
                    <span class="goals">8</span>
                </div>
                <div class="scorer-item">
                    <div class="scorer-info"><span class="scorer-name">M. Silva</span><span class="scorer-team">Galácticos</span></div>
                    <span class="goals">6</span>
                </div>
            </div>
        </div>

        <h2 id="multimedia" class="section-title"><span class="resalte">Galería</span> Exclusiva</h2>
        
        <div class="collage-grid">
            <div class="collage-item destacado glass-panel">
                <!-- Tu enlace de Facebook -->
                <iframe src="https://www.facebook.com/plugins/post.php?href=https%3A%2F%2Fwww.facebook.com%2Fpermalink.php%3Fstory_fbid%3Dpfbid05EFHunfXTsy9hx15uk12oD5BQ5GNRgXCp3JdfX4XTKqBj8izP4gDp7ycQcR97cXWl%26id%3D61586438177203&show_text=false&width=500" width="500" height="497" style="border:none;overflow:hidden" scrolling="no" frameborder="0" allowfullscreen="true" allow="autoplay; clipboard-write; encrypted-media; picture-in-picture; web-share"></iframe>
            </div>

            <div class="collage-item glass-panel">
                <iframe src="https://www.facebook.com/plugins/post.php?href=https%3A%2F%2Fwww.facebook.com%2Fpermalink.php%3Fstory_fbid%3Dpfbid05EFHunfXTsy9hx15uk12oD5BQ5GNRgXCp3JdfX4XTKqBj8izP4gDp7ycQcR97cXWl%26id%3D61586438177203&show_text=false&width=350" width="350" height="350" style="border:none;overflow:hidden" scrolling="no" frameborder="0" allowfullscreen="true" allow="autoplay; clipboard-write; encrypted-media; picture-in-picture; web-share"></iframe>
            </div>

            <div class="collage-item glass-panel">
                <iframe src="https://www.facebook.com/plugins/post.php?href=https%3A%2F%2Fwww.facebook.com%2Fpermalink.php%3Fstory_fbid%3Dpfbid05EFHunfXTsy9hx15uk12oD5BQ5GNRgXCp3JdfX4XTKqBj8izP4gDp7ycQcR97cXWl%26id%3D61586438177203&show_text=false&width=350" width="350" height="350" style="border:none;overflow:hidden" scrolling="no" frameborder="0" allowfullscreen="true" allow="autoplay; clipboard-write; encrypted-media; picture-in-picture; web-share"></iframe>
            </div>
        </div>
    </div>

    <footer>
        <p>&copy; 2026 La Unión TV. Transparencia y pasión en la cancha.</p>
    </footer>

    <script>
        window.addEventListener('load', function() {
            setTimeout(function() {
                const loader = document.getElementById('loader');
                loader.style.opacity = '0';
                loader.style.visibility = 'hidden';
            }, 2000);
        });
    </script>

</body>
</html>
