<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Urban City Living - CSS Animation</title>
  <style>
    /* ==========================================================================
       1. Global Styles & Reset
       ========================================================================== */
    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }
    body {
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      line-height: 1.6;
      background-color: #f4f4f9;
      color: #333333;
    }
    header {
      text-align: center;
      padding: 2.5rem 1rem 1.5rem;
      background-color: #111827;
      color: #ffffff;
      box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1);
    }
    header h1 {
      font-size: 2.5rem;
      font-weight: 700;
      letter-spacing: -0.025em;
      margin-bottom: 0.25rem;
    }
    header p {
      font-size: 1.1rem;
      color: #9ca3af;
    }
    /* ==========================================================================
       2. City Stage & Backdrop Layout
       ========================================================================== */
    .city-stage {
      position: relative;
      width: 100%;
      height: 380px;
      background: linear-gradient(to bottom, #0f172a 0%, #1e293b 60%, #334155 100%);
      overflow: hidden; /* Clips the animated car while it is off-screen */
      border-bottom: 4px solid #0f172a;
    }
    /* Distant Skyline Layer */
    .skyline-back {
      position: absolute;
      bottom: 60px;
      left: 0;
      width: 100%;
      height: 180px;
      opacity: 0.35;
    }
    /* Foreground Skyline Layer */
    .skyline-front {
      position: absolute;
      bottom: 60px;
      left: 0;
      width: 100%;
      height: 220px;
      opacity: 0.65;
    }
    /* Road & Street Elements */
    .road {
      position: absolute;
      bottom: 0;
      width: 100%;
      height: 60px;
      background-color: #1e293b;
      border-top: 3px solid #475569;
    }
    /* Dashed Center Road Line */
    .road-line {
      position: absolute;
      top: 50%;
      width: 100%;
      height: 4px;
      background: repeating-linear-gradient(
        90deg,
        #f59e0b 0px,
        #f59e0b 30px,
        transparent 30px,
        transparent 60px
      );
      transform: translateY(-50%);
    }
    /* Stage Header Overlay */
    .stage-title {
      position: absolute;
      top: 15px;
      width: 100%;
      text-align: center;
      color: rgba(255, 255, 255, 0.4);
      font-size: 0.9rem;
      text-transform: uppercase;
      letter-spacing: 0.15em;
      pointer-events: none;
    }
    /* ==========================================================================
       3. Car CSS Animation
       ========================================================================== */
    .driving-car {
      position: absolute;
      bottom: 12px; /* Positioned directly on the road lane */
      width: 220px;  /* Adjust size as needed */
      height: auto;
      z-index: 10;
      filter: drop-shadow(0 10px 8px rgba(0, 0, 0, 0.5));
      /* Keyframe animation assignment */
      animation-name: driveAcross;
      animation-duration: 7s;
      animation-timing-function: linear;
      animation-iteration-count: infinite;
    }
    /* 
       @keyframes Sequence: Moves the vehicle horizontally across 
       from off-screen left (-260px) to past the viewport right (100vw).
    */
    @keyframes driveAcross {
      0% {
        transform: translateX(-260px);
      }
      100% {
        transform: translateX(100vw);
      }
    }
    /* ==========================================================================
       4. Content Section Styling
       ========================================================================== */
    .content-block {
      max-width: 800px;
      margin: 3rem auto;
      padding: 0 1.5rem;
    }
    .content-block h2 {
      font-size: 1.8rem;
      margin-bottom: 1rem;
      color: #0f172a;
    }
    .content-block p {
      margin-bottom: 1.25rem;
      color: #475569;
      font-size: 1.05rem;
    }
    footer {
      text-align: center;
      padding: 2rem 1rem;
      color: #9ca3af;
      font-size: 0.875rem;
      border-top: 1px solid #e2e8f0;
      margin-top: 2rem;
    }
  </style>
</head>
<body>

  <!-- Site Header -->
  <header>
    <h1>Urban City Living</h1>
    <p>Experience the pulse of the city.</p>
  </header>

  <main>
    <!-- Animation Stage Container -->
    <section class="city-stage">
      <div class="stage-title">Animation Stage Container</div>
      <!-- Background Silhouette Skyline -->
      <svg class="skyline-back" preserveAspectRatio="none" viewBox="0 0 1000 200" xmlns="http://www.w3.org/2000/svg">
        <path fill="#475569" d="M0,200 L0,90 L30,90 L30,200 L50,200 L50,110 L90,110 L90,200 L120,200 L120,60 L170,60 L170,200 L200,200 L200,130 L240,130 L240,200 L290,200 L290,40 L340,40 L340,200 L390,200 L390,100 L430,100 L430,200 L480,200 L480,80 L530,80 L530,200 L580,200 L580,120 L620,120 L620,200 L680,200 L680,50 L730,50 L730,200 L790,200 L790,95 L840,95 L840,200 L900,200 L900,70 L950,70 L950,200 L1000,200 Z"/>
      </svg>
      <!-- Foreground Silhouette Skyline -->
      <svg class="skyline-front" preserveAspectRatio="none" viewBox="0 0 1000 200" xmlns="http://www.w3.org/2000/svg">
        <path fill="#0f172a" d="M0,200 L0,120 L40,120 L40,200 L70,200 L70,70 L130,70 L130,200 L160,200 L160,140 L210,140 L210,200 L260,200 L260,30 L320,30 L320,200 L360,200 L360,110 L410,110 L410,200 L460,200 L460,85 L510,85 L510,200 L560,200 L560,135 L610,135 L610,200 L660,200 L660,45 L720,45 L720,200 L770,200 L770,105 L820,105 L820,200 L870,200 L870,75 L930,75 L930,200 L1000,200 Z"/>
      </svg>
      <!-- Road Baseline -->
      <div class="road">
        <div class="road-line"></div>
      </div>
      <!-- Animated Red Sports Car Graphic (Inline Vector SVG) -->
      <div class="driving-car">
        <svg viewBox="0 0 500 160" xmlns="http://www.w3.org/2000/svg">
          <!-- Car Body Base Shadow -->
          <ellipse cx="250" cy="148" rx="220" ry="10" fill="rgba(0,0,0,0.3)" />
          <!-- Main Chassis -->
          <path d="M 40,110 
                   Q 45,85 75,80 
                   C 120,78 160,65 210,42 
                   C 260,20 340,22 390,45 
                   C 420,58 450,75 475,90 
                   Q 490,100 485,115 
                   L 470,125 
                   L 30,125 Z" 
                fill="#dc2626" />    
          <!-- Body Curves & Aerodynamic Highlights -->
          <path d="M 75,80 C 130,75 220,68 380,50" stroke="#b91c1c" stroke-width="4" fill="none" />
          <path d="M 210,42 C 260,20 340,22 390,45" fill="#991b1b" opacity="0.6" />
          <!-- Roof Line / Cabin Shell -->
          <path d="M 150,70 C 185,50 220,30 270,30 C 330,30 365,45 390,55 Z" fill="#111827" />
          <!-- Side Windows -->
          <path d="M 160,68 C 190,52 220,36 265,36 L 265,65 Z" fill="#38bdf8" opacity="0.75" />
          <path d="M 275,36 C 315,36 350,48 375,56 L 275,65 Z" fill="#38bdf8" opacity="0.75" />
          <!-- Front Headlight -->
          <path d="M 460,92 L 482,98 L 465,106 Z" fill="#fef08a" />
          <!-- Headlight Glow -->
          <polygon points="482,95 500,85 500,115 482,102" fill="rgba(254, 240, 138, 0.35)" />
          <!-- Tail Light -->
          <path d="M 35,98 Q 30,102 38,108 Z" fill="#ef4444" stroke="#7f1d1d" stroke-width="2" />
          <!-- Rear Wheel & Rim -->
          <g transform="translate(110, 118)">
            <circle cx="0" cy="0" r="30" fill="#111827" />
            <circle cx="0" cy="0" r="20" fill="#94a3b8" />
            <circle cx="0" cy="0" r="14" fill="#475569" />
            <circle cx="0" cy="0" r="6" fill="#f8fafc" />
            <!-- Spokes -->
            <line x1="-18" y1="0" x2="18" y2="0" stroke="#f8fafc" stroke-width="2.5" />
            <line x1="0" y1="-18" x2="0" y2="18" stroke="#f8fafc" stroke-width="2.5" />
            <line x1="-12" y1="-12" x2="12" y2="12" stroke="#f8fafc" stroke-width="2.5" />
            <line x1="-12" y1="12" x2="12" y2="-12" stroke="#f8fafc" stroke-width="2.5" />
          </g>
          <!-- Front Wheel & Rim -->
          <g transform="translate(390, 118)">
            <circle cx="0" cy="0" r="30" fill="#111827" />
            <circle cx="0" cy="0" r="20" fill="#94a3b8" />
            <circle cx="0" cy="0" r="14" fill="#475569" />
            <circle cx="0" cy="0" r="6" fill="#f8fafc" />
            <!-- Spokes -->
            <line x1="-18" y1="0" x2="18" y2="0" stroke="#f8fafc" stroke-width="2.5" />
            <line x1="0" y1="-18" x2="0" y2="18" stroke="#f8fafc" stroke-width="2.5" />
            <line x1="-12" y1="-12" x2="12" y2="12" stroke="#f8fafc" stroke-width="2.5" />
            <line x1="-12" y1="12" x2="12" y2="-12" stroke="#f8fafc" stroke-width="2.5" />
          </g>
        </svg>
      </div>
    </section>
    <!-- Page Content Article -->
    <article class="content-block">
      <h2>About City Life</h2>
      <p>
        Urban environments are dynamic hubs of continuous activity, architectural design, and perpetual movement. City life represents a fast-paced blend of culture, commerce, and motion, where streets are constantly alive with vehicles, commuters, and changing lights. This digital showcase captures that energetic pulse, translating the fast-moving rhythm of metropolitan streets into a clean, modern web layout.
      </p>
      <p>
        This subtle horizontal CSS animation brings our cityscape to life without distracting from the main text content. Smooth horizontal movement is achieved by binding a CSS @keyframes rule to an absolutely positioned image element. By using translateX() transform functions paired with a linear animation timing curve, the transparent vehicle graphic glides continuously across the viewport at a steady, natural pace. Setting the container to hide overflow ensures the graphic enters and exits the screen cleanly off-stage, maintaining visual balance without disrupting the reading experience.
      </p>
    </article>
  </main>

  <footer>
    <p>&copy; CSS Animation Assignment — Urban City Living</p>
  </footer>

</body>
</html>
