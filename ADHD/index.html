(function() {

  const DEFAULT_LINES = 2;
  const DEFAULT_COLOR = 'rgba(255,255,0,0.3)';
  const OVERLAY_ID = 'adhd-reading-overlay';
  const CONTROLS_ID = 'adhd-reading-controls';
  const STORAGE_KEY = 'adhdReadingPrefs';

  let numLines = DEFAULT_LINES;
  let highlightColor = DEFAULT_COLOR;
  let currentParagraph = 0;
  let paragraphs = [];

  function loadPrefs() {
    try {
      const prefs = JSON.parse(localStorage.getItem(STORAGE_KEY));
      if (prefs) {
        numLines = prefs.numLines || DEFAULT_LINES;
        highlightColor = prefs.highlightColor || DEFAULT_COLOR;
      }
    } catch {}
  }

  function savePrefs() {
    localStorage.setItem(STORAGE_KEY, JSON.stringify({ numLines, highlightColor }));
  }

  function createOverlay() {
    let overlay = document.getElementById(OVERLAY_ID);
    if (!overlay) {
      overlay = document.createElement('div');
      overlay.id = OVERLAY_ID;
      overlay.style.position = 'fixed';
      overlay.style.top = '0';
      overlay.style.left = '0';
      overlay.style.width = '100vw';
      overlay.style.height = '100vh';
      overlay.style.background = 'rgba(0,0,0,0.7)';
      overlay.style.zIndex = '9998';
      overlay.style.pointerEvents = 'none';
      document.body.appendChild(overlay);
    }
    overlay.style.display = 'block';
  }

  function createControls() {
    let controls = document.getElementById(CONTROLS_ID);
    if (!controls) {
      controls = document.createElement('div');
      controls.id = CONTROLS_ID;
      controls.style.position = 'fixed';
      controls.style.bottom = '20px';
      controls.style.right = '20px';
      controls.style.background = '#fff';
      controls.style.padding = '10px 16px';
      controls.style.borderRadius = '8px';
      controls.style.boxShadow = '0 2px 8px rgba(0,0,0,0.2)';
      controls.style.zIndex = '10000';
      controls.innerHTML = `
        <button id="adhd-prev">▲</button>
        <button id="adhd-next">▼</button>
        <button id="adhd-more">+ Line</button>
        <button id="adhd-less">- Line</button>
        <input id="adhd-color" type="color" value="#ffff00" title="Highlight color" style="vertical-align:middle; width:32px; height:32px; border:none; background:none;">
      `;
      document.body.appendChild(controls);
      document.getElementById('adhd-prev').onclick = () => moveFocus(-1);
      document.getElementById('adhd-next').onclick = () => moveFocus(1);
      document.getElementById('adhd-more').onclick = () => { numLines++; savePrefs(); updateHighlight(); };
      document.getElementById('adhd-less').onclick = () => { if (numLines > 1) { numLines--; savePrefs(); updateHighlight(); } };
      document.getElementById('adhd-color').oninput = (e) => { highlightColor = hexToRgba(e.target.value, 0.3); savePrefs(); updateHighlight(); };
    }
  }

  function hexToRgba(hex, alpha) {
    let r = 0, g = 0, b = 0;
    if (hex.length === 7) {
      r = parseInt(hex.slice(1,3), 16);
      g = parseInt(hex.slice(3,5), 16);
      b = parseInt(hex.slice(5,7), 16);
    }
    return `rgba(${r},${g},${b},${alpha})`;
  }

  function updateHighlight() {
    createOverlay();
    paragraphs.forEach((p, i) => {
      p.style.background = (i >= currentParagraph && i < currentParagraph + numLines) ? highlightColor : 'transparent';
      p.style.position = '';
      p.style.zIndex = '';
    });

    if (paragraphs[currentParagraph]) {
      paragraphs[currentParagraph].scrollIntoView({ behavior: 'smooth', block: 'center' });
    }

    positionOverlay();
  }

  function positionOverlay() {
    const overlay = document.getElementById(OVERLAY_ID);
    if (!overlay) return;
    if (!paragraphs[currentParagraph]) return;
    const rects = [];
    for (let i = 0; i < numLines; i++) {
      const p = paragraphs[currentParagraph + i];
      if (p) rects.push(p.getBoundingClientRect());
    }
    if (rects.length === 0) return;

    const top = Math.min(...rects.map(r => r.top));
    const bottom = Math.max(...rects.map(r => r.bottom));
    const left = Math.min(...rects.map(r => r.left));
    const right = Math.max(...rects.map(r => r.right));

    overlay.style.clipPath = `polygon(0 0, 100vw 0, 100vw 100vh, 0 100vh, 0 0, 0 ${top}px, ${left}px ${top}px, ${left}px ${bottom}px, ${right}px ${bottom}px, ${right}px ${top}px, 0 ${top}px)`;
  }


  function moveFocus(delta) {
    currentParagraph = Math.max(0, Math.min(paragraphs.length - numLines, currentParagraph + delta));
    updateHighlight();
  }


  function handleKey(e) {
    if (e.key === 'ArrowDown') { moveFocus(1); e.preventDefault(); }
    if (e.key === 'ArrowUp') { moveFocus(-1); e.preventDefault(); }
  }

  
  function init() {
    loadPrefs();
    paragraphs = Array.from(document.querySelectorAll('#main-content p'));
    if (paragraphs.length === 0) return;
    createOverlay();
    createControls();
    updateHighlight();
    window.addEventListener('scroll', positionOverlay, { passive: true });
    window.addEventListener('resize', positionOverlay);
    window.addEventListener('keydown', handleKey);
  }


  if (document.readyState === 'loading') {
    document.addEventListener('DOMContentLoaded', init);
  } else {
    init();
  }
})(); 
