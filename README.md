<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <meta name="description" content="VELORA — Luxury Resort & Spa demo website." />
  <title>VELORA — Luxury Resort & Spa</title>

  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=DM+Sans:wght@400;500;600&family=Playfair+Display:wght@500;600&display=swap" rel="stylesheet">

  <style>
    :root{
      --ink:#161814;
      --cream:#f5f1e8;
      --paper:#fbfaf6;
      --gold:#b89a61;
      --muted:#77756d;
      --line:rgba(22,24,20,.14);
      --white:#fff;
      --shadow:0 24px 70px rgba(0,0,0,.12);
    }
    *{box-sizing:border-box}
    html{scroll-behavior:smooth}
    body{
      margin:0;
      color:var(--ink);
      background:var(--paper);
      font-family:"DM Sans",sans-serif;
      overflow-x:hidden;
    }
    a{text-decoration:none;color:inherit}
    button,input,select{font:inherit}
    img{display:block;max-width:100%;user-select:none;-webkit-user-drag:none}
    .container{width:min(1180px,calc(100% - 48px));margin:auto}
    .eyebrow{
      display:flex;align-items:center;gap:10px;
      color:var(--gold);font-size:11px;letter-spacing:.22em;text-transform:uppercase;
      font-weight:600
    }
    .eyebrow:before{content:"";width:28px;height:1px;background:currentColor}
    h1,h2,h3,.logo,.quote{font-family:"Playfair Display",serif;font-weight:500}
    h2{font-size:clamp(38px,5vw,68px);line-height:1.02;margin:14px 0 20px}
    p{line-height:1.8;color:var(--muted)}
    .btn{
      border:1px solid rgba(255,255,255,.35);padding:15px 23px;
      display:inline-flex;align-items:center;justify-content:center;gap:10px;
      font-size:12px;letter-spacing:.12em;text-transform:uppercase;cursor:pointer;
      transition:.3s ease;background:transparent;color:#fff
    }
    .btn:hover{background:#fff;color:var(--ink);transform:translateY(-2px)}
    .btn.dark{background:var(--ink);border-color:var(--ink);color:#fff}
    .btn.dark:hover{background:var(--gold);border-color:var(--gold)}
    .btn.light{background:#fff;color:var(--ink);border-color:#fff}
    .btn.light:hover{background:transparent;color:#fff}

    /* NAV */
    .nav{
      position:fixed;top:0;left:0;width:100%;z-index:50;
      color:#fff;transition:.35s ease;border-bottom:1px solid transparent
    }
    .nav.scrolled{background:rgba(20,22,18,.92);backdrop-filter:blur(14px);border-color:rgba(255,255,255,.1)}
    .nav-inner{height:82px;display:flex;align-items:center;justify-content:space-between}
    .logo{font-size:25px;letter-spacing:.16em}
    .logo span{font-family:"DM Sans";font-size:9px;letter-spacing:.35em;display:block;margin-top:-2px;text-align:center}
    .links{display:flex;gap:29px;font-size:12px;letter-spacing:.1em;text-transform:uppercase}
    .links a{opacity:.9;position:relative}
    .links a:after{content:"";position:absolute;left:0;bottom:-7px;width:0;height:1px;background:var(--gold);transition:.3s}
    .links a:hover:after{width:100%}
    .menu{display:none;background:none;border:0;color:#fff;font-size:26px;cursor:pointer}

    /* HERO */
    .hero{
      min-height:100vh;position:relative;display:grid;place-items:center;color:#fff;
      background:
        linear-gradient(90deg,rgba(10,14,12,.66),rgba(10,14,12,.2)),
        url("https://images.unsplash.com/photo-1564501049412-61c2a3083791?auto=format&fit=crop&w=2200&q=88") center/cover;
    }
    .hero:after{content:"";position:absolute;inset:0;background:linear-gradient(0deg,rgba(0,0,0,.48),transparent 50%,rgba(0,0,0,.15))}
    .hero-content{position:relative;z-index:2;width:min(1180px,calc(100% - 48px));padding-top:70px}
    .hero h1{font-size:clamp(58px,9vw,128px);line-height:.88;max-width:850px;margin:18px 0 25px}
    .hero p{max-width:520px;color:rgba(255,255,255,.82);font-size:16px}
    .hero-actions{display:flex;gap:12px;margin-top:32px}
    .scroll{position:absolute;z-index:3;bottom:28px;left:50%;transform:translateX(-50%);font-size:10px;letter-spacing:.22em;text-transform:uppercase;opacity:.8}
    .scroll:after{content:"";display:block;width:1px;height:38px;background:#fff;margin:10px auto 0;opacity:.5}

    /* INTRO */
    section{padding:120px 0}
    .intro{background:var(--cream)}
    .intro-grid{display:grid;grid-template-columns:1fr 1fr;gap:80px;align-items:center}
    .intro-image{height:600px;overflow:hidden}
    .intro-image img{width:100%;height:100%;object-fit:cover;transition:1s}
    .intro-image:hover img{transform:scale(1.04)}
    .intro-copy{max-width:500px}
    .intro-copy p{font-size:15px}
    .signature{font-family:"Playfair Display";font-size:24px;margin-top:30px}

    /* ROOMS */
    .section-head{display:flex;justify-content:space-between;gap:30px;align-items:end;margin-bottom:48px}
    .section-head > div:last-child{max-width:410px}
    .section-head p{margin:0}
    .rooms-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:22px}
    .room-card{background:#fff;box-shadow:0 10px 40px rgba(0,0,0,.06);overflow:hidden}
    .room-img{height:330px;overflow:hidden;position:relative}
    .room-img img{width:100%;height:100%;object-fit:cover;transition:.8s}
    .room-card:hover .room-img img{transform:scale(1.06)}
    .room-info{padding:25px}
    .room-info h3{font-size:27px;margin:0 0 8px}
    .room-info p{font-size:13px;margin:0 0 20px}
    .room-meta{display:flex;justify-content:space-between;border-top:1px solid var(--line);padding-top:16px;font-size:12px}
    .price{font-weight:600}

    /* EXPERIENCE */
    .experience{background:var(--ink);color:#fff}
    .experience p{color:rgba(255,255,255,.6)}
    .experience-grid{display:grid;grid-template-columns:1.1fr .9fr;gap:70px;align-items:center}
    .experience-image{height:650px;overflow:hidden}
    .experience-image img{height:100%;width:100%;object-fit:cover}
    .experiences{display:grid;grid-template-columns:1fr 1fr;gap:28px;margin-top:38px}
    .experience-item{padding-top:20px;border-top:1px solid rgba(255,255,255,.16)}
    .experience-item b{font-family:"Playfair Display";font-size:23px;font-weight:500}
    .experience-item p{font-size:12px;line-height:1.6}

    /* BOOKING */
    .booking-wrap{margin-top:-55px;position:relative;z-index:5}
    .booking{
      background:#fff;box-shadow:var(--shadow);padding:27px;
      display:grid;grid-template-columns:1fr 1fr 1fr auto;gap:0
    }
    .field{padding:0 25px;border-right:1px solid var(--line)}
    .field:first-child{padding-left:0}
    .field label{display:block;text-transform:uppercase;font-size:10px;letter-spacing:.16em;color:var(--muted);margin-bottom:7px}
    .field input,.field select{border:0;outline:0;background:transparent;font-size:15px;color:var(--ink);width:100%;padding:5px 0}
    .booking .btn{margin-left:25px;align-self:center}

    /* OFFER */
    .offer{
      min-height:600px;display:flex;align-items:center;color:#fff;
      background:
        linear-gradient(90deg,rgba(12,15,12,.82),rgba(12,15,12,.12)),
        url("https://images.unsplash.com/photo-1540541338287-41700207dee6?auto=format&fit=crop&w=2000&q=88") center/cover;
    }
    .offer-content{max-width:600px}
    .offer h2{font-size:clamp(45px,6vw,78px)}
    .offer p{color:rgba(255,255,255,.75)}

    /* GALLERY */
    .gallery{display:grid;grid-template-columns:1.2fr .8fr .8fr;grid-auto-rows:260px;gap:12px}
    .gallery-item{overflow:hidden;cursor:pointer;position:relative}
    .gallery-item:first-child{grid-row:span 2}
    .gallery-item:last-child{grid-column:2 / 4}
    .gallery img{width:100%;height:100%;object-fit:cover;transition:.7s}
    .gallery-item:hover img{transform:scale(1.05)}
    .gallery-item:after{content:"View";position:absolute;inset:0;display:grid;place-items:center;background:rgba(0,0,0,.28);color:#fff;opacity:0;transition:.3s;font-size:11px;letter-spacing:.2em;text-transform:uppercase}
    .gallery-item:hover:after{opacity:1}

    /* TESTIMONIAL */
    .testimonial{background:var(--cream);text-align:center}
    .quote{font-size:clamp(30px,4.5vw,58px);line-height:1.18;max-width:950px;margin:25px auto}
    .author{font-size:11px;letter-spacing:.18em;text-transform:uppercase;color:var(--muted)}

    /* LOCATION */
    .location-grid{display:grid;grid-template-columns:1fr 1fr;gap:70px;align-items:stretch}
    .map{
      min-height:480px;
      background:
        linear-gradient(rgba(0,0,0,.15),rgba(0,0,0,.15)),
        url("https://images.unsplash.com/photo-1507525428034-b723cf961d3e?auto=format&fit=crop&w=1500&q=85") center/cover;
      display:flex;align-items:end;padding:30px
    }
    .map-card{background:#fff;padding:25px;max-width:330px;box-shadow:var(--shadow)}
    .map-card h3{margin:0 0 8px;font-size:25px}
    .map-card p{margin:0 0 15px;font-size:13px}

    /* FOOTER */
    footer{background:#10120f;color:#fff;padding:70px 0 25px}
    .footer-grid{display:grid;grid-template-columns:1.5fr 1fr 1fr 1fr;gap:50px}
    footer p,footer a{color:rgba(255,255,255,.55);font-size:13px}
    footer h4{font-size:10px;letter-spacing:.18em;text-transform:uppercase;color:var(--gold);margin:0 0 18px}
    .footer-logo{font-size:35px;font-family:"Playfair Display";letter-spacing:.14em}
    .copyright{border-top:1px solid rgba(255,255,255,.1);margin-top:55px;padding-top:20px;color:rgba(255,255,255,.35);font-size:11px;display:flex;justify-content:space-between}

    /* MODAL */
    .modal{position:fixed;inset:0;background:rgba(0,0,0,.7);z-index:100;display:none;align-items:center;justify-content:center;padding:20px}
    .modal.open{display:flex}
    .modal-box{width:min(560px,100%);background:var(--paper);padding:35px;position:relative;animation:pop .25s ease}
    @keyframes pop{from{transform:translateY(20px);opacity:0}to{transform:none;opacity:1}}
    .close{position:absolute;right:17px;top:13px;border:0;background:none;font-size:28px;cursor:pointer}
    .modal-box h3{font-size:35px;margin:0 0 8px}
    .modal-box p{font-size:13px;margin-top:0}
    .form{display:grid;gap:13px;margin-top:20px}
    .form input,.form select{width:100%;padding:14px;border:1px solid var(--line);background:#fff;outline:0}
    .form .btn{width:100%;margin-top:4px}
    .success{display:none;padding:20px;background:#edf5ed;margin-top:15px;color:#305536;font-size:13px}

    /* LIGHTBOX */
    .lightbox{position:fixed;inset:0;background:rgba(0,0,0,.92);z-index:110;display:none;align-items:center;justify-content:center;padding:30px}
    .lightbox.open{display:flex}
    .lightbox img{max-height:88vh;max-width:92vw;object-fit:contain}
    .lightbox .close{color:#fff;top:18px;right:25px}

    @media(max-width:900px){
      .links{display:none}.menu{display:block}
      .nav.mobile-open .links{display:flex;position:absolute;top:82px;left:0;width:100%;padding:25px;background:#151713;flex-direction:column}
      .intro-grid,.experience-grid,.location-grid{grid-template-columns:1fr;gap:40px}
      .intro-image{height:500px}
      .rooms-grid{grid-template-columns:1fr 1fr}
      .booking{grid-template-columns:1fr 1fr;gap:20px}
      .field{border:0;padding:0}
      .field:first-child{padding-left:0}
      .booking .btn{margin:0;grid-column:1/-1}
      .footer-grid{grid-template-columns:1fr 1fr}
    }
    @media(max-width:620px){
      .container,.hero-content{width:min(100% - 30px,1180px)}
      section{padding:80px 0}
      .hero h1{font-size:57px}
      .hero-actions{flex-direction:column;max-width:260px}
      .rooms-grid{grid-template-columns:1fr}
      .room-img{height:300px}
      .experiences{grid-template-columns:1fr}
      .gallery{grid-template-columns:1fr 1fr;grid-auto-rows:180px}
      .gallery-item:first-child{grid-row:span 2}
      .gallery-item:last-child{grid-column:1/-1}
      .footer-grid{grid-template-columns:1fr}
      .copyright{flex-direction:column;gap:8px}
      .booking{padding:20px;grid-template-columns:1fr}
      .booking .btn{grid-column:auto}
    }
  </style>
</head>

<body>
  <header class="nav" id="nav">
    <div class="container nav-inner">
      <a href="#home" class="logo">VELORA<span>RESORT & SPA</span></a>
      <nav class="links">
        <a href="#rooms">Rooms</a>
        <a href="#experience">Experiences</a>
        <a href="#dining">Dining</a>
        <a href="#gallery">Gallery</a>
        <a href="#contact">Contact</a>
        <a href="#book">Book</a>
      </nav>
      <button class="menu" id="menu" aria-label="Open menu">☰</button>
    </div>
  </header>

  <main>
    <section class="hero" id="home">
      <div class="hero-content">
        <div class="eyebrow">Goa · India</div>
        <h1>Escape to<br>Extraordinary.</h1>
        <p>Where quiet mornings, golden sunsets and effortless luxury come together by the sea.</p>
        <div class="hero-actions">
          <a class="btn light" href="#rooms">Explore Rooms</a>
          <button class="btn" onclick="openBooking()">Book Your Stay</button>
        </div>
      </div>
      <div class="scroll">Scroll to explore</div>
    </section>

    <div class="booking-wrap container" id="book">
      <form class="booking" onsubmit="quickBook(event)">
        <div class="field">
          <label>Check in</label>
          <input id="checkin" type="date" required>
        </div>
        <div class="field">
          <label>Check out</label>
          <input id="checkout" type="date" required>
        </div>
        <div class="field">
          <label>Guests</label>
          <select id="guests">
            <option>2 Adults</option>
            <option>1 Adult</option>
            <option>2 Adults, 1 Child</option>
            <option>2 Adults, 2 Children</option>
            <option>4 Adults</option>
          </select>
        </div>
        <button class="btn dark" type="submit">Check Availability</button>
      </form>
    </div>

    <section class="intro">
      <div class="container intro-grid">
        <div class="intro-image">
          <img src="https://images.unsplash.com/photo-1584132967334-10e028bd69f7?auto=format&fit=crop&w=1200&q=85" alt="Luxury hotel interior" draggable="false">
        </div>
        <div class="intro-copy">
          <div class="eyebrow">The Velora Story</div>
          <h2>A world away from the ordinary.</h2>
          <p>Velora is a private coastal retreat created for slow mornings, long lunches and evenings beneath an endless sky. Every space has been designed to feel intimate, refined and naturally connected to its surroundings.</p>
          <p>From thoughtful service to locally inspired cuisine, every detail is considered so you can simply arrive, exhale and stay awhile.</p>
          <div class="signature">— The Velora Team</div>
        </div>
      </div>
    </section>

    <section id="rooms">
      <div class="container">
        <div class="section-head">
          <div>
            <div class="eyebrow">Stay with us</div>
            <h2>Rooms & Suites</h2>
          </div>
          <div><p>Private spaces, natural textures and views that make it difficult to leave.</p></div>
        </div>

        <div class="rooms-grid">
          <article class="room-card">
            <div class="room-img"><img src="https://images.unsplash.com/photo-1590490360182-c33d57733427?auto=format&fit=crop&w=1200&q=85" alt="Ocean View Suite" draggable="false"></div>
            <div class="room-info">
              <h3>Ocean View Suite</h3>
              <p>Panoramic sea views · King bed · Private balcony</p>
              <div class="room-meta"><span>2 Guests</span><span class="price">₹18,500 / night</span></div>
            </div>
          </article>

          <article class="room-card">
            <div class="room-img"><img src="https://images.unsplash.com/photo-1601918774946-25832a4be0d6?auto=format&fit=crop&w=1200&q=85" alt="Private Pool Villa" draggable="false"></div>
            <div class="room-info">
              <h3>Private Pool Villa</h3>
              <p>Private pool · Garden view · Outdoor lounge</p>
              <div class="room-meta"><span>3 Guests</span><span class="price">₹32,000 / night</span></div>
            </div>
          </article>

          <article class="room-card">
            <div class="room-img"><img src="https://images.unsplash.com/photo-1611892440504-42a792e24d32?auto=format&fit=crop&w=1200&q=85" alt="Presidential Suite" draggable="false"></div>
            <div class="room-info">
              <h3>Presidential Suite</h3>
              <p>Two bedrooms · Ocean terrace · Butler service</p>
              <div class="room-meta"><span>4 Guests</span><span class="price">₹55,000 / night</span></div>
            </div>
          </article>
        </div>
      </div>
    </section>

    <section class="experience" id="experience">
      <div class="container experience-grid">
        <div class="experience-image">
          <img src="https://images.unsplash.com/photo-1544161515-4ab6ce6db874?auto=format&fit=crop&w=1400&q=85" alt="Luxury spa experience" draggable="false">
        </div>
        <div>
          <div class="eyebrow">More than a stay</div>
          <h2>Designed for the senses.</h2>
          <p>From sunrise swims to candlelit dinners, every Velora experience is made to slow time down.</p>
          <div class="experiences">
            <div class="experience-item"><b>Private Beach</b><p>Golden sands, quiet waters and your own corner of the coast.</p></div>
            <div class="experience-item"><b>Signature Spa</b><p>Restorative rituals inspired by local botanicals.</p></div>
            <div class="experience-item" id="dining"><b>Fine Dining</b><p>Seasonal ingredients, coastal flavours and intimate tables.</p></div>
            <div class="experience-item"><b>Sunset Sailing</b><p>Golden-hour cruises designed for unforgettable evenings.</p></div>
          </div>
        </div>
      </div>
    </section>

    <section class="offer">
      <div class="container">
        <div class="offer-content">
          <div class="eyebrow">Limited time</div>
          <h2>A weekend worth remembering.</h2>
          <p>Stay three nights and enjoy your fourth night on us, plus a complimentary spa ritual for two.</p>
          <button class="btn light" onclick="openBooking()">Book this offer</button>
        </div>
      </div>
    </section>

    <section id="gallery">
      <div class="container">
        <div class="section-head">
          <div>
            <div class="eyebrow">Visual journey</div>
            <h2>Life at Velora</h2>
          </div>
        </div>
        <div class="gallery">
          <div class="gallery-item"><img src="https://images.unsplash.com/photo-1505693416388-ac5ce068fe85?auto=format&fit=crop&w=1400&q=85" alt="Luxury bedroom" draggable="false"></div>
          <div class="gallery-item"><img src="https://images.unsplash.com/photo-1540555700478-4be289fbecef?auto=format&fit=crop&w=1000&q=85" alt="Resort spa" draggable="false"></div>
          <div class="gallery-item"><img src="https://images.unsplash.com/photo-1510414842594-a61c69b5ae57?auto=format&fit=crop&w=1000&q=85" alt="Tropical pool" draggable="false"></div>
          <div class="gallery-item"><img src="https://images.unsplash.com/photo-1556742049-0cfed4f6a45d?auto=format&fit=crop&w=1500&q=85" alt="Elegant dining" draggable="false"></div>
        </div>
      </div>
    </section>

    <section class="testimonial">
      <div class="container">
        <div class="eyebrow" style="justify-content:center">Guest stories</div>
        <div class="quote">“From the room to the service, every detail was exceptional. Velora felt less like a hotel and more like our own private paradise.”</div>
        <div class="author">Ananya Sharma · Mumbai</div>
      </div>
    </section>

    <section id="contact">
      <div class="container location-grid">
        <div>
          <div class="eyebrow">Find your way here</div>
          <h2>Meet us by the sea.</h2>
          <p>Velora Resort & Spa<br>Morjim, Goa · India</p>
          <p>Reservations<br>+91 98765 43210<br>stay@veloraresort.com</p>
          <button class="btn dark" onclick="openBooking()">Plan your stay</button>
        </div>
        <div class="map">
          <div class="map-card">
            <h3>Velora Resort</h3>
            <p>Morjim, North Goa<br>20 minutes from the airport transfer point.</p>
            <a class="btn dark" href="https://www.google.com/maps/search/?api=1&query=Morjim%2C%20Goa" target="_blank" rel="noopener">Open Maps</a>
          </div>
        </div>
      </div>
    </section>
  </main>

  <footer>
    <div class="container">
      <div class="footer-grid">
        <div>
          <div class="footer-logo">VELORA</div>
          <p>A quiet luxury resort & spa on the coast of Goa.</p>
        </div>
        <div>
          <h4>Explore</h4>
          <p><a href="#rooms">Rooms & Suites</a></p>
          <p><a href="#experience">Experiences</a></p>
          <p><a href="#gallery">Gallery</a></p>
        </div>
        <div>
          <h4>Reservations</h4>
          <p>+91 98765 43210</p>
          <p>stay@veloraresort.com</p>
        </div>
        <div>
          <h4>Follow</h4>
          <p><a href="#">Instagram</a></p>
          <p><a href="#">Pinterest</a></p>
          <p><a href="#">Facebook</a></p>
        </div>
      </div>
      <div class="copyright">
        <span>© 2026 VELORA Resort & Spa. Demo concept.</span>
        <span>Designed for presentation</span>
      </div>
    </div>
  </footer>

  <!-- Booking Modal -->
  <div class="modal" id="bookingModal" aria-hidden="true">
    <div class="modal-box">
      <button class="close" onclick="closeBooking()" aria-label="Close">×</button>
      <div class="eyebrow">Reservations</div>
      <h3>Plan your escape.</h3>
      <p>Send your preferred dates and our reservations team will get back to you.</p>
      <form class="form" onsubmit="submitBooking(event)">
        <input id="modalName" placeholder="Full name" required>
        <input id="modalEmail" type="email" placeholder="Email address" required>
        <input id="modalDate" type="date" required>
        <select id="modalRoom">
          <option>Ocean View Suite</option>
          <option>Private Pool Villa</option>
          <option>Presidential Suite</option>
        </select>
        <button class="btn dark" type="submit">Request Reservation</button>
      </form>
      <div class="success" id="success">Thank you. Your reservation request has been received for this demo.</div>
    </div>
  </div>

  <!-- Gallery Lightbox -->
  <div class="lightbox" id="lightbox">
    <button class="close" onclick="closeLightbox()" aria-label="Close">×</button>
    <img id="lightboxImg" src="" alt="">
  </div>

  <script>
    const nav = document.getElementById('nav');
    window.addEventListener('scroll', () => nav.classList.toggle('scrolled', window.scrollY > 30));

    const menu = document.getElementById('menu');
    menu.addEventListener('click', () => nav.classList.toggle('mobile-open'));
    document.querySelectorAll('.links a').forEach(a => a.addEventListener('click', () => nav.classList.remove('mobile-open')));

    const modal = document.getElementById('bookingModal');
    function openBooking(){
      modal.classList.add('open');
      modal.setAttribute('aria-hidden','false');
      document.body.style.overflow='hidden';
    }
    function closeBooking(){
      modal.classList.remove('open');
      modal.setAttribute('aria-hidden','true');
      document.body.style.overflow='';
    }
    modal.addEventListener('click', e => { if(e.target === modal) closeBooking(); });

    function quickBook(e){
      e.preventDefault();
      const checkin = document.getElementById('checkin').value;
      const checkout = document.getElementById('checkout').value;
      if(checkout <= checkin){ alert('Please choose a check-out date after check-in.'); return; }
      openBooking();
      document.getElementById('modalDate').value = checkin;
    }

    function submitBooking(e){
      e.preventDefault();
      document.getElementById('success').style.display='block';
      e.target.querySelector('button').textContent='Request Sent ✓';
      setTimeout(() => {
        closeBooking();
        document.getElementById('success').style.display='none';
        e.target.reset();
        e.target.querySelector('button').textContent='Request Reservation';
      }, 2200);
    }

    const lightbox = document.getElementById('lightbox');
    const lightboxImg = document.getElementById('lightboxImg');
    document.querySelectorAll('.gallery-item img').forEach(img => {
      img.addEventListener('click', () => {
        lightboxImg.src = img.src;
        lightboxImg.alt = img.alt;
        lightbox.classList.add('open');
        document.body.style.overflow='hidden';
      });
    });
    function closeLightbox(){
      lightbox.classList.remove('open');
      document.body.style.overflow='';
      lightboxImg.src='';
    }
    lightbox.addEventListener('click', e => { if(e.target === lightbox) closeLightbox(); });

    // Small deterrent for casual image saving. This is NOT a security mechanism.
    document.addEventListener('contextmenu', e => {
      if(e.target.tagName === 'IMG') e.preventDefault();
    });
    document.addEventListener('dragstart', e => {
      if(e.target.tagName === 'IMG') e.preventDefault();
    });

    // Set sensible default booking dates.
    const today = new Date();
    const tomorrow = new Date(today);
    tomorrow.setDate(today.getDate()+1);
    const in3 = new Date(today);
    in3.setDate(today.getDate()+3);
    const iso = d => d.toISOString().split('T')[0];
    document.getElementById('checkin').value = iso(tomorrow);
    document.getElementById('checkout').value = iso(in3);
    document.getElementById('modalDate').value = iso(tomorrow);
  </script>
</body>
</html>
