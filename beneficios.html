/* =====================================================================
   rctag — efeitos compartilhados por todas as páginas
   WHATSAPP: troque pelo número real (DDI + DDD + número, só dígitos).
   ===================================================================== */
window.RCTAG = window.RCTAG || {};
RCTAG.whatsapp = '5561983544077';   // (61) 98354-4077
RCTAG.reduceMotion = window.matchMedia('(prefers-reduced-motion: reduce)').matches;
RCTAG.waLink = text => 'https://wa.me/' + RCTAG.whatsapp + '?text=' + encodeURIComponent(text);

document.addEventListener('DOMContentLoaded', () => {
  // WhatsApp buttons that the page did not set up itself
  document.querySelectorAll('.js-wa').forEach(a => {
    if(a.getAttribute('href') && a.getAttribute('href') !== '#') return;
    const plan = a.dataset.plan;
    a.href = RCTAG.waLink(plan ? `Olá! Quero a placa rctag, plano ${plan}.` : 'Olá! Quero saber mais sobre a placa rctag.');
  });

  // mobile menu
  const btn = document.querySelector('.menu-btn'), nav = document.querySelector('.nav');
  if(btn && nav){
    const set = open => { nav.classList.toggle('open', open); btn.setAttribute('aria-expanded', open); };
    btn.addEventListener('click', () => set(!nav.classList.contains('open')));
    nav.addEventListener('click', e => { if(e.target.closest('a')) set(false); });
    document.addEventListener('keydown', e => { if(e.key === 'Escape') set(false); });
  }

  // header turns light-on-dark while it sits over a dark band
  const top = document.querySelector('.top'), bands = [...document.querySelectorAll('.dark-band')];
  if(top && bands.length){
    const chk = () => { const y = 32; top.classList.toggle('on-dark', bands.some(b => { const r = b.getBoundingClientRect(); return r.top <= y && r.bottom > y; })); };
    window.addEventListener('scroll', chk, { passive:true }); chk();
  }

  // reveal: blocks rise out of depth as they enter
  const rv = document.querySelectorAll('[data-reveal]');
  if('IntersectionObserver' in window && !RCTAG.reduceMotion){
    const io = new IntersectionObserver(es => es.forEach(e => { if(e.isIntersecting){ e.target.classList.add('in'); io.unobserve(e.target); } }), { rootMargin:'0px 0px -8% 0px' });
    rv.forEach(el => io.observe(el));
  } else rv.forEach(el => el.classList.add('in'));

  // tilt: cards lean toward the pointer, with a moving glare
  if(!RCTAG.reduceMotion && window.matchMedia('(hover: hover)').matches){
    document.querySelectorAll('[data-tilt]').forEach(el => {
      const max = +el.dataset.tilt || 10;
      if(!el.querySelector('.glare-fx')){ const g = document.createElement('i'); g.className = 'glare-fx'; el.appendChild(g); }
      el.addEventListener('pointermove', e => {
        const r = el.getBoundingClientRect(), x = (e.clientX - r.left) / r.width, y = (e.clientY - r.top) / r.height;
        el.classList.add('tilting');
        el.style.transform = `perspective(1000px) rotateX(${(.5 - y) * max}deg) rotateY(${(x - .5) * max}deg) translateZ(0)`;
        el.style.setProperty('--gx', x*100 + '%'); el.style.setProperty('--gy', y*100 + '%');
      });
      el.addEventListener('pointerleave', () => { el.classList.remove('tilting'); el.style.transform = ''; });
    });
  }
});

/* ---------- three.js helpers (usados em O produto e Para o seu negócio) ---------- */
RCTAG.loadPlateTexture = (THREE, cb) => {
  const img = new Image();
  const tex = new THREE.Texture(img);
  img.onload = () => { tex.needsUpdate = true; cb && cb(tex); };
  img.src = 'img/placa-rctag.webp';
  tex.anisotropy = 8;
  if('encoding' in tex) tex.encoding = THREE.sRGBEncoding;
  return tex;
};

// Rounded-rectangle acrylic plate: clear beveled body + the real printed face.
RCTAG.makePlate = (THREE, tex, opt = {}) => {
  const w = opt.w || 2.2, h = w * 952/1128, d = opt.d || .1, r = w * .05;
  const shape = new THREE.Shape();
  shape.moveTo(-w/2 + r, -h/2); shape.lineTo(w/2 - r, -h/2); shape.quadraticCurveTo(w/2, -h/2, w/2, -h/2 + r);
  shape.lineTo(w/2, h/2 - r); shape.quadraticCurveTo(w/2, h/2, w/2 - r, h/2); shape.lineTo(-w/2 + r, h/2);
  shape.quadraticCurveTo(-w/2, h/2, -w/2, h/2 - r); shape.lineTo(-w/2, -h/2 + r); shape.quadraticCurveTo(-w/2, -h/2, -w/2 + r, -h/2);
  const geo = new THREE.ExtrudeGeometry(shape, { depth:d, bevelEnabled:true, bevelThickness:.018, bevelSize:.018, bevelSegments:4, curveSegments:10 });
  geo.translate(0, 0, -d/2);
  const body = new THREE.Mesh(geo, new THREE.MeshPhysicalMaterial({ color:0xdfeeff, roughness:.08, metalness:0, clearcoat:1, clearcoatRoughness:.05, transparent:true, opacity:.55 }));
  const face = new THREE.Mesh(new THREE.PlaneGeometry(w * .985, h * .985), new THREE.MeshStandardMaterial({ map:tex, roughness:.35, metalness:0, transparent:true, alphaTest:.35 }));
  face.position.z = d/2 + .02;
  const back = new THREE.Mesh(new THREE.PlaneGeometry(w * .96, h * .96), new THREE.MeshStandardMaterial({ color:0xf2f5fa, roughness:.6 }));
  back.position.z = -d/2 - .005; back.rotation.y = Math.PI;
  const g = new THREE.Group(); g.add(body, face, back);
  g.userData = { w, h, d, face, body, back };
  return g;
};

// Soft glowing dot texture for particles and halos.
RCTAG.glowTexture = (THREE, rgb = '120,190,255') => {
  const c = document.createElement('canvas'); c.width = c.height = 128;
  const x = c.getContext('2d'), g = x.createRadialGradient(64,64,0,64,64,64);
  g.addColorStop(0, `rgba(${rgb},1)`); g.addColorStop(.25, `rgba(${rgb},.55)`); g.addColorStop(1, `rgba(${rgb},0)`);
  x.fillStyle = g; x.fillRect(0,0,128,128);
  return new THREE.CanvasTexture(c);
};

// Drifting bokeh particles like the scroll-world videos.
RCTAG.makeDust = (THREE, n = 260, spread = 18) => {
  const pos = new Float32Array(n*3), rnd = () => Math.random() - .5;
  for(let i=0;i<n;i++){ pos[i*3] = rnd()*spread; pos[i*3+1] = rnd()*spread*.6; pos[i*3+2] = rnd()*spread*.8 - 4; }
  const geo = new THREE.BufferGeometry(); geo.setAttribute('position', new THREE.BufferAttribute(pos, 3));
  const mat = new THREE.PointsMaterial({ size:.16, map:RCTAG.glowTexture(THREE), transparent:true, depthWrite:false, blending:THREE.AdditiveBlending, opacity:.85 });
  return new THREE.Points(geo, mat);
};

RCTAG.starShape = (THREE, r = .5) => {
  const s = new THREE.Shape();
  for(let i=0;i<10;i++){ const a = Math.PI/2 + i*Math.PI/5, rr = i%2 ? r*.45 : r; const x = Math.cos(a)*rr, y = Math.sin(a)*rr; i ? s.lineTo(x,y) : s.moveTo(x,y); }
  s.closePath(); return s;
};

// Renderer sized to its canvas, paused when off screen.
RCTAG.stage = (THREE, canvas, draw) => {
  let gl = null;
  try { gl = canvas.getContext('webgl2') || canvas.getContext('webgl'); } catch(e){}
  if(!gl) return null;
  const renderer = new THREE.WebGLRenderer({ canvas, context:gl, antialias:true, alpha:true });
  renderer.setPixelRatio(Math.min(window.devicePixelRatio || 1, 2));
  if('outputEncoding' in renderer) renderer.outputEncoding = THREE.sRGBEncoding;
  const camera = new THREE.PerspectiveCamera(35, 1, .1, 200);
  const scene = new THREE.Scene();
  const size = () => { const w = canvas.clientWidth, h = canvas.clientHeight; renderer.setSize(w, h, false); camera.aspect = w/h; camera.updateProjectionMatrix(); };
  size(); window.addEventListener('resize', size);
  let visible = true;
  if('IntersectionObserver' in window) new IntersectionObserver(es => { visible = es[0].isIntersecting; }).observe(canvas);
  let last = performance.now();
  function loop(now){
    const dt = Math.min(.05, (now - last) / 1000); last = now;
    if(visible){ draw(now/1000, dt); renderer.render(scene, camera); }
    requestAnimationFrame(loop);
  }
  requestAnimationFrame(loop);   // first frame after the caller has built its scene
  return { renderer, camera, scene, size };
};
