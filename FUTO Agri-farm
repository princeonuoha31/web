<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8"/>
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>FUTO Agri-Market</title>
  <link href="https://fonts.googleapis.com/css2?family=Playfair+Display:wght@700;800;900&family=DM+Sans:wght@300;400;500;600&family=Space+Mono:wght@400;700&family=Syne:wght@600;700;800&display=swap" rel="stylesheet"/>
  <style>
    :root {
      --green-deep:#1a3c2e; --green-mid:#2d6a4f; --green-fresh:#40916c;
      --green-light:#74c69d; --green-pale:#d8f3dc; --gold:#f4a12a;
      --earth-light:#c89b72; --cream:#faf7f0; --white:#ffffff;
      --text-dark:#1a2e1a; --text-mid:#3d5a3e; --text-light:#6b8f6b;
      --shadow:0 8px 32px rgba(26,60,46,0.15);
      --shadow-deep:0 20px 60px rgba(26,60,46,0.25);
      --radius:16px; --radius-sm:8px;
      --farm-bg:#0f1f17; --farm-surface:#162b1e; --farm-card:#1c3526;
      --farm-border:rgba(116,198,157,0.15); --farm-accent:#52c984;
      --farm-text:#e8f5ec; --farm-muted:rgba(232,245,236,0.5);
    }
    *,*::before,*::after{box-sizing:border-box;margin:0;padding:0;}
    html{scroll-behavior:smooth;}
    body{font-family:'DM Sans',sans-serif;background:var(--cream);color:var(--text-dark);overflow-x:hidden;}
    .page{display:none;min-height:100vh;}
    .page.active{display:block;animation:fadeIn .35s ease;}
    @keyframes fadeIn{from{opacity:0;transform:translateY(10px)}to{opacity:1;transform:translateY(0)}}

    /* NAVBAR */
    .navbar{position:sticky;top:0;z-index:1000;background:rgba(26,60,46,0.97);backdrop-filter:blur(12px);padding:0 2rem;display:flex;align-items:center;justify-content:space-between;height:68px;box-shadow:0 2px 20px rgba(0,0,0,0.3);}
    .nav-brand{display:flex;align-items:center;gap:10px;cursor:pointer;}
    .nav-logo{display:flex;align-items:center;gap:6px;padding:4px;}
    .nav-logo img{width:32px;height:32px;object-fit:contain;border-radius:8px;background:var(--gold);}
    .nav-brand-text{font-family:'Playfair Display',serif;font-size:1.25rem;color:var(--white);line-height:1.1;}
    .nav-brand-text span{display:block;font-size:0.65rem;font-family:'DM Sans',sans-serif;color:var(--green-light);font-weight:400;letter-spacing:2px;text-transform:uppercase;}
    .nav-links{display:flex;align-items:center;gap:0.3rem;}
    .nav-btn{background:none;border:none;color:var(--green-light);font-family:'DM Sans',sans-serif;font-size:0.875rem;font-weight:500;padding:0.5rem 1rem;border-radius:var(--radius-sm);cursor:pointer;transition:all .2s;}
    .nav-btn:hover{background:rgba(116,198,157,0.15);color:var(--white);}
    .nav-btn.active{color:var(--white);background:rgba(116,198,157,0.2);}
    .nav-cta{background:var(--gold);color:var(--green-deep)!important;font-weight:700;padding:0.5rem 1.2rem;border-radius:var(--radius-sm);}
    .nav-cta:hover{background:var(--earth-light)!important;color:var(--white)!important;}
    .nav-user-info{display:flex;align-items:center;gap:10px;color:var(--green-light);font-size:0.85rem;}
    .nav-user-avatar{width:32px;height:32px;border-radius:50%;background:var(--green-fresh);display:flex;align-items:center;justify-content:center;font-weight:700;color:var(--white);font-size:0.85rem;overflow:hidden;}
    .nav-user-avatar img{width:100%;height:100%;object-fit:cover;}
    .nav-signout{background:rgba(231,76,60,0.15);border:1px solid rgba(231,76,60,0.35);color:#e05c4a;font-family:'DM Sans',sans-serif;font-size:0.82rem;font-weight:600;padding:0.4rem 0.9rem;border-radius:8px;cursor:pointer;transition:all .2s;}
    .nav-signout:hover{background:rgba(231,76,60,0.3);}

    .back-bar{background:rgba(26,60,46,0.97);backdrop-filter:blur(12px);padding:0.75rem 2rem;box-shadow:0 2px 8px rgba(0,0,0,0.1);z-index:999;}
    .back-bar button{background:rgba(116,198,157,0.15);border:1px solid var(--green-light);color:var(--gold);font-family:'DM Sans',sans-serif;font-size:0.85rem;font-weight:600;padding:0.45rem 1rem;border-radius:8px;cursor:pointer;transition:all .2s;}
    .back-bar button:hover{background:rgba(116,198,157,0.3);color:var(--white);}

    .floating-cart{position:fixed;bottom:28px;right:28px;background:var(--gold);color:var(--green-deep);width:56px;height:56px;border-radius:50%;display:none;align-items:center;justify-content:center;cursor:pointer;box-shadow:0 4px 16px rgba(0,0,0,0.25);z-index:999;transition:transform .2s;}
    .floating-cart:hover{transform:scale(1.08);}
    .floating-cart.show{display:flex;}
    .floating-cart svg{width:24px;height:24px;stroke:var(--green-deep);fill:none;stroke-width:2;}
    .cart-badge{position:absolute;top:-6px;right:-6px;background:var(--green-deep);color:var(--gold);width:22px;height:22px;border-radius:50%;font-size:0.68rem;font-weight:700;display:flex;align-items:center;justify-content:center;border:2px solid white;}

    .btn{display:inline-flex;align-items:center;gap:8px;padding:0.85rem 1.8rem;border-radius:var(--radius);font-family:'DM Sans',sans-serif;font-size:0.95rem;font-weight:600;cursor:pointer;border:none;transition:all .25s;}
    .btn-primary{background:var(--gold);color:var(--green-deep);box-shadow:0 4px 20px rgba(244,161,42,0.35);}
    .btn-primary:hover{transform:translateY(-2px);box-shadow:0 8px 28px rgba(244,161,42,0.5);}
    .btn-outline{background:transparent;border:2px solid rgba(255,255,255,0.4);color:var(--white);}
    .btn-outline:hover{background:rgba(255,255,255,0.1);border-color:rgba(255,255,255,0.7);}
    .btn-green{background:var(--green-fresh);color:var(--white);box-shadow:0 4px 20px rgba(64,145,108,0.3);}
    .btn-green:hover{background:var(--green-mid);transform:translateY(-2px);}
    .btn-sm{padding:0.5rem 1rem;font-size:0.85rem;border-radius:var(--radius-sm);}

    /* HERO */
    .hero{min-height:92vh;background:linear-gradient(135deg,rgba(26,60,46,0.92),rgba(45,106,79,0.85),rgba(26,60,46,0.9)),url('data:image/svg+xml,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 800 600"><rect fill="%231a3c2e"/><circle cx="200" cy="150" r="120" fill="%232d6a4f" opacity="0.4"/><circle cx="600" cy="400" r="180" fill="%2340916c" opacity="0.3"/></svg>');background-size:cover;background-position:center;display:flex;align-items:center;padding:4rem 3rem;position:relative;overflow:hidden;}
    .hero::before{content:'';position:absolute;inset:0;background:radial-gradient(ellipse at 30% 50%,rgba(116,198,157,0.12),transparent 60%);}
    .hero-content{max-width:600px;position:relative;z-index:2;}
    .hero-badge{display:inline-flex;align-items:center;background:rgba(244,161,42,0.2);border:1px solid rgba(244,161,42,0.4);color:var(--gold);padding:0.4rem 1rem;border-radius:100px;font-size:0.78rem;font-weight:600;letter-spacing:1px;text-transform:uppercase;margin-bottom:1.5rem;}
    .hero h1{font-family:'Playfair Display',serif;font-size:clamp(2.5rem,5vw,4rem);color:var(--white);line-height:1.1;margin-bottom:1.2rem;}
    .hero h1 .accent{color:var(--gold);}
    .hero p{font-size:1.1rem;color:rgba(255,255,255,0.8);line-height:1.7;margin-bottom:2rem;}
    .hero-actions{display:flex;gap:1rem;flex-wrap:wrap;}
    .hero-stats{display:flex;gap:2rem;margin-top:3rem;}
    .hero-stat .num{font-family:'Playfair Display',serif;font-size:1.8rem;color:var(--gold);font-weight:900;}
    .hero-stat .lbl{font-size:0.75rem;color:rgba(255,255,255,0.6);text-transform:uppercase;letter-spacing:1px;}

    .section{padding:5rem 3rem;}
    .section-label{font-size:0.75rem;font-weight:700;text-transform:uppercase;letter-spacing:3px;color:var(--green-fresh);margin-bottom:0.75rem;}
    .section-title{font-family:'Playfair Display',serif;font-size:clamp(1.8rem,3.5vw,2.8rem);color:var(--green-deep);line-height:1.2;}
    .section-sub{color:var(--text-light);margin-top:0.75rem;font-size:1rem;}
    .section-header{text-align:center;margin-bottom:3.5rem;}
    .steps-grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(220px,1fr));gap:2rem;}
    .step-card{background:var(--white);border-radius:var(--radius);padding:2rem 1.5rem;box-shadow:var(--shadow);position:relative;overflow:hidden;transition:transform .3s;}
    .step-card:hover{transform:translateY(-6px);}
    .step-card::before{content:'';position:absolute;top:0;left:0;right:0;height:4px;background:linear-gradient(90deg,var(--green-fresh),var(--gold));}
    .step-num{font-family:'Space Mono',monospace;font-size:3rem;font-weight:700;color:var(--green-pale);line-height:1;margin-bottom:0.5rem;}
    .step-title{font-size:1.05rem;font-weight:700;color:var(--green-deep);margin-bottom:0.5rem;}
    .step-desc{font-size:0.9rem;color:var(--text-light);line-height:1.6;}

    /* PRODUCT CARDS */
    .products-section{background:var(--white);}
    .filter-bar{display:flex;gap:0.75rem;flex-wrap:wrap;justify-content:center;margin-bottom:2.5rem;}
    .filter-btn{padding:0.5rem 1.2rem;border-radius:100px;border:2px solid var(--green-pale);background:transparent;color:var(--text-mid);font-family:'DM Sans',sans-serif;font-size:0.85rem;font-weight:600;cursor:pointer;transition:all .2s;}
    .filter-btn:hover,.filter-btn.active{background:var(--green-fresh);border-color:var(--green-fresh);color:white;}
    .products-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(260px,1fr));gap:1.5rem;}
    .product-card{background:var(--cream);border-radius:var(--radius);overflow:hidden;box-shadow:var(--shadow);transition:all .3s;border:1px solid rgba(116,198,157,0.15);}
    .product-card:hover{transform:translateY(-6px);box-shadow:var(--shadow-deep);}
    .product-img{height:200px;overflow:hidden;background:var(--green-pale);display:flex;align-items:center;justify-content:center;position:relative;}
    .product-img img{width:100%;height:100%;object-fit:cover;display:block;}
    .product-img .no-img-text{font-size:0.85rem;color:var(--text-light);}
    .product-badge{position:absolute;top:12px;left:12px;background:var(--gold);color:var(--green-deep);padding:0.25rem 0.7rem;border-radius:100px;font-size:0.7rem;font-weight:700;text-transform:uppercase;letter-spacing:1px;}
    .product-badge.fresh{background:var(--green-fresh);color:white;}
    .product-body{padding:1.25rem;}
    .product-farmer{display:flex;align-items:center;gap:6px;font-size:0.78rem;color:var(--text-light);margin-bottom:0.6rem;}
    .farmer-dot{width:6px;height:6px;border-radius:50%;background:var(--green-light);}
    .product-name{font-size:1.05rem;font-weight:700;color:var(--green-deep);margin-bottom:0.4rem;}
    .product-meta{display:flex;align-items:center;justify-content:space-between;margin-bottom:0.8rem;}
    .product-price{font-family:'Space Mono',monospace;font-size:1.1rem;font-weight:700;color:var(--green-fresh);}
    .product-unit{font-size:0.75rem;color:var(--text-light);}
    .product-stars{color:var(--gold);font-size:0.85rem;}

    /* AUTH */
    .auth-wrap{min-height:100vh;display:flex;align-items:center;justify-content:center;background:linear-gradient(135deg,var(--green-deep),var(--green-mid));padding:2rem;position:relative;}
    .auth-wrap::before{content:'';position:absolute;inset:0;background:url("data:image/svg+xml,%3Csvg width='60' height='60' viewBox='0 0 60 60' xmlns='http://www.w3.org/2000/svg'%3E%3Cg fill='%2374c69d' fill-opacity='0.05'%3E%3Ccircle cx='30' cy='30' r='2'/%3E%3C/g%3E%3C/svg%3E");}
    .auth-box{width:100%;max-width:460px;position:relative;z-index:1;}
    .auth-brand{text-align:center;margin-bottom:1.5rem;}
    .auth-logo-mark{width:60px;height:60px;border-radius:18px;background:var(--gold);display:flex;align-items:center;justify-content:center;margin:0 auto 0.75rem;overflow:hidden;}
    .auth-logo-mark img{width:100%;height:100%;object-fit:contain;}
    .auth-brand h2{font-family:'Playfair Display',serif;color:var(--white);font-size:1.5rem;}
    .auth-brand p{color:rgba(255,255,255,0.6);font-size:0.85rem;margin-top:0.2rem;}
    .auth-card{background:var(--white);border-radius:var(--radius);padding:2rem;box-shadow:var(--shadow-deep);}
    .role-toggle{display:flex;background:var(--green-pale);border-radius:var(--radius-sm);padding:4px;margin-bottom:1.5rem;}
    .role-btn{flex:1;padding:0.6rem;background:transparent;border:none;border-radius:calc(var(--radius-sm) - 2px);font-family:'DM Sans',sans-serif;font-size:0.9rem;font-weight:600;color:var(--text-mid);cursor:pointer;transition:all .2s;}
    .role-btn.active{background:var(--green-fresh);color:var(--white);box-shadow:0 2px 8px rgba(64,145,108,0.3);}
    .form-group{margin-bottom:1.1rem;}
    .form-label{display:block;font-size:0.78rem;font-weight:600;color:var(--text-mid);margin-bottom:0.4rem;text-transform:uppercase;letter-spacing:0.5px;}
    .form-input{width:100%;padding:0.8rem 1rem;border:2px solid var(--green-pale);border-radius:var(--radius-sm);font-family:'DM Sans',sans-serif;font-size:0.95rem;color:var(--text-dark);background:var(--cream);transition:border-color .2s;outline:none;}
    .form-input:focus{border-color:var(--green-fresh);background:white;}
    .form-input::placeholder{color:#bbb;}
    .form-row{display:grid;grid-template-columns:1fr 1fr;gap:0.75rem;}
    .auth-footer{text-align:center;margin-top:1.25rem;font-size:0.85rem;color:var(--text-light);}
    .auth-link{color:var(--green-fresh);text-decoration:none;font-weight:600;cursor:pointer;}
    .auth-divider{display:flex;align-items:center;gap:1rem;color:var(--text-light);font-size:0.8rem;margin:1rem 0;}
    .auth-divider::before,.auth-divider::after{content:'';flex:1;height:1px;background:var(--green-pale);}

    /* MARKETPLACE */
    .mkt-header{background:linear-gradient(135deg,var(--green-deep),var(--green-mid));padding:3rem;color:white;}
    .mkt-header h2{font-family:'Playfair Display',serif;font-size:2rem;margin-bottom:0.5rem;}
    .mkt-header p{color:rgba(255,255,255,0.7);}
    .search-bar{display:flex;gap:0.75rem;margin-top:1.5rem;}
    .search-input{flex:1;padding:0.85rem 1.2rem;border-radius:var(--radius);border:none;font-family:'DM Sans',sans-serif;font-size:0.95rem;background:rgba(255,255,255,0.15);color:white;outline:none;}
    .search-input::placeholder{color:rgba(255,255,255,0.5);}
    .search-input:focus{background:rgba(255,255,255,0.22);}
    .mkt-body{padding:2rem 3rem;}

    /* CART */
    .cart-page{padding:2.5rem 3rem;}
    .cart-page h2{font-family:'Playfair Display',serif;font-size:2rem;color:var(--green-deep);margin-bottom:2rem;}
    .cart-layout{display:grid;grid-template-columns:1fr 350px;gap:2rem;}
    .cart-items{display:flex;flex-direction:column;gap:1rem;}
    .cart-item{background:var(--white);border-radius:var(--radius);padding:1.25rem;display:flex;align-items:center;gap:1.25rem;box-shadow:var(--shadow);}
    .cart-item-img{width:70px;height:70px;border-radius:var(--radius-sm);background:var(--green-pale);flex-shrink:0;overflow:hidden;}
    .cart-item-img img{width:100%;height:100%;object-fit:cover;}
    .cart-item-info{flex:1;}
    .cart-item-name{font-weight:700;font-size:1rem;color:var(--green-deep);}
    .cart-item-farmer{font-size:0.8rem;color:var(--text-light);margin-top:0.2rem;}
    .cart-item-price{font-family:'Space Mono',monospace;color:var(--green-fresh);font-weight:700;margin-top:0.3rem;}
    .qty-ctrl{display:flex;align-items:center;gap:0.75rem;}
    .qty-btn{width:30px;height:30px;border-radius:50%;border:2px solid var(--green-light);background:none;font-size:1.1rem;color:var(--green-fresh);cursor:pointer;display:flex;align-items:center;justify-content:center;font-weight:700;transition:all .2s;}
    .qty-btn:hover{background:var(--green-fresh);color:white;border-color:var(--green-fresh);}
    .qty-num{font-weight:700;font-size:1rem;min-width:20px;text-align:center;}
    .cart-summary{background:var(--white);border-radius:var(--radius);padding:1.75rem;box-shadow:var(--shadow);height:fit-content;position:sticky;top:88px;}
    .cart-summary h3{font-family:'Playfair Display',serif;font-size:1.2rem;color:var(--green-deep);margin-bottom:1.25rem;}
    .summary-row{display:flex;justify-content:space-between;padding:0.5rem 0;font-size:0.9rem;}
    .summary-total{border-top:2px solid var(--green-pale);margin-top:0.5rem;padding-top:1rem;font-weight:700;font-size:1.1rem;color:var(--green-deep);display:flex;justify-content:space-between;}
    .total-price{font-family:'Space Mono',monospace;color:var(--green-fresh);}

    /* PAYMENT */
    .pay-page{padding:2.5rem 3rem;}
    .pay-page h2{font-family:'Playfair Display',serif;font-size:2rem;color:var(--green-deep);margin-bottom:2rem;}
    .pay-layout{display:grid;grid-template-columns:1fr 380px;gap:2rem;}
    .pay-card{background:var(--white);border-radius:var(--radius);padding:2rem;box-shadow:var(--shadow);margin-bottom:1.5rem;}
    .pay-card h3{font-family:'Playfair Display',serif;font-size:1.1rem;color:var(--green-deep);margin-bottom:1.25rem;}
    .pay-methods{display:flex;gap:0.75rem;margin-bottom:1.5rem;flex-wrap:wrap;}
    .pay-method{flex:1;min-width:90px;padding:0.8rem 1rem;border:2px solid var(--green-pale);border-radius:var(--radius-sm);cursor:pointer;text-align:center;font-size:0.85rem;font-weight:600;color:var(--text-mid);transition:all .2s;font-family:'DM Sans',sans-serif;}
    .pay-method:hover,.pay-method.active{border-color:var(--green-fresh);background:var(--green-pale);color:var(--green-deep);}
    .card-visual{background:linear-gradient(135deg,var(--green-deep),var(--green-fresh));border-radius:var(--radius);padding:1.5rem;margin-bottom:1.5rem;color:white;position:relative;overflow:hidden;}
    .card-visual::before{content:'';position:absolute;right:-30px;top:-30px;width:160px;height:160px;border-radius:50%;background:rgba(255,255,255,0.07);}
    .card-chip{font-family:'Space Mono',monospace;font-size:0.75rem;letter-spacing:2px;margin-bottom:1rem;opacity:0.7;}
    .card-number{font-family:'Space Mono',monospace;letter-spacing:4px;font-size:1rem;margin-bottom:0.75rem;opacity:0.9;}
    .card-info{display:flex;justify-content:space-between;font-size:0.8rem;opacity:0.7;}
    .prog-steps{display:flex;align-items:center;margin-bottom:2rem;}
    .prog-step{display:flex;flex-direction:column;align-items:center;flex:1;}
    .prog-dot{width:32px;height:32px;border-radius:50%;border:2px solid var(--green-pale);background:var(--cream);display:flex;align-items:center;justify-content:center;font-size:0.75rem;font-weight:700;color:var(--text-light);position:relative;z-index:1;transition:all .3s;}
    .prog-dot.done{background:var(--green-fresh);border-color:var(--green-fresh);color:white;}
    .prog-dot.cur{background:var(--gold);border-color:var(--gold);color:var(--green-deep);}
    .prog-lbl{font-size:0.7rem;color:var(--text-light);margin-top:0.3rem;text-align:center;}
    .prog-line{flex:1;height:2px;background:var(--green-pale);position:relative;top:-10px;}
    .prog-line.done{background:var(--green-fresh);}
    .order-box{background:var(--white);border-radius:var(--radius);padding:1.5rem;box-shadow:var(--shadow);height:fit-content;position:sticky;top:88px;}
    .order-box h3{font-family:'Playfair Display',serif;font-size:1.1rem;color:var(--green-deep);margin-bottom:1rem;padding-bottom:0.75rem;border-bottom:2px solid var(--green-pale);}
    .order-item{display:flex;justify-content:space-between;align-items:center;padding:0.6rem 0;border-bottom:1px solid var(--green-pale);font-size:0.9rem;}
    .order-item:last-child{border-bottom:none;}

    /* SUCCESS */
    .success-page{min-height:100vh;display:flex;align-items:center;justify-content:center;background:linear-gradient(135deg,var(--green-deep),var(--green-mid));padding:2rem;}
    .success-card{background:white;border-radius:var(--radius);padding:3rem;text-align:center;max-width:480px;box-shadow:var(--shadow-deep);}
    .success-icon{width:72px;height:72px;background:var(--green-pale);border-radius:50%;display:flex;align-items:center;justify-content:center;font-size:2rem;color:var(--green-fresh);font-weight:900;margin:0 auto 1.5rem;animation:pop .5s cubic-bezier(0.175,0.885,0.32,1.275);}
    @keyframes pop{from{transform:scale(0)}to{transform:scale(1)}}
    .success-card h2{font-family:'Playfair Display',serif;color:var(--green-deep);font-size:1.8rem;margin-bottom:0.75rem;}
    .success-card p{color:var(--text-light);line-height:1.6;margin-bottom:0.5rem;}
    .order-id-tag{font-family:'Space Mono',monospace;background:var(--green-pale);padding:0.5rem 1rem;border-radius:var(--radius-sm);color:var(--green-deep);font-size:0.9rem;display:inline-block;margin:1rem 0;}

    /* TOAST */
    .toast{position:fixed;bottom:2rem;right:2rem;background:var(--green-deep);color:white;padding:0.9rem 1.5rem;border-radius:var(--radius);font-size:0.9rem;box-shadow:var(--shadow-deep);z-index:9999;display:none;animation:slideIn .3s ease;}
    .toast.show{display:flex;align-items:center;gap:8px;}
    @keyframes slideIn{from{opacity:0;transform:translateX(20px)}to{opacity:1;transform:translateX(0)}}

    /* FARMER DASHBOARD */
    #page-farmer-dashboard{background:var(--farm-bg);min-height:100vh;display:none;flex-direction:column;}
    #page-farmer-dashboard.active{display:flex;}
    .farm-navbar{position:sticky;top:0;z-index:1000;background:var(--farm-surface);border-bottom:1px solid var(--farm-border);display:flex;align-items:center;padding:0 1.5rem;height:64px;gap:0.5rem;}
    .farm-brand{display:flex;align-items:center;gap:8px;cursor:pointer;margin-right:1rem;}
    .farm-brand img{width:28px;height:28px;object-fit:contain;border-radius:6px;background:var(--gold);}
    .farm-brand-text{font-family:'Syne',sans-serif;font-size:1.05rem;font-weight:700;color:var(--farm-text);}
    .farm-nav-links{display:flex;align-items:center;gap:0.25rem;}
    .farm-nav-btn{padding:0.45rem 0.9rem;border-radius:8px;border:none;background:transparent;color:var(--farm-muted);font-family:'DM Sans',sans-serif;font-size:0.85rem;font-weight:500;cursor:pointer;transition:all .2s;}
    .farm-nav-btn:hover{background:rgba(82,201,132,0.1);color:var(--farm-text);}
    .farm-nav-btn.active{background:rgba(82,201,132,0.15);color:var(--farm-accent);font-weight:600;}
    .farm-nav-right{display:flex;align-items:center;gap:0.75rem;margin-left:auto;}
    .farm-user-pill{display:flex;align-items:center;gap:8px;background:rgba(82,201,132,0.1);border:1px solid var(--farm-border);border-radius:100px;padding:0.3rem 0.75rem 0.3rem 0.3rem;}
    .farm-user-av{width:28px;height:28px;border-radius:50%;background:linear-gradient(135deg,var(--farm-accent),#28a06b);display:flex;align-items:center;justify-content:center;font-weight:700;color:white;font-size:0.78rem;overflow:hidden;}
    .farm-user-av img{width:100%;height:100%;object-fit:cover;}
    .farm-user-name{font-size:0.82rem;color:var(--farm-text);font-weight:600;}
    .farm-signout{background:rgba(231,76,60,0.12);border:1px solid rgba(231,76,60,0.3);color:#e05c4a;font-family:'DM Sans',sans-serif;font-size:0.8rem;font-weight:600;padding:0.35rem 0.8rem;border-radius:8px;cursor:pointer;transition:all .2s;}
    .farm-signout:hover{background:rgba(231,76,60,0.25);}
    .farm-layout{display:flex;flex:1;}
    .farm-sidebar{width:210px;flex-shrink:0;background:var(--farm-surface);border-right:1px solid var(--farm-border);padding:1.25rem 0.75rem;display:flex;flex-direction:column;}
    .farm-sb-label{font-size:0.68rem;font-weight:700;letter-spacing:2px;text-transform:uppercase;color:var(--farm-muted);padding:0.5rem 0.75rem;margin-top:0.75rem;}
    .farm-sb-btn{display:flex;align-items:center;padding:0.6rem 0.85rem;border-radius:10px;border:none;background:transparent;color:var(--farm-muted);font-family:'DM Sans',sans-serif;font-size:0.85rem;font-weight:500;cursor:pointer;transition:all .2s;text-align:left;width:100%;margin-bottom:2px;}
    .farm-sb-btn:hover{background:rgba(82,201,132,0.08);color:var(--farm-text);}
    .farm-sb-btn.active{background:rgba(82,201,132,0.15);color:var(--farm-accent);font-weight:600;}
    .farm-sb-signout{color:rgba(231,76,60,0.7)!important;margin-top:auto;}
    .farm-sb-signout:hover{background:rgba(231,76,60,0.1)!important;color:#e05c4a!important;}
    .farm-main{flex:1;overflow-y:auto;padding:2rem;}
    .farm-section{display:none;}
    .farm-section.active{display:block;animation:fadeIn .3s ease;}
    .farm-page-title{font-family:'Syne',sans-serif;font-size:1.5rem;font-weight:800;color:var(--farm-text);margin-bottom:0.25rem;}
    .farm-page-sub{color:var(--farm-muted);font-size:0.9rem;margin-bottom:2rem;}
    .farm-stats-row{display:grid;grid-template-columns:repeat(4,1fr);gap:1rem;margin-bottom:2rem;}
    .farm-stat-card{background:var(--farm-card);border:1px solid var(--farm-border);border-radius:14px;padding:1.25rem 1.5rem;transition:transform .2s;}
    .farm-stat-card:hover{transform:translateY(-2px);}
    .farm-stat-val{font-family:'Syne',sans-serif;font-size:1.75rem;font-weight:800;color:var(--farm-text);line-height:1;margin-bottom:0.25rem;}
    .farm-stat-lbl{font-size:0.75rem;color:var(--farm-muted);text-transform:uppercase;letter-spacing:1px;margin-bottom:0.25rem;}
    .farm-stat-ch{font-size:0.75rem;color:var(--farm-accent);}
    .farm-grid2{display:grid;grid-template-columns:1fr 1fr;gap:1.5rem;margin-top:1.5rem;}
    .farm-card{background:var(--farm-card);border:1px solid var(--farm-border);border-radius:14px;padding:1.5rem;}
    .farm-card-title{font-family:'Syne',sans-serif;font-size:0.95rem;font-weight:700;color:var(--farm-text);margin-bottom:1rem;display:flex;align-items:center;justify-content:space-between;}
    .farm-card-title a{font-size:0.75rem;color:var(--farm-accent);font-weight:500;cursor:pointer;font-family:'DM Sans',sans-serif;}
    .farm-actions-grid{display:grid;grid-template-columns:1fr 1fr;gap:0.75rem;}
    .farm-action-tile{background:rgba(82,201,132,0.06);border:1px solid var(--farm-border);border-radius:12px;padding:1rem;cursor:pointer;transition:all .2s;}
    .farm-action-tile:hover{background:rgba(82,201,132,0.14);border-color:rgba(82,201,132,0.4);}
    .farm-action-lbl{font-size:0.85rem;font-weight:600;color:var(--farm-text);}
    .farm-action-sub{font-size:0.75rem;color:var(--farm-muted);margin-top:2px;}
    .farm-sale-item{display:flex;align-items:center;gap:0.75rem;padding:0.65rem 0;border-bottom:1px solid var(--farm-border);}
    .farm-sale-item:last-child{border-bottom:none;}
    .farm-sale-img{width:38px;height:38px;border-radius:8px;overflow:hidden;flex-shrink:0;background:var(--farm-surface);}
    .farm-sale-img img{width:100%;height:100%;object-fit:cover;}
    .farm-sale-info{flex:1;}
    .farm-sale-name{font-size:0.85rem;font-weight:600;color:var(--farm-text);}
    .farm-sale-meta{font-size:0.75rem;color:var(--farm-muted);}
    .farm-sale-amount{font-family:'Space Mono',monospace;font-size:0.85rem;font-weight:700;color:var(--farm-accent);}
    .farm-listings-hdr{display:flex;align-items:center;justify-content:space-between;margin-bottom:1.5rem;flex-wrap:wrap;gap:1rem;}
    .farm-search-input{background:var(--farm-card);border:1px solid var(--farm-border);border-radius:10px;padding:0.6rem 1rem;color:var(--farm-text);font-family:'DM Sans',sans-serif;font-size:0.85rem;outline:none;width:220px;transition:border-color .2s;}
    .farm-search-input:focus{border-color:var(--farm-accent);}
    .farm-search-input::placeholder{color:var(--farm-muted);}
    .farm-add-btn{display:flex;align-items:center;gap:6px;padding:0.6rem 1.25rem;border-radius:10px;border:none;background:linear-gradient(135deg,var(--farm-accent),#28a06b);color:white;font-family:'DM Sans',sans-serif;font-size:0.875rem;font-weight:600;cursor:pointer;transition:all .2s;box-shadow:0 4px 14px rgba(82,201,132,0.3);}
    .farm-add-btn:hover{transform:translateY(-1px);box-shadow:0 6px 20px rgba(82,201,132,0.45);}
    .farm-listings-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(230px,1fr));gap:1.25rem;}
    .farm-listing-card{background:var(--farm-card);border:1px solid var(--farm-border);border-radius:16px;overflow:hidden;transition:all .25s;}
    .farm-listing-card:hover{border-color:rgba(82,201,132,0.4);transform:translateY(-3px);box-shadow:0 12px 32px rgba(0,0,0,0.3);}
    .farm-listing-img{height:150px;overflow:hidden;background:#0d1a12;display:flex;align-items:center;justify-content:center;position:relative;}
    .farm-listing-img img{width:100%;height:100%;object-fit:cover;}
    .farm-listing-img .no-img{font-size:0.82rem;color:rgba(232,245,236,0.3);}
    .farm-listing-status{position:absolute;top:8px;right:8px;padding:0.2rem 0.6rem;border-radius:100px;font-size:0.68rem;font-weight:700;background:rgba(82,201,132,0.2);color:#52c984;border:1px solid rgba(82,201,132,0.4);}
    .farm-listing-body{padding:1rem;}
    .farm-listing-name{font-family:'Syne',sans-serif;font-size:0.95rem;font-weight:700;color:var(--farm-text);margin-bottom:0.3rem;}
    .farm-listing-meta{font-size:0.75rem;color:var(--farm-muted);margin-bottom:0.5rem;}
    .farm-listing-price{font-family:'Space Mono',monospace;font-size:1.05rem;font-weight:700;color:var(--farm-accent);}
    .farm-listing-actions{display:flex;gap:0.5rem;margin-top:0.75rem;padding-top:0.75rem;border-top:1px solid var(--farm-border);}
    .farm-btn{flex:1;padding:0.45rem;border-radius:8px;border:none;font-family:'DM Sans',sans-serif;font-size:0.8rem;font-weight:600;cursor:pointer;transition:all .2s;}
    .farm-btn-edit{background:rgba(244,161,42,0.14);color:#f4a12a;border:1px solid rgba(244,161,42,0.3);}
    .farm-btn-edit:hover{background:rgba(244,161,42,0.28);}
    .farm-btn-del{background:rgba(231,76,60,0.1);color:#e05c4a;border:1px solid rgba(231,76,60,0.3);}
    .farm-btn-del:hover{background:rgba(231,76,60,0.25);}

    /* PROFILE SECTION (farmer dashboard) */
    .farm-profile-banner{background:rgba(82,201,132,0.08);border:1px solid var(--farm-border);border-radius:18px;padding:2rem;display:flex;align-items:center;gap:1.5rem;margin-bottom:2rem;}
    .farm-profile-av{width:76px;height:76px;border-radius:50%;background:linear-gradient(135deg,var(--farm-accent),#28a06b);display:flex;align-items:center;justify-content:center;font-size:2rem;font-weight:900;color:white;flex-shrink:0;font-family:'Syne',sans-serif;overflow:hidden;position:relative;}
    .farm-profile-av img{width:100%;height:100%;object-fit:cover;position:absolute;inset:0;}
    .farm-profile-info h2{font-family:'Syne',sans-serif;font-size:1.3rem;color:var(--farm-text);}
    .farm-profile-info p{color:var(--farm-muted);font-size:0.85rem;margin-top:0.2rem;}
    .farm-profile-badge{display:inline-flex;align-items:center;gap:4px;background:rgba(82,201,132,0.14);border:1px solid rgba(82,201,132,0.35);color:var(--farm-accent);padding:0.2rem 0.6rem;border-radius:100px;font-size:0.72rem;font-weight:600;margin-top:0.5rem;}
    .farm-info-grid{display:grid;grid-template-columns:1fr 1fr;gap:1rem;}
    .farm-info-card{background:var(--farm-card);border:1px solid var(--farm-border);border-radius:14px;padding:1.25rem;}
    .farm-info-card h4{font-family:'Syne',sans-serif;font-size:0.875rem;color:var(--farm-accent);margin-bottom:0.75rem;}
    .farm-info-row{display:flex;justify-content:space-between;align-items:center;padding:0.4rem 0;border-bottom:1px solid var(--farm-border);font-size:0.85rem;}
    .farm-info-row:last-child{border-bottom:none;}
    .farm-info-label{color:var(--farm-muted);}
    .farm-info-value{color:var(--farm-text);font-weight:600;}
    .farm-form-group{margin-bottom:1rem;}
    .farm-form-label{display:block;font-size:0.75rem;font-weight:600;color:var(--farm-muted);margin-bottom:0.35rem;text-transform:uppercase;letter-spacing:0.8px;}
    .farm-form-input{width:100%;padding:0.7rem 1rem;background:var(--farm-surface);border:1px solid var(--farm-border);border-radius:10px;color:var(--farm-text);font-family:'DM Sans',sans-serif;font-size:0.9rem;outline:none;transition:border-color .2s;}
    .farm-form-input:focus{border-color:var(--farm-accent);}
    .farm-form-input::placeholder{color:rgba(232,245,236,0.25);}
    .farm-form-row{display:grid;grid-template-columns:1fr 1fr;gap:0.75rem;}
    textarea.farm-form-input{resize:vertical;min-height:80px;}

    /* PROFILE PHOTO UPLOAD (dashboard) */
    .profile-photo-wrap{position:relative;width:90px;height:90px;flex-shrink:0;}
    .profile-photo-circle{width:90px;height:90px;border-radius:50%;background:linear-gradient(135deg,var(--farm-accent),#28a06b);display:flex;align-items:center;justify-content:center;font-size:2.2rem;font-weight:900;color:white;font-family:'Syne',sans-serif;overflow:hidden;border:3px solid rgba(82,201,132,0.4);}
    .profile-photo-circle img{width:100%;height:100%;object-fit:cover;}
    .profile-photo-upload-btn{position:absolute;bottom:0;right:0;width:28px;height:28px;border-radius:50%;background:var(--farm-accent);border:2px solid var(--farm-bg);display:flex;align-items:center;justify-content:center;cursor:pointer;transition:all .2s;}
    .profile-photo-upload-btn:hover{background:#28a06b;transform:scale(1.1);}
    .profile-photo-upload-btn svg{width:14px;height:14px;fill:white;}
    .profile-photo-input{display:none;}

    /* MODAL */
    .modal-overlay{display:none;position:fixed;inset:0;z-index:2000;background:rgba(0,0,0,0.72);backdrop-filter:blur(4px);align-items:center;justify-content:center;padding:2rem;}
    .modal-overlay.open{display:flex;animation:fadeIn .2s ease;}
    .modal{background:var(--farm-card);border:1px solid var(--farm-border);border-radius:20px;width:100%;max-width:540px;max-height:90vh;overflow-y:auto;box-shadow:0 30px 80px rgba(0,0,0,0.5);}
    .modal-header{padding:1.5rem 1.75rem 1rem;border-bottom:1px solid var(--farm-border);display:flex;align-items:center;justify-content:space-between;}
    .modal-header h3{font-family:'Syne',sans-serif;font-size:1.15rem;font-weight:700;color:var(--farm-text);}
    .modal-close{background:rgba(255,255,255,0.07);border:none;color:var(--farm-muted);width:30px;height:30px;border-radius:50%;cursor:pointer;font-size:1rem;display:flex;align-items:center;justify-content:center;transition:all .2s;}
    .modal-close:hover{background:rgba(231,76,60,0.2);color:#e05c4a;}
    .modal-body{padding:1.5rem 1.75rem;}
    .modal-footer{padding:1rem 1.75rem 1.5rem;display:flex;gap:0.75rem;justify-content:flex-end;}
    .modal-cancel{padding:0.6rem 1.25rem;border-radius:10px;border:1px solid var(--farm-border);background:transparent;color:var(--farm-muted);font-family:'DM Sans',sans-serif;font-size:0.875rem;font-weight:600;cursor:pointer;transition:all .2s;}
    .modal-cancel:hover{background:rgba(255,255,255,0.05);color:var(--farm-text);}
    .modal-submit{padding:0.6rem 1.5rem;border-radius:10px;border:none;background:linear-gradient(135deg,var(--farm-accent),#28a06b);color:white;font-family:'DM Sans',sans-serif;font-size:0.875rem;font-weight:600;cursor:pointer;transition:all .2s;box-shadow:0 4px 14px rgba(82,201,132,0.3);}
    .modal-submit:hover{transform:translateY(-1px);}
    .modal-del-confirm{padding:0.6rem 1.5rem;border-radius:10px;border:1px solid rgba(231,76,60,0.4);background:rgba(231,76,60,0.14);color:#e05c4a;font-family:'DM Sans',sans-serif;font-size:0.875rem;font-weight:700;cursor:pointer;transition:all .2s;}
    .modal-del-confirm:hover{background:rgba(231,76,60,0.28);}
    .upload-zone{border:2px dashed rgba(82,201,132,0.35);border-radius:12px;padding:1.5rem;text-align:center;cursor:pointer;transition:all .2s;background:rgba(82,201,132,0.04);}
    .upload-zone:hover{border-color:var(--farm-accent);background:rgba(82,201,132,0.09);}
    .upload-zone input[type="file"]{display:none;}
    .upload-preview{width:100%;height:150px;object-fit:cover;border-radius:8px;display:none;}
    .upload-plus{font-size:1.5rem;font-weight:300;color:var(--farm-accent);margin-bottom:0.4rem;}
    .upload-hint{font-size:0.82rem;color:var(--farm-muted);}
    .upload-hint strong{color:var(--farm-accent);}

    /* ======================== */
    /* FARMER PROFILE MODAL (student side) */
    /* ======================== */
    .fp-modal-overlay{display:none;position:fixed;inset:0;z-index:3000;background:rgba(0,0,0,0.65);backdrop-filter:blur(8px);align-items:center;justify-content:center;padding:1.5rem;}
    .fp-modal-overlay.open{display:flex;animation:fadeIn .25s ease;}
    .fp-modal{background:var(--white);border-radius:24px;width:100%;max-width:560px;max-height:90vh;overflow-y:auto;box-shadow:0 40px 100px rgba(0,0,0,0.35);position:relative;}
    .fp-modal-hero{height:160px;background:linear-gradient(135deg,var(--green-deep),var(--green-mid));position:relative;border-radius:24px 24px 0 0;overflow:hidden;}
    .fp-modal-hero::after{content:'';position:absolute;inset:0;background:url("data:image/svg+xml,%3Csvg width='40' height='40' viewBox='0 0 40 40' xmlns='http://www.w3.org/2000/svg'%3E%3Cg fill='%2374c69d' fill-opacity='0.08'%3E%3Ccircle cx='20' cy='20' r='2'/%3E%3C/g%3E%3C/svg%3E");}
    .fp-modal-close{position:absolute;top:14px;right:14px;width:32px;height:32px;border-radius:50%;background:rgba(255,255,255,0.15);border:none;color:white;cursor:pointer;font-size:1.1rem;display:flex;align-items:center;justify-content:center;z-index:2;transition:all .2s;}
    .fp-modal-close:hover{background:rgba(255,255,255,0.28);}
    .fp-modal-avatar-wrap{position:absolute;bottom:-40px;left:2rem;z-index:2;}
    .fp-modal-avatar{width:80px;height:80px;border-radius:50%;border:4px solid var(--white);background:linear-gradient(135deg,var(--green-fresh),var(--green-mid));display:flex;align-items:center;justify-content:center;font-family:'Playfair Display',serif;font-size:2rem;font-weight:900;color:white;overflow:hidden;box-shadow:0 8px 24px rgba(0,0,0,0.2);}
    .fp-modal-avatar img{width:100%;height:100%;object-fit:cover;}
    .fp-verified-badge{position:absolute;bottom:0;right:0;width:24px;height:24px;background:var(--gold);border-radius:50%;border:2px solid white;display:flex;align-items:center;justify-content:center;font-size:0.7rem;}
    .fp-modal-body{padding:3.5rem 2rem 2rem;}
    .fp-name{font-family:'Playfair Display',serif;font-size:1.6rem;color:var(--green-deep);margin-bottom:0.25rem;font-weight:900;}
    .fp-title{font-size:0.85rem;color:var(--text-light);margin-bottom:1rem;}
    .fp-stats-row{display:grid;grid-template-columns:repeat(3,1fr);gap:0.75rem;margin-bottom:1.5rem;}
    .fp-stat{background:var(--green-pale);border-radius:12px;padding:0.85rem 0.75rem;text-align:center;}
    .fp-stat-val{font-family:'Space Mono',monospace;font-size:1.1rem;font-weight:700;color:var(--green-deep);}
    .fp-stat-lbl{font-size:0.68rem;color:var(--text-light);text-transform:uppercase;letter-spacing:0.8px;margin-top:2px;}
    .fp-info-section{margin-bottom:1.25rem;}
    .fp-info-label{font-size:0.7rem;font-weight:700;text-transform:uppercase;letter-spacing:1.5px;color:var(--green-fresh);margin-bottom:0.5rem;}
    .fp-info-items{display:flex;flex-direction:column;gap:0.5rem;}
    .fp-info-item{display:flex;align-items:center;gap:0.6rem;font-size:0.88rem;color:var(--text-mid);}
    .fp-info-icon{padding:0.2rem 0.55rem;background:var(--green-pale);border-radius:6px;font-size:0.68rem;font-weight:700;color:var(--green-deep);letter-spacing:0.5px;text-transform:uppercase;flex-shrink:0;min-width:60px;text-align:center;}
    .fp-crops-row{display:flex;flex-wrap:wrap;gap:0.4rem;margin-top:0.5rem;}
    .fp-crop-tag{background:var(--green-pale);color:var(--green-deep);padding:0.25rem 0.7rem;border-radius:100px;font-size:0.76rem;font-weight:600;}
    .fp-actions{display:flex;gap:0.75rem;margin-top:1.5rem;padding-top:1.25rem;border-top:2px solid var(--green-pale);}
    .fp-report-btn{flex:1;padding:0.75rem;border-radius:12px;border:2px solid rgba(224,92,74,0.35);background:rgba(224,92,74,0.06);color:#c0392b;font-family:'DM Sans',sans-serif;font-size:0.875rem;font-weight:700;cursor:pointer;transition:all .2s;display:flex;align-items:center;justify-content:center;gap:6px;}
    .fp-report-btn:hover{background:rgba(224,92,74,0.14);border-color:#e05c4a;}
    .fp-close-btn{flex:1;padding:0.75rem;border-radius:12px;border:none;background:var(--green-fresh);color:white;font-family:'DM Sans',sans-serif;font-size:0.875rem;font-weight:700;cursor:pointer;transition:all .2s;}
    .fp-close-btn:hover{background:var(--green-mid);}

    /* FLOATING REPORT BUTTON (farmer profile modal) - fixed right side tab */
    .fp-floating-report{display:none;position:fixed;right:0;top:50%;transform:translateY(-50%);z-index:3500;background:#c0392b;color:white;border:none;border-radius:10px 0 0 10px;padding:0.9rem 0.6rem;font-family:'DM Sans',sans-serif;font-size:0;cursor:pointer;box-shadow:-4px 0 18px rgba(192,57,43,0.4);writing-mode:vertical-rl;text-orientation:mixed;transition:all .2s;width:36px;display:none;align-items:center;justify-content:center;}
    .fp-floating-report:hover{background:#a93226;width:42px;box-shadow:-6px 0 24px rgba(192,57,43,0.55);}
    .fp-floating-report.show{display:flex;}
    .fp-floating-report svg{width:18px;height:18px;fill:none;stroke:white;stroke-width:2.5;flex-shrink:0;}

    /* CROP CARDS inside farmer profile modal */
    .fp-crop-cards{display:flex;flex-direction:column;gap:0.6rem;margin-top:0.5rem;}
    .fp-crop-card{display:flex;align-items:center;gap:0.85rem;background:var(--green-pale);border-radius:12px;padding:0.7rem 0.9rem;transition:background .2s;}
    .fp-crop-card:hover{background:#c5e8cc;}
    .fp-crop-img{width:52px;height:52px;border-radius:10px;overflow:hidden;flex-shrink:0;background:var(--green-light);}
    .fp-crop-img img{width:100%;height:100%;object-fit:cover;}
    .fp-crop-img-placeholder{width:100%;height:100%;display:flex;align-items:center;justify-content:center;font-size:0.65rem;color:var(--text-light);text-align:center;}
    .fp-crop-info{flex:1;}
    .fp-crop-name{font-weight:700;font-size:0.9rem;color:var(--green-deep);}
    .fp-crop-price{font-family:'Space Mono',monospace;font-size:0.82rem;color:var(--green-fresh);font-weight:700;margin-top:2px;}
    .fp-crop-unit{font-size:0.72rem;color:var(--text-light);}
    .fp-buy-btn{padding:0.45rem 1rem;border-radius:8px;border:none;background:var(--green-fresh);color:white;font-family:'DM Sans',sans-serif;font-size:0.8rem;font-weight:700;cursor:pointer;transition:all .2s;flex-shrink:0;}
    .fp-buy-btn:hover{background:var(--green-mid);transform:translateY(-1px);}

    /* REPORT PAGE */
    .report-page{padding:0;min-height:100vh;background:var(--cream);}
    .report-header{background:linear-gradient(135deg,#c0392b,#e74c3c);padding:3rem;color:white;position:relative;overflow:hidden;}
    .report-header::before{content:'';position:absolute;inset:0;background:url("data:image/svg+xml,%3Csvg width='60' height='60' viewBox='0 0 60 60' xmlns='http://www.w3.org/2000/svg'%3E%3Cg fill='white' fill-opacity='0.04'%3E%3Ccircle cx='30' cy='30' r='2'/%3E%3C/g%3E%3C/svg%3E");}
    .report-header h2{font-family:'Playfair Display',serif;font-size:1.9rem;margin-bottom:0.4rem;position:relative;}
    .report-header p{color:rgba(255,255,255,0.75);font-size:0.95rem;position:relative;}
    .report-body{max-width:680px;margin:0 auto;padding:2.5rem 2rem;}
    .report-farmer-card{background:white;border-radius:16px;padding:1.25rem 1.5rem;box-shadow:var(--shadow);display:flex;align-items:center;gap:1rem;margin-bottom:2rem;border-left:4px solid #e74c3c;}
    .report-farmer-av{width:52px;height:52px;border-radius:50%;background:linear-gradient(135deg,var(--green-fresh),var(--green-mid));display:flex;align-items:center;justify-content:center;font-size:1.3rem;font-weight:900;color:white;flex-shrink:0;overflow:hidden;}
    .report-farmer-av img{width:100%;height:100%;object-fit:cover;}
    .report-farmer-name{font-weight:700;font-size:1rem;color:var(--green-deep);}
    .report-farmer-loc{font-size:0.8rem;color:var(--text-light);margin-top:2px;}
    .report-card{background:white;border-radius:16px;padding:1.75rem;box-shadow:var(--shadow);margin-bottom:1.25rem;}
    .report-card h3{font-family:'Playfair Display',serif;font-size:1rem;color:var(--green-deep);margin-bottom:1rem;}
    .report-categories{display:grid;grid-template-columns:1fr 1fr;gap:0.5rem;margin-bottom:0.5rem;}
    .report-cat-btn{padding:0.65rem 1rem;border-radius:10px;border:2px solid var(--green-pale);background:transparent;font-family:'DM Sans',sans-serif;font-size:0.82rem;font-weight:600;color:var(--text-mid);cursor:pointer;transition:all .2s;text-align:left;}
    .report-cat-btn:hover{border-color:#e74c3c;color:#c0392b;}
    .report-cat-btn.active{border-color:#e74c3c;background:rgba(231,76,60,0.07);color:#c0392b;}
    .report-form-label{display:block;font-size:0.75rem;font-weight:700;color:var(--text-mid);margin-bottom:0.4rem;text-transform:uppercase;letter-spacing:0.5px;}
    .report-form-input{width:100%;padding:0.8rem 1rem;border:2px solid var(--green-pale);border-radius:10px;font-family:'DM Sans',sans-serif;font-size:0.92rem;color:var(--text-dark);background:var(--cream);outline:none;transition:border-color .2s;}
    .report-form-input:focus{border-color:#e74c3c;}
    textarea.report-form-input{resize:vertical;min-height:130px;}
    .report-submit-btn{width:100%;padding:1rem;border-radius:12px;border:none;background:linear-gradient(135deg,#c0392b,#e74c3c);color:white;font-family:'DM Sans',sans-serif;font-size:1rem;font-weight:700;cursor:pointer;transition:all .2s;box-shadow:0 6px 20px rgba(192,57,43,0.3);display:flex;align-items:center;justify-content:center;gap:8px;}
    .report-submit-btn:hover{transform:translateY(-2px);box-shadow:0 10px 28px rgba(192,57,43,0.45);}

    /* STUDENT PROFILE PAGE */
    .stu-page{background:var(--cream);min-height:100vh;}
    .stu-hero{background:linear-gradient(135deg,var(--green-deep),var(--green-mid));padding:3rem 3rem 5rem;position:relative;overflow:hidden;}
    .stu-hero::before{content:'';position:absolute;inset:0;background:url("data:image/svg+xml,%3Csvg width='60' height='60' viewBox='0 0 60 60' xmlns='http://www.w3.org/2000/svg'%3E%3Cg fill='%2374c69d' fill-opacity='0.07'%3E%3Ccircle cx='30' cy='30' r='2'/%3E%3C/g%3E%3C/svg%3E");}
    .stu-hero-inner{position:relative;z-index:1;display:flex;align-items:center;gap:1.75rem;flex-wrap:wrap;}
    .stu-avatar-wrap{position:relative;flex-shrink:0;}
    .stu-avatar-circle{width:90px;height:90px;border-radius:50%;border:4px solid rgba(255,255,255,0.3);background:linear-gradient(135deg,var(--green-fresh),var(--green-mid));display:flex;align-items:center;justify-content:center;font-family:'Playfair Display',serif;font-size:2.2rem;font-weight:900;color:white;overflow:hidden;box-shadow:0 8px 24px rgba(0,0,0,0.25);}
    .stu-avatar-circle img{width:100%;height:100%;object-fit:cover;}
    .stu-avatar-edit{position:absolute;bottom:0;right:0;width:28px;height:28px;border-radius:50%;background:var(--gold);border:2px solid white;display:flex;align-items:center;justify-content:center;cursor:pointer;transition:all .2s;}
    .stu-avatar-edit:hover{background:var(--earth-light);transform:scale(1.1);}
    .stu-avatar-edit svg{width:13px;height:13px;fill:var(--green-deep);}
    .stu-avatar-input{display:none;}
    .stu-hero-info h2{font-family:'Playfair Display',serif;font-size:1.7rem;color:white;margin-bottom:0.2rem;}
    .stu-hero-info p{color:rgba(255,255,255,0.65);font-size:0.9rem;}
    .stu-badge{display:inline-flex;align-items:center;gap:5px;background:rgba(244,161,42,0.2);border:1px solid rgba(244,161,42,0.45);color:var(--gold);padding:0.25rem 0.8rem;border-radius:100px;font-size:0.72rem;font-weight:700;letter-spacing:0.5px;text-transform:uppercase;margin-top:0.5rem;}

    .stu-body{max-width:820px;margin:-2.5rem auto 0;padding:0 2rem 3rem;position:relative;z-index:2;}
    .stu-stats-row{display:grid;grid-template-columns:repeat(3,1fr);gap:1rem;margin-bottom:1.75rem;}
    .stu-stat{background:white;border-radius:14px;padding:1.1rem 1.25rem;box-shadow:var(--shadow);text-align:center;}
    .stu-stat-val{font-family:'Space Mono',monospace;font-size:1.4rem;font-weight:700;color:var(--green-deep);}
    .stu-stat-lbl{font-size:0.72rem;color:var(--text-light);text-transform:uppercase;letter-spacing:1px;margin-top:3px;}

    .stu-section-card{background:white;border-radius:16px;padding:1.75rem;box-shadow:var(--shadow);margin-bottom:1.25rem;}
    .stu-section-title{font-family:'Playfair Display',serif;font-size:1rem;color:var(--green-deep);margin-bottom:1.25rem;padding-bottom:0.75rem;border-bottom:2px solid var(--green-pale);display:flex;align-items:center;justify-content:space-between;}
    .stu-edit-toggle{font-size:0.78rem;font-weight:700;color:var(--green-fresh);cursor:pointer;font-family:'DM Sans',sans-serif;background:none;border:none;padding:0;}
    .stu-edit-toggle:hover{color:var(--green-mid);}
    .stu-info-row{display:flex;justify-content:space-between;align-items:center;padding:0.55rem 0;border-bottom:1px solid var(--green-pale);font-size:0.9rem;}
    .stu-info-row:last-child{border-bottom:none;}
    .stu-info-label{color:var(--text-light);font-size:0.8rem;font-weight:600;text-transform:uppercase;letter-spacing:0.5px;}
    .stu-info-value{color:var(--text-dark);font-weight:600;}
    .stu-form-grid{display:grid;grid-template-columns:1fr 1fr;gap:0.85rem;}
    .stu-form-group{margin-bottom:0;}
    .stu-form-label{display:block;font-size:0.72rem;font-weight:700;color:var(--text-mid);margin-bottom:0.35rem;text-transform:uppercase;letter-spacing:0.5px;}
    .stu-form-input{width:100%;padding:0.72rem 1rem;border:2px solid var(--green-pale);border-radius:10px;font-family:'DM Sans',sans-serif;font-size:0.9rem;color:var(--text-dark);background:var(--cream);outline:none;transition:border-color .2s;}
    .stu-form-input:focus{border-color:var(--green-fresh);background:white;}
    .stu-form-input::placeholder{color:#bbb;}
    .stu-save-btn{margin-top:1.1rem;padding:0.75rem 2rem;border-radius:10px;border:none;background:var(--green-fresh);color:white;font-family:'DM Sans',sans-serif;font-size:0.9rem;font-weight:700;cursor:pointer;transition:all .2s;box-shadow:0 4px 14px rgba(64,145,108,0.3);}
    .stu-save-btn:hover{background:var(--green-mid);transform:translateY(-1px);}
    .stu-danger-zone{background:rgba(231,76,60,0.05);border:1px solid rgba(231,76,60,0.2);border-radius:12px;padding:1.25rem 1.5rem;display:flex;align-items:center;justify-content:space-between;gap:1rem;flex-wrap:wrap;}
    .stu-danger-text h4{font-size:0.9rem;font-weight:700;color:#c0392b;margin-bottom:0.25rem;}
    .stu-danger-text p{font-size:0.8rem;color:var(--text-light);}
    .stu-danger-btn{padding:0.55rem 1.25rem;border-radius:8px;border:2px solid rgba(231,76,60,0.4);background:transparent;color:#c0392b;font-family:'DM Sans',sans-serif;font-size:0.82rem;font-weight:700;cursor:pointer;transition:all .2s;}
    .stu-danger-btn:hover{background:rgba(231,76,60,0.1);}

    /* ORDERS SECTION (farmer dashboard) */
    .farm-orders-hdr{display:flex;align-items:center;justify-content:space-between;margin-bottom:1.5rem;flex-wrap:wrap;gap:1rem;}
    .farm-order-filter{display:flex;gap:0.4rem;}
    .farm-order-filter-btn{padding:0.38rem 0.9rem;border-radius:100px;border:1px solid var(--farm-border);background:transparent;color:var(--farm-muted);font-family:'DM Sans',sans-serif;font-size:0.78rem;font-weight:600;cursor:pointer;transition:all .2s;}
    .farm-order-filter-btn:hover{border-color:var(--farm-accent);color:var(--farm-text);}
    .farm-order-filter-btn.active{background:rgba(82,201,132,0.15);border-color:var(--farm-accent);color:var(--farm-accent);}
    .farm-orders-table{background:var(--farm-card);border:1px solid var(--farm-border);border-radius:16px;overflow:hidden;}
    .farm-orders-thead{display:grid;grid-template-columns:2fr 1.5fr 1fr 1fr 1fr 0.8fr;gap:0;padding:0.75rem 1.25rem;border-bottom:1px solid var(--farm-border);background:rgba(82,201,132,0.05);}
    .farm-orders-th{font-size:0.68rem;font-weight:700;text-transform:uppercase;letter-spacing:1.2px;color:var(--farm-muted);}
    .farm-order-row{display:grid;grid-template-columns:2fr 1.5fr 1fr 1fr 1fr 0.8fr;gap:0;padding:1rem 1.25rem;border-bottom:1px solid var(--farm-border);align-items:center;cursor:pointer;transition:background .18s;}
    .farm-order-row:last-child{border-bottom:none;}
    .farm-order-row:hover{background:rgba(82,201,132,0.06);}
    .farm-order-student{display:flex;align-items:center;gap:0.6rem;}
    .farm-order-stu-av{width:34px;height:34px;border-radius:50%;background:linear-gradient(135deg,#3498db,#1a5276);display:flex;align-items:center;justify-content:center;font-size:0.8rem;font-weight:700;color:white;flex-shrink:0;overflow:hidden;}
    .farm-order-stu-av img{width:100%;height:100%;object-fit:cover;}
    .farm-order-stu-name{font-size:0.88rem;font-weight:600;color:var(--farm-text);}
    .farm-order-stu-email{font-size:0.72rem;color:var(--farm-muted);margin-top:1px;}
    .farm-order-id{font-family:'Space Mono',monospace;font-size:0.75rem;color:var(--farm-muted);}
    .farm-order-amount{font-family:'Space Mono',monospace;font-size:0.88rem;font-weight:700;color:var(--farm-accent);}
    .farm-order-date{font-size:0.78rem;color:var(--farm-muted);}
    .farm-order-items-count{font-size:0.82rem;color:var(--farm-text);font-weight:600;}
    .farm-order-status{display:inline-flex;align-items:center;padding:0.22rem 0.65rem;border-radius:100px;font-size:0.68rem;font-weight:700;letter-spacing:0.3px;}
    .order-status-pending{background:rgba(244,161,42,0.15);color:#f4a12a;border:1px solid rgba(244,161,42,0.35);}
    .order-status-delivered{background:rgba(82,201,132,0.15);color:#52c984;border:1px solid rgba(82,201,132,0.35);}
    .farm-order-action{display:flex;justify-content:flex-end;}
    .farm-order-view-btn{padding:0.3rem 0.75rem;border-radius:7px;border:1px solid var(--farm-border);background:transparent;color:var(--farm-accent);font-family:'DM Sans',sans-serif;font-size:0.75rem;font-weight:600;cursor:pointer;transition:all .2s;}
    .farm-order-view-btn:hover{background:rgba(82,201,132,0.12);border-color:var(--farm-accent);}
    .farm-no-orders{text-align:center;padding:4rem 2rem;color:var(--farm-muted);}
    .farm-no-orders-title{font-size:1rem;font-weight:600;color:var(--farm-text);margin-bottom:0.4rem;}

    /* ORDER DETAIL MODAL */
    .order-modal{background:var(--farm-card);border:1px solid var(--farm-border);border-radius:20px;width:100%;max-width:580px;max-height:92vh;overflow-y:auto;box-shadow:0 30px 80px rgba(0,0,0,0.55);}
    .order-modal-hero{background:linear-gradient(135deg,rgba(82,201,132,0.12),rgba(82,201,132,0.04));border-bottom:1px solid var(--farm-border);padding:1.5rem 1.75rem;display:flex;align-items:center;gap:1rem;}
    .order-modal-stu-av{width:52px;height:52px;border-radius:50%;background:linear-gradient(135deg,#3498db,#1a5276);display:flex;align-items:center;justify-content:center;font-size:1.3rem;font-weight:700;color:white;flex-shrink:0;overflow:hidden;}
    .order-modal-stu-av img{width:100%;height:100%;object-fit:cover;}
    .order-modal-stu-info{flex:1;}
    .order-modal-stu-name{font-family:'Syne',sans-serif;font-size:1.05rem;font-weight:700;color:var(--farm-text);}
    .order-modal-stu-meta{font-size:0.78rem;color:var(--farm-muted);margin-top:2px;}
    .order-modal-id{font-family:'Space Mono',monospace;font-size:0.72rem;color:var(--farm-accent);margin-top:4px;}
    .order-modal-close{background:rgba(255,255,255,0.07);border:none;color:var(--farm-muted);width:30px;height:30px;border-radius:50%;cursor:pointer;font-size:1rem;display:flex;align-items:center;justify-content:center;transition:all .2s;flex-shrink:0;}
    .order-modal-close:hover{background:rgba(231,76,60,0.2);color:#e05c4a;}
    .order-modal-body{padding:1.5rem 1.75rem;}
    .order-modal-section{margin-bottom:1.5rem;}
    .order-modal-section-title{font-size:0.7rem;font-weight:700;text-transform:uppercase;letter-spacing:1.5px;color:var(--farm-accent);margin-bottom:0.75rem;}
    .order-info-grid{display:grid;grid-template-columns:1fr 1fr;gap:0.6rem;}
    .order-info-tile{background:rgba(82,201,132,0.06);border:1px solid var(--farm-border);border-radius:10px;padding:0.8rem 1rem;}
    .order-info-tile-label{font-size:0.68rem;font-weight:600;text-transform:uppercase;letter-spacing:0.8px;color:var(--farm-muted);margin-bottom:0.3rem;}
    .order-info-tile-val{font-size:0.9rem;font-weight:700;color:var(--farm-text);}
    .order-items-list{display:flex;flex-direction:column;gap:0.6rem;}
    .order-item-row{display:flex;align-items:center;gap:0.85rem;background:rgba(82,201,132,0.05);border:1px solid var(--farm-border);border-radius:12px;padding:0.75rem 1rem;}
    .order-item-img{width:46px;height:46px;border-radius:9px;overflow:hidden;flex-shrink:0;background:var(--farm-surface);}
    .order-item-img img{width:100%;height:100%;object-fit:cover;}
    .order-item-img-ph{width:100%;height:100%;display:flex;align-items:center;justify-content:center;font-size:0.6rem;color:var(--farm-muted);}
    .order-item-info{flex:1;}
    .order-item-name{font-size:0.88rem;font-weight:600;color:var(--farm-text);}
    .order-item-meta{font-size:0.75rem;color:var(--farm-muted);margin-top:2px;}
    .order-item-price{font-family:'Space Mono',monospace;font-size:0.85rem;font-weight:700;color:var(--farm-accent);}
    .order-delivery-box{background:rgba(82,201,132,0.06);border:1px solid var(--farm-border);border-radius:12px;padding:1rem 1.1rem;}
    .order-delivery-row{display:flex;justify-content:space-between;align-items:flex-start;padding:0.35rem 0;font-size:0.85rem;border-bottom:1px solid var(--farm-border);}
    .order-delivery-row:last-child{border-bottom:none;}
    .order-delivery-label{color:var(--farm-muted);font-size:0.78rem;font-weight:600;text-transform:uppercase;letter-spacing:0.5px;}
    .order-delivery-val{color:var(--farm-text);font-weight:600;text-align:right;max-width:60%;}
    .order-total-bar{display:flex;justify-content:space-between;align-items:center;padding:1rem 1.1rem;background:rgba(82,201,132,0.1);border:1px solid rgba(82,201,132,0.25);border-radius:12px;margin-top:0.75rem;}
    .order-total-lbl{font-size:0.85rem;font-weight:700;color:var(--farm-text);}
    .order-total-val{font-family:'Space Mono',monospace;font-size:1.1rem;font-weight:700;color:var(--farm-accent);}
    .order-modal-footer{padding:1rem 1.75rem 1.5rem;display:flex;gap:0.75rem;border-top:1px solid var(--farm-border);}
    .order-mark-btn{flex:1;padding:0.65rem;border-radius:10px;border:none;background:linear-gradient(135deg,var(--farm-accent),#28a06b);color:white;font-family:'DM Sans',sans-serif;font-size:0.875rem;font-weight:700;cursor:pointer;transition:all .2s;}
    .order-mark-btn:hover{transform:translateY(-1px);}
    .order-mark-btn:disabled{opacity:0.5;cursor:not-allowed;transform:none;}

    /* RESPONSIVE */
    @media(max-width:900px){.farm-stats-row{grid-template-columns:repeat(2,1fr)}.farm-grid2{grid-template-columns:1fr}.farm-sidebar{display:none}.farm-main{padding:1.25rem}.fp-stats-row{grid-template-columns:repeat(3,1fr)}}
    @media(max-width:768px){.hero{padding:3rem 1.5rem}.section{padding:3rem 1.5rem}.cart-layout,.pay-layout{grid-template-columns:1fr}.cart-page,.pay-page,.mkt-body{padding:1.5rem}.mkt-header{padding:1.5rem}.form-row,.farm-info-grid,.farm-form-row{grid-template-columns:1fr}.nav-links .nav-btn:not(.nav-cta){display:none}.report-categories{grid-template-columns:1fr}}
  </style>
</head>
<body>

<!-- TOAST -->
<div class="toast" id="toast"><span id="toast-msg"></span></div>

<!-- FLOATING CART -->
<div class="floating-cart" id="floating-cart" onclick="showPage('cart')">
  <svg viewBox="0 0 24 24"><circle cx="9" cy="21" r="1"/><circle cx="20" cy="21" r="1"/><path d="M1 1h4l2.68 13.39a2 2 0 0 0 2 1.61h9.72a2 2 0 0 0 2-1.61L23 6H6"/></svg>
  <div class="cart-badge" id="cart-badge">0</div>
</div>

<!-- PUBLIC NAVBAR -->
<nav class="navbar" id="main-navbar">
  <div class="nav-brand" onclick="showPage('home')">
    <div class="nav-logo"><img src="https://tse3.mm.bing.net/th/id/OIP.l0Yc4nXvTNf_2YV89vgP_QAAAA?cb=defcache2&defcache=1&rs=1&pid=ImgDetMain&o=7&rm=3" alt="FUTO"/></div>
    <div class="nav-brand-text">FUTO Agri-Market<span>Farm to Campus</span></div>
  </div>
  <div class="nav-links" id="nav-links">
    <button class="nav-btn active" id="nav-home-btn" onclick="showPage('home')">Home</button>
    <button class="nav-btn" id="nav-about-btn" onclick="scrollToAbout()">About</button>
    <button class="nav-btn" id="nav-market-btn" style="display:none;" onclick="showPage('marketplace')">Marketplace</button>
    <button class="nav-btn nav-cta" id="nav-signin-btn" onclick="showPage('login')">Sign In</button>
    <div class="nav-user-info" id="user-nav-info" style="display:none;">
      <div class="nav-user-avatar" id="user-avatar" onclick="showPage('student-profile')" title="My Profile" style="cursor:pointer;border:2px solid rgba(116,198,157,0.4);transition:all .2s;" onmouseover="this.style.borderColor='var(--gold)'" onmouseout="this.style.borderColor='rgba(116,198,157,0.4)'"><span id="user-avatar-letter">?</span></div>
      <span id="user-nav-name" onclick="showPage('student-profile')" style="cursor:pointer;" onmouseover="this.style.color='white'" onmouseout="this.style.color=''">User</span>
      <button class="nav-signout" onclick="logout()">Sign Out</button>
    </div>
  </div>
</nav>

<!-- ======== HOME ======== -->
<div class="page active" id="page-home">
  <section class="hero">
    <div class="hero-content">
      <div class="hero-badge">FUTO Official Farm Marketplace</div>
      <h1>Fresh From <span class="accent">Local Farms</span> to Your Table</h1>
      <p>Connecting FUTO students with farmers around Ihiagwa, Obinze and Eziobodo. Buy fresh produce directly, reduce waste, support your local community.</p>
      <div class="hero-actions">
        <button class="btn btn-primary" onclick="showPage('login')">Shop Now</button>
        <button class="btn btn-outline" onclick="showPage('register')">Sell Your Crops</button>
      </div>
      <div class="hero-stats">
        <div class="hero-stat"><div class="num">120+</div><div class="lbl">Farmers</div></div>
        <div class="hero-stat"><div class="num">850+</div><div class="lbl">Students Served</div></div>
        <div class="hero-stat"><div class="num">40%</div><div class="lbl">Less Waste</div></div>
      </div>
    </div>
  </section>
  <section class="section">
    <div class="section-header">
      <div class="section-label">Simple Process</div>
      <h2 class="section-title">How FUTO Agri-Market Works</h2>
      <p class="section-sub">Four easy steps from farm to your door</p>
    </div>
    <div class="steps-grid">
      <div class="step-card"><div class="step-num">01</div><div class="step-title">Farmers Register and List</div><div class="step-desc">Local farmers create a profile and post their available crops with prices, quantity and harvest date.</div></div>
      <div class="step-card"><div class="step-num">02</div><div class="step-title">Students Browse and Shop</div><div class="step-desc">FUTO students browse the marketplace, add items to cart, and discover fresh produce near campus.</div></div>
      <div class="step-card"><div class="step-num">03</div><div class="step-title">Pay Securely Online</div><div class="step-desc">Pay via card, bank transfer, or mobile money. Get your order delivered or pick up at the farm.</div></div>
      <div class="step-card"><div class="step-num">04</div><div class="step-title">Fresh Delivery</div><div class="step-desc">Farmers pack and deliver within 24 hours. No middlemen — fresher food, better prices for everyone.</div></div>
    </div>
  </section>
  <section class="section products-section">
    <div class="section-header">
      <div class="section-label">Fresh Picks</div>
      <h2 class="section-title">Featured Produce</h2>
    </div>
    <div class="filter-bar">
      <button class="filter-btn active" onclick="filterHome('all',this)">All</button>
      <button class="filter-btn" onclick="filterHome('veg',this)">Vegetables</button>
      <button class="filter-btn" onclick="filterHome('fruit',this)">Fruits</button>
      <button class="filter-btn" onclick="filterHome('grain',this)">Grains</button>
    </div>
    <div class="products-grid" id="featured-grid"></div>
  </section>
  <section id="about-home" class="section" style="background:linear-gradient(180deg,var(--cream),#f7fbf8);">
    <div class="section-header">
      <div class="section-label">Who We Are</div>
      <h2 class="section-title">About FUTO Agri-Market</h2>
      <p class="section-sub">We connect campus buyers with nearby farmers — helping you sell produce faster and put fresh food on students' tables.</p>
    </div>
    <div style="max-width:960px;margin:0 auto;display:grid;grid-template-columns:1fr 1fr;gap:2rem;align-items:center;">
      <div style="font-size:0.98rem;color:var(--text-mid);line-height:1.75;">
        <p><strong>For Farmers:</strong> List your harvest in minutes, reach thousands of students, and move produce before it spoils.</p>
        <p style="margin-top:0.8rem;"><strong>For Students:</strong> Discover fresh, affordable local produce, support campus farmers, and order for delivery or pickup.</p>
        <p style="margin-top:0.8rem;">Join the community — reduce food waste, support local livelihoods, and get fresher food every week.</p>
      </div>
      <div style="display:flex;flex-direction:column;gap:0.8rem;">
        <div style="background:var(--white);padding:1.2rem;border-radius:12px;box-shadow:var(--shadow);">Easy Listings — post photos, price and quantity</div>
        <div style="background:var(--white);padding:1.2rem;border-radius:12px;box-shadow:var(--shadow);">Faster Sales — reach campus buyers directly</div>
        <div style="background:var(--white);padding:1.2rem;border-radius:12px;box-shadow:var(--shadow);">Local Impact — keep food local, support neighbors</div>
      </div>
    </div>
  </section>
  <section class="section" style="background:linear-gradient(135deg,var(--green-deep),var(--green-mid));color:white;text-align:center;">
    <div class="section-label" style="color:var(--green-light);">Are You a Farmer?</div>
    <h2 class="section-title" style="color:white;">Stop Losing Your Harvest</h2>
    <p style="color:rgba(255,255,255,0.75);margin-top:0.75rem;margin-bottom:2rem;max-width:500px;margin-left:auto;margin-right:auto;">Register on FUTO Agri-Market today and connect with thousands of students ready to buy your produce.</p>
    <button class="btn btn-primary" onclick="showPage('register')" style="font-size:1rem;padding:1rem 2.5rem;">Register as a Farmer</button>
  </section>
</div>

<!-- ======== LOGIN ======== -->
<div class="page" id="page-login">
  <div class="back-bar"><button onclick="showPage('home')">Back</button></div>
  <div class="auth-wrap">
    <div class="auth-box">
      <div class="auth-brand"><div class="auth-logo-mark"><img src="https://tse3.mm.bing.net/th/id/OIP.l0Yc4nXvTNf_2YV89vgP_QAAAA?cb=defcache2&defcache=1&rs=1&pid=ImgDetMain&o=7&rm=3" alt="FUTO logo"></div><h2>Welcome Back</h2><p>Sign in to FUTO Agri-Market</p></div>
      <div class="auth-card">
        <div class="role-toggle">
          <button class="role-btn active" id="ls-btn" onclick="setLoginRole('student')">Student</button>
          <button class="role-btn" id="lf-btn" onclick="setLoginRole('farmer')">Farmer</button>
        </div>
        <div class="form-group"><label class="form-label">Email Address</label><input class="form-input" type="email" placeholder="you@example.com" id="l-email"/></div>
        <div class="form-group"><label class="form-label">Password</label><input class="form-input" type="password" placeholder="Enter your password" id="l-pass"/></div>
        <button class="btn btn-green" style="width:100%;justify-content:center;margin-top:0.5rem;" onclick="doLogin()">Sign In</button>
        <div class="auth-divider">or</div>
        <div class="auth-footer">No account? <span class="auth-link" onclick="showPage('register')">Register here</span></div>
      </div>
    </div>
  </div>
</div>

<!-- ======== REGISTER ======== -->
<div class="page" id="page-register">
  <div class="back-bar"><button onclick="showPage('home')">Back</button></div>
  <div class="auth-wrap">
    <div class="auth-box" style="max-width:500px;">
      <div class="auth-brand"><div class="auth-logo-mark"><img src="https://tse3.mm.bing.net/th/id/OIP.l0Yc4nXvTNf_2YV89vgP_QAAAA?cb=defcache2&defcache=1&rs=1&pid=ImgDetMain&o=7&rm=3" alt="FUTO logo"></div><h2>Create Account</h2><p>Join FUTO Agri-Market today</p></div>
      <div class="auth-card">
        <div class="role-toggle">
          <button class="role-btn active" id="rs-btn" onclick="setRegRole('student')">Student</button>
          <button class="role-btn" id="rf-btn" onclick="setRegRole('farmer')">Farmer</button>
        </div>
        <div class="form-row">
          <div class="form-group"><label class="form-label">First Name</label><input class="form-input" placeholder="John" id="r-fname"/></div>
          <div class="form-group"><label class="form-label">Last Name</label><input class="form-input" placeholder="Doe" id="r-lname"/></div>
        </div>
        <div class="form-group"><label class="form-label">Email</label><input class="form-input" type="email" placeholder="you@futo.edu.ng" id="r-email"/></div>
        <div class="form-group"><label class="form-label">Phone</label><input class="form-input" placeholder="+234 800 000 0000" id="r-phone"/></div>
        <div class="form-group" id="r-matric-grp"><label class="form-label">Matric Number</label><input class="form-input" placeholder="2021/1234567"/></div>
        <div class="form-group" id="r-farm-grp" style="display:none;"><label class="form-label">Farm Location</label><input class="form-input" placeholder="e.g. Ihiagwa, near FUTO Gate" id="r-farmloc"/></div>
        <div class="form-group"><label class="form-label">Password</label><input class="form-input" type="password" placeholder="Create a password" id="r-pass"/></div>
        <div class="form-group"><label class="form-label">Confirm Password</label><input class="form-input" type="password" placeholder="Repeat password" id="r-cpass"/></div>
        <button class="btn btn-green" style="width:100%;justify-content:center;margin-top:0.5rem;" onclick="doRegister()">Create Account</button>
        <div class="auth-footer" style="margin-top:1rem;">Already have an account? <span class="auth-link" onclick="showPage('login')">Sign in</span></div>
      </div>
    </div>
  </div>
</div>

<!-- ======== MARKETPLACE ======== -->
<div class="page" id="page-marketplace">
  <div class="mkt-header">
    <h2>Marketplace</h2>
    <p>Browse fresh produce from farmers around FUTO</p>
    <div class="search-bar">
      <input class="search-input" placeholder="Search for tomatoes, yam, pineapple..." id="search-input" oninput="searchProducts()"/>
      <button class="btn btn-primary" onclick="searchProducts()">Search</button>
    </div>
  </div>
  <div class="mkt-body">
    <div class="filter-bar" style="margin-bottom:1.5rem;">
      <button class="filter-btn active" onclick="filterMarket('all',this)">All</button>
      <button class="filter-btn" onclick="filterMarket('veg',this)">Vegetables</button>
      <button class="filter-btn" onclick="filterMarket('fruit',this)">Fruits</button>
      <button class="filter-btn" onclick="filterMarket('grain',this)">Grains and Tubers</button>
      <button class="filter-btn" onclick="filterMarket('leaf',this)">Leafy Greens</button>
    </div>
    <div class="products-grid" id="market-grid"></div>
  </div>
</div>

<!-- ======== CART ======== -->
<div class="page" id="page-cart">
  <div class="back-bar"><button onclick="showPage('marketplace')">Back to Marketplace</button></div>
  <div class="cart-page">
    <h2>Your Cart</h2>
    <div class="cart-layout">
      <div>
        <div class="cart-items" id="cart-items-list"></div>
        <div id="empty-cart" style="text-align:center;padding:3rem;color:var(--text-light);display:none;">
          <p style="font-size:1.1rem;margin-bottom:1.5rem;">Your cart is empty</p>
          <button class="btn btn-green" onclick="showPage('marketplace')">Browse Products</button>
        </div>
      </div>
      <div>
        <div class="cart-summary">
          <h3>Order Summary</h3>
          <div class="summary-row"><span>Subtotal</span><span id="cart-subtotal">₦0</span></div>
          <div class="summary-row"><span>Delivery Fee</span><span>₦500</span></div>
          <div class="summary-total"><span>Total</span><span class="total-price" id="cart-total">₦500</span></div>
          <button class="btn btn-primary" style="width:100%;justify-content:center;margin-top:1.25rem;" onclick="showPage('payment')">Proceed to Payment</button>
          <button class="btn btn-outline" style="width:100%;justify-content:center;margin-top:0.5rem;color:var(--text-mid);border-color:var(--green-pale);" onclick="showPage('marketplace')">Continue Shopping</button>
        </div>
      </div>
    </div>
  </div>
</div>

<!-- ======== PAYMENT ======== -->
<div class="page" id="page-payment">
  <div class="back-bar"><button onclick="showPage('cart')">Back to Cart</button></div>
  <div class="pay-page">
    <h2>Checkout</h2>
    <div class="prog-steps">
      <div class="prog-step"><div class="prog-dot done">1</div><div class="prog-lbl">Cart</div></div>
      <div class="prog-line done"></div>
      <div class="prog-step"><div class="prog-dot cur">2</div><div class="prog-lbl">Payment</div></div>
      <div class="prog-line"></div>
      <div class="prog-step"><div class="prog-dot">3</div><div class="prog-lbl">Confirm</div></div>
    </div>
    <div class="pay-layout">
      <div>
        <div class="pay-card">
          <h3>Delivery Address</h3>
          <div class="form-group"><label class="form-label">Full Name</label><input class="form-input" placeholder="John Doe"/></div>
          <div class="form-row">
            <div class="form-group"><label class="form-label">Hostel / Block</label><input class="form-input" placeholder="e.g. Block C, Room 12"/></div>
            <div class="form-group"><label class="form-label">Phone</label><input class="form-input" placeholder="+234 800 000 0000"/></div>
          </div>
          <div class="form-group"><label class="form-label">Notes</label><input class="form-input" placeholder="Delivery instructions..."/></div>
        </div>
        <div class="pay-card">
          <h3>Payment Method</h3>
          <div class="pay-methods">
            <div class="pay-method active" onclick="selectPay(this)">Card</div>
            <div class="pay-method" onclick="selectPay(this)">Bank Transfer</div>
            <div class="pay-method" onclick="selectPay(this)">USSD</div>
            <div class="pay-method" onclick="selectPay(this)">Opay</div>
          </div>
          <div class="card-visual">
            <div class="card-chip">CARD</div>
            <div class="card-number" id="card-display">.... .... .... ....</div>
            <div class="card-info"><span>Card Holder</span><span>Expires</span></div>
          </div>
          <div class="form-group"><label class="form-label">Card Number</label><input class="form-input" placeholder="0000 0000 0000 0000" maxlength="19" oninput="fmtCard(this)"/></div>
          <div class="form-row">
            <div class="form-group"><label class="form-label">Expiry</label><input class="form-input" placeholder="MM/YY" maxlength="5"/></div>
            <div class="form-group"><label class="form-label">CVV</label><input class="form-input" placeholder="..." type="password" maxlength="3"/></div>
          </div>
          <button class="btn btn-primary" style="width:100%;justify-content:center;font-size:1rem;padding:1rem;" onclick="completePurchase()">Pay Securely Now</button>
        </div>
      </div>
      <div>
        <div class="order-box">
          <h3>Your Order</h3>
          <div id="pay-order-items"></div>
          <div style="margin-top:1rem;padding-top:1rem;border-top:2px solid var(--green-pale);">
            <div class="summary-row"><span>Subtotal</span><span id="pay-sub">₦0</span></div>
            <div class="summary-row"><span>Delivery</span><span>₦500</span></div>
            <div class="summary-total"><span>Total</span><span class="total-price" id="pay-total">₦0</span></div>
          </div>
          <div style="margin-top:1rem;padding:0.75rem;background:var(--green-pale);border-radius:var(--radius-sm);font-size:0.8rem;color:var(--text-mid);">Secured with 256-bit SSL encryption</div>
        </div>
      </div>
    </div>
  </div>
</div>

<!-- ======== SUCCESS ======== -->
<div class="page" id="page-success">
  <div class="success-page">
    <div class="success-card">
      <div class="success-icon">&#10003;</div>
      <h2>Order Confirmed!</h2>
      <p>Thank you — your order has been placed successfully.</p>
      <div class="order-id-tag" id="order-id">#AGM-000000</div>
      <p style="font-size:0.85rem;">Your farmer will pack your fresh produce and deliver within <strong>24 hours</strong>.</p>
      <div style="margin-top:2rem;"><button class="btn btn-green" onclick="showPage('marketplace')">Continue Shopping</button></div>
    </div>
  </div>
</div>

<!-- ======== REPORT PAGE ======== -->
<div class="page" id="page-report">
  <div class="back-bar"><button onclick="closeFarmerProfileAndGoBack()">← Back to Marketplace</button></div>
  <div class="report-page">
    <div class="report-header">
      <h2>Report a Farmer</h2>
      <p>Help us keep the marketplace safe and trustworthy for everyone.</p>
    </div>
    <div class="report-body">
      <div class="report-farmer-card" id="report-farmer-card">
        <div class="report-farmer-av" id="report-farmer-av"><span id="report-farmer-av-letter">F</span></div>
        <div>
          <div class="report-farmer-name" id="report-farmer-name">Farmer Name</div>
          <div class="report-farmer-loc" id="report-farmer-loc">Location</div>
        </div>
      </div>
      <div class="report-card">
        <h3>What are you reporting?</h3>
        <div class="report-categories">
          <button class="report-cat-btn" onclick="selectReportCat(this)">Fake / Misleading Listing</button>
          <button class="report-cat-btn" onclick="selectReportCat(this)">Overcharging / Scam</button>
          <button class="report-cat-btn" onclick="selectReportCat(this)">Spoiled / Unsafe Food</button>
          <button class="report-cat-btn" onclick="selectReportCat(this)">Did Not Deliver Order</button>
          <button class="report-cat-btn" onclick="selectReportCat(this)">Rude / Harassment</button>
          <button class="report-cat-btn" onclick="selectReportCat(this)">Other Issue</button>
        </div>
      </div>
      <div class="report-card">
        <h3>Describe what happened</h3>
        <div class="form-group" style="margin-bottom:1rem;">
          <label class="report-form-label">Order Reference (optional)</label>
          <input class="report-form-input" id="report-order-ref" placeholder="e.g. #AGM-123456"/>
        </div>
        <div class="form-group" style="margin-bottom:0;">
          <label class="report-form-label">Full Description *</label>
          <textarea class="report-form-input" id="report-desc" placeholder="Please describe the issue in detail. The more information you provide, the faster we can investigate..."></textarea>
        </div>
      </div>
      <button class="report-submit-btn" onclick="submitReport()">Submit Report</button>
      <p style="text-align:center;font-size:0.78rem;color:var(--text-light);margin-top:1rem;">Reports are reviewed within 24–48 hours. False reports may affect your account.</p>
    </div>
  </div>
</div>


<!-- ======== STUDENT PROFILE ======== -->
<div class="page" id="page-student-profile">
  <div class="back-bar"><button onclick="showPage('marketplace')">Back to Marketplace</button></div>
  <div class="stu-page">
    <div class="stu-hero">
      <div class="stu-hero-inner">
        <div class="stu-avatar-wrap">
          <div class="stu-avatar-circle" id="stu-avatar-circle">
            <span id="stu-avatar-letter">S</span>
          </div>
          <label class="stu-avatar-edit" for="stu-avatar-input" title="Change photo">
            <svg viewBox="0 0 24 24"><path d="M23 19a2 2 0 0 1-2 2H3a2 2 0 0 1-2-2V8a2 2 0 0 1 2-2h4l2-3h6l2 3h4a2 2 0 0 1 2 2z"/><circle cx="12" cy="13" r="4"/></svg>
          </label>
          <input type="file" id="stu-avatar-input" class="stu-avatar-input" accept="image/*" onchange="handleStudentPhoto(this)"/>
        </div>
        <div class="stu-hero-info">
          <h2 id="stu-hero-name">Student Name</h2>
          <p id="stu-hero-email">email@example.com</p>
          <div class="stu-badge">FUTO Student</div>
        </div>
      </div>
    </div>

    <div class="stu-body">
      <div class="stu-stats-row">
        <div class="stu-stat"><div class="stu-stat-val" id="stu-stat-orders">0</div><div class="stu-stat-lbl">Orders</div></div>
        <div class="stu-stat"><div class="stu-stat-val" id="stu-stat-spent">₦0</div><div class="stu-stat-lbl">Total Spent</div></div>
        <div class="stu-stat"><div class="stu-stat-val">4.9</div><div class="stu-stat-lbl">Trust Score</div></div>
      </div>

      <!-- Personal Info -->
      <div class="stu-section-card">
        <div class="stu-section-title">
          Personal Information
          <button class="stu-edit-toggle" onclick="toggleStuEdit('info')">Edit</button>
        </div>
        <!-- View mode -->
        <div id="stu-info-view">
          <div class="stu-info-row"><span class="stu-info-label">Full Name</span><span class="stu-info-value" id="stu-view-name">—</span></div>
          <div class="stu-info-row"><span class="stu-info-label">Email</span><span class="stu-info-value" id="stu-view-email">—</span></div>
          <div class="stu-info-row"><span class="stu-info-label">Phone</span><span class="stu-info-value" id="stu-view-phone">Not set</span></div>
          <div class="stu-info-row"><span class="stu-info-label">Department</span><span class="stu-info-value" id="stu-view-dept">Not set</span></div>
          <div class="stu-info-row"><span class="stu-info-label">Matric Number</span><span class="stu-info-value" id="stu-view-matric">Not set</span></div>
          <div class="stu-info-row"><span class="stu-info-label">Level</span><span class="stu-info-value" id="stu-view-level">Not set</span></div>
        </div>
        <!-- Edit mode -->
        <div id="stu-info-edit" style="display:none;">
          <div class="stu-form-grid">
            <div class="stu-form-group">
              <label class="stu-form-label">Full Name</label>
              <input class="stu-form-input" id="stu-edit-name" placeholder="Your full name"/>
            </div>
            <div class="stu-form-group">
              <label class="stu-form-label">Phone Number</label>
              <input class="stu-form-input" id="stu-edit-phone" placeholder="+234 800 000 0000"/>
            </div>
            <div class="stu-form-group">
              <label class="stu-form-label">Department</label>
              <input class="stu-form-input" id="stu-edit-dept" placeholder="e.g. Computer Science"/>
            </div>
            <div class="stu-form-group">
              <label class="stu-form-label">Matric Number</label>
              <input class="stu-form-input" id="stu-edit-matric" placeholder="e.g. 2021/1234567"/>
            </div>
            <div class="stu-form-group">
              <label class="stu-form-label">Level</label>
              <select class="stu-form-input" id="stu-edit-level">
                <option value="">Select level</option>
                <option>100 Level</option><option>200 Level</option><option>300 Level</option>
                <option>400 Level</option><option>500 Level</option>
              </select>
            </div>
          </div>
          <button class="stu-save-btn" onclick="saveStudentProfile()">Save Changes</button>
        </div>
      </div>

      <!-- Delivery Address -->
      <div class="stu-section-card">
        <div class="stu-section-title">
          Delivery Address
          <button class="stu-edit-toggle" onclick="toggleStuEdit('address')">Edit</button>
        </div>
        <div id="stu-address-view">
          <div class="stu-info-row"><span class="stu-info-label">Hostel / Block</span><span class="stu-info-value" id="stu-view-hostel">Not set</span></div>
          <div class="stu-info-row"><span class="stu-info-label">Room Number</span><span class="stu-info-value" id="stu-view-room">Not set</span></div>
          <div class="stu-info-row"><span class="stu-info-label">Delivery Notes</span><span class="stu-info-value" id="stu-view-notes">None</span></div>
        </div>
        <div id="stu-address-edit" style="display:none;">
          <div class="stu-form-grid">
            <div class="stu-form-group">
              <label class="stu-form-label">Hostel / Block</label>
              <input class="stu-form-input" id="stu-edit-hostel" placeholder="e.g. Alvan Ikoku Hall, Block B"/>
            </div>
            <div class="stu-form-group">
              <label class="stu-form-label">Room Number</label>
              <input class="stu-form-input" id="stu-edit-room" placeholder="e.g. Room 14"/>
            </div>
            <div class="stu-form-group" style="grid-column:1/-1;">
              <label class="stu-form-label">Delivery Notes</label>
              <input class="stu-form-input" id="stu-edit-notes" placeholder="Any special delivery instructions..."/>
            </div>
          </div>
          <button class="stu-save-btn" onclick="saveStudentAddress()">Save Address</button>
        </div>
      </div>

      <!-- Account Security -->
      <div class="stu-section-card">
        <div class="stu-section-title">Account &amp; Security</div>
        <div class="stu-info-row"><span class="stu-info-label">Password</span><span class="stu-info-value">••••••••</span></div>
        <div class="stu-info-row"><span class="stu-info-label">Account Type</span><span class="stu-info-value">Student</span></div>
        <div class="stu-info-row"><span class="stu-info-label">Member Since</span><span class="stu-info-value">2024</span></div>
        <div style="margin-top:1.25rem;">
          <div class="stu-danger-zone">
            <div class="stu-danger-text">
              <h4>Sign Out</h4>
              <p>You will be returned to the home page.</p>
            </div>
            <button class="stu-danger-btn" onclick="logout()">Sign Out</button>
          </div>
        </div>
      </div>
    </div>
  </div>
</div>

<!-- ======== FARMER DASHBOARD ======== -->
<div class="page" id="page-farmer-dashboard">
  <nav class="farm-navbar">
    <div class="farm-brand" onclick="switchSection('overview')">
      <img src="https://tse3.mm.bing.net/th/id/OIP.l0Yc4nXvTNf_2YV89vgP_QAAAA?cb=defcache2&defcache=1&rs=1&pid=ImgDetMain&o=7&rm=3" alt="FUTO"/>
      <span class="farm-brand-text">FUTO Agri-Market</span>
    </div>
    <div class="farm-nav-links">
      <button class="farm-nav-btn active" id="fn-overview" onclick="switchSection('overview')">Overview</button>
      <button class="farm-nav-btn" id="fn-orders" onclick="switchSection('orders')">Orders</button>
      <button class="farm-nav-btn" id="fn-listings" onclick="switchSection('listings')">My Listings</button>
      <button class="farm-nav-btn" id="fn-profile" onclick="switchSection('profile')">Profile</button>
    </div>
    <div class="farm-nav-right">
      <div class="farm-user-pill">
        <div class="farm-user-av" id="farm-avatar-top"><span id="farm-avatar-top-letter">F</span></div>
        <span class="farm-user-name" id="farm-name-top">Farmer</span>
      </div>
      <button class="farm-signout" onclick="logout()">Sign Out</button>
    </div>
  </nav>
  <div class="farm-layout">
    <aside class="farm-sidebar">
      <div class="farm-sb-label">Main</div>
      <button class="farm-sb-btn active" id="fsb-overview" onclick="switchSection('overview')">Overview</button>
      <button class="farm-sb-btn" id="fsb-orders" onclick="switchSection('orders')">Orders</button>
      <button class="farm-sb-btn" id="fsb-listings" onclick="switchSection('listings')">My Listings</button>
      <button class="farm-sb-btn" id="fsb-profile" onclick="switchSection('profile')">My Profile</button>
      <div class="farm-sb-label">Manage</div>
      <button class="farm-sb-btn" onclick="openAddModal()">Add New Crop</button>
      <button class="farm-sb-btn farm-sb-signout" onclick="logout()" style="margin-top:auto;">Sign Out</button>
    </aside>
    <main class="farm-main">

      <!-- ORDERS -->
      <div class="farm-section" id="farm-section-orders">
        <div class="farm-page-title">Orders</div>
        <div class="farm-page-sub">Students who have ordered from your farm.</div>
        <div class="farm-orders-hdr">
          <div class="farm-order-filter">
            <button class="farm-order-filter-btn active" onclick="filterOrders('all',this)">All</button>
            <button class="farm-order-filter-btn" onclick="filterOrders('pending',this)">Pending</button>
            <button class="farm-order-filter-btn" onclick="filterOrders('delivered',this)">Delivered</button>
          </div>
          <span id="orders-count" style="font-size:0.78rem;color:var(--farm-muted);">0 orders</span>
        </div>
        <div class="farm-orders-table">
          <div class="farm-orders-thead">
            <div class="farm-orders-th">Student</div>
            <div class="farm-orders-th">Order ID</div>
            <div class="farm-orders-th">Items</div>
            <div class="farm-orders-th">Amount</div>
            <div class="farm-orders-th">Status</div>
            <div class="farm-orders-th"></div>
          </div>
          <div id="farm-orders-list"></div>
        </div>
        <div id="farm-no-orders" style="display:none;" class="farm-no-orders">
          <div class="farm-no-orders-title">No orders yet</div>
          <div style="font-size:0.85rem;">When students buy your crops, their orders will appear here.</div>
        </div>
      </div>

      <!-- OVERVIEW -->
      <div class="farm-section active" id="farm-section-overview">
        <div class="farm-page-title" id="farm-greeting">Good day</div>
        <div class="farm-page-sub" id="farm-sub">Your farm performance at a glance.</div>
        <div class="farm-stats-row">
          <div class="farm-stat-card"><div class="farm-stat-lbl">Active Listings</div><div class="farm-stat-val" id="stat-active">0</div><div class="farm-stat-ch">Updated now</div></div>
          <div class="farm-stat-card"><div class="farm-stat-lbl">Pending Orders</div><div class="farm-stat-val" id="stat-pending">0</div><div class="farm-stat-ch" id="stat-pending-sub">Loading...</div></div>
          <div class="farm-stat-card"><div class="farm-stat-lbl">This Month</div><div class="farm-stat-val">₦87k</div><div class="farm-stat-ch">+12% vs last month</div></div>
          <div class="farm-stat-card"><div class="farm-stat-lbl">Avg Rating</div><div class="farm-stat-val">4.8</div><div class="farm-stat-ch">From 47 reviews</div></div>
        </div>
        <div class="farm-grid2">
          <div class="farm-card">
            <div class="farm-card-title">Quick Actions <a onclick="openAddModal()">+ Add Listing</a></div>
            <div class="farm-actions-grid">
              <div class="farm-action-tile" onclick="openAddModal()"><div class="farm-action-lbl">Post New Crop</div><div class="farm-action-sub">Upload and list produce</div></div>
              <div class="farm-action-tile" onclick="switchSection('listings')"><div class="farm-action-lbl">Manage Listings</div><div class="farm-action-sub">Edit or remove crops</div></div>
              <div class="farm-action-tile" onclick="switchSection('profile')"><div class="farm-action-lbl">Update Profile</div><div class="farm-action-sub">Farm info and contact</div></div>
              <div class="farm-action-tile"><div class="farm-action-lbl">View Analytics</div><div class="farm-action-sub">Sales performance</div></div>
            </div>
          </div>
          <div class="farm-card">
            <div class="farm-card-title">Recent Sales</div>
            <div class="farm-sale-item"><div class="farm-sale-img"><img src="https://img.freepik.com/premium-photo/fresh-organic-tomatoes_66869-583.jpg" alt="Tomatoes"/></div><div class="farm-sale-info"><div class="farm-sale-name">Fresh Tomatoes</div><div class="farm-sale-meta">Chukwuemeka O. · 2 baskets</div></div><div class="farm-sale-amount">₦1,600</div></div>
            <div class="farm-sale-item"><div class="farm-sale-img"><img src="https://images.squarespace-cdn.com/content/v1/6064cb7418b622722c221663/1630006723933-WBP0378C5FI50IE3UUGR/corn2.jpeg" alt="Corn"/></div><div class="farm-sale-info"><div class="farm-sale-name">Yellow Corn</div><div class="farm-sale-meta">Amaka N. · 5 cobs</div></div><div class="farm-sale-amount">₦1,250</div></div>
            <div class="farm-sale-item"><div class="farm-sale-img"><img src="https://tse3.mm.bing.net/th/id/OIP.WMffkCx-wDzf7Nikuja36QHaFj?cb=defcache2&defcache=1&rs=1&pid=ImgDetMain&o=7&rm=3" alt="Ugu"/></div><div class="farm-sale-info"><div class="farm-sale-name">Ugu Leaves</div><div class="farm-sale-meta">Bola A. · 3 bunches</div></div><div class="farm-sale-amount">₦600</div></div>
          </div>
        </div>
      </div>

      <!-- LISTINGS -->
      <div class="farm-section" id="farm-section-listings">
        <div class="farm-page-title">My Listings</div>
        <div class="farm-page-sub">All your active crop listings. Edit or delete anytime.</div>
        <div class="farm-listings-hdr">
          <input class="farm-search-input" placeholder="Search listings..." id="farm-search" oninput="renderDashListings()"/>
          <button class="farm-add-btn" onclick="openAddModal()">+ Add New Crop</button>
        </div>
        <div class="farm-listings-grid" id="dash-listings-grid"></div>
        <div id="no-listings" style="display:none;text-align:center;padding:4rem 2rem;color:var(--farm-muted);">
          <div style="font-size:1rem;margin-bottom:0.5rem;font-weight:600;">No listings yet</div>
          <button class="farm-add-btn" onclick="openAddModal()">Post Your First Crop</button>
        </div>
      </div>

      <!-- PROFILE -->
      <div class="farm-section" id="farm-section-profile">
        <div class="farm-page-title">My Profile</div>
        <div class="farm-page-sub">Your farm information visible to buyers on the marketplace.</div>
        <div class="farm-profile-banner">
          <div class="profile-photo-wrap">
            <div class="profile-photo-circle" id="prof-photo-circle">
              <span id="prof-avatar-letter">F</span>
            </div>
            <label class="profile-photo-upload-btn" for="prof-photo-input" title="Upload profile photo">
              <svg viewBox="0 0 24 24"><path d="M23 19a2 2 0 0 1-2 2H3a2 2 0 0 1-2-2V8a2 2 0 0 1 2-2h4l2-3h6l2 3h4a2 2 0 0 1 2 2z"/><circle cx="12" cy="13" r="4"/></svg>
            </label>
            <input type="file" id="prof-photo-input" class="profile-photo-input" accept="image/*" onchange="handleProfilePhoto(this)"/>
          </div>
          <div class="farm-profile-info">
            <h2 id="prof-name">Farmer Name</h2>
            <p id="prof-email">farmer@example.com</p>
            <div class="farm-profile-badge">Verified Farmer</div>
          </div>
        </div>
        <div class="farm-info-grid">
          <div class="farm-info-card">
            <h4>Farm Details</h4>
            <div class="farm-info-row"><span class="farm-info-label">Farm Name</span><span class="farm-info-value" id="pf-farmname">—</span></div>
            <div class="farm-info-row"><span class="farm-info-label">Location</span><span class="farm-info-value" id="pf-location">Ihiagwa, Owerri</span></div>
            <div class="farm-info-row"><span class="farm-info-label">Phone</span><span class="farm-info-value" id="pf-phone">—</span></div>
            <div class="farm-info-row"><span class="farm-info-label">Bio</span><span class="farm-info-value" id="pf-bio" style="font-weight:400;font-size:0.82rem;color:var(--farm-muted);">Not set</span></div>
            <div class="farm-info-row"><span class="farm-info-label">Member Since</span><span class="farm-info-value">2024</span></div>
          </div>
          <div class="farm-info-card">
            <h4>Statistics</h4>
            <div class="farm-info-row"><span class="farm-info-label">Total Listings</span><span class="farm-info-value" id="pf-listings">0</span></div>
            <div class="farm-info-row"><span class="farm-info-label">Total Sales</span><span class="farm-info-value">187</span></div>
            <div class="farm-info-row"><span class="farm-info-label">Avg Rating</span><span class="farm-info-value">4.8 / 5</span></div>
            <div class="farm-info-row"><span class="farm-info-label">Revenue (All Time)</span><span class="farm-info-value">₦342,000</span></div>
          </div>
        </div>
        <div class="farm-card" style="margin-top:1rem;">
          <div class="farm-card-title">Update Profile</div>
          <div class="farm-form-row" style="margin-bottom:0.75rem;">
            <div class="farm-form-group"><label class="farm-form-label">Farm Name</label><input class="farm-form-input" id="pf-edit-name" placeholder="e.g. Okafor Fresh Farms"/></div>
            <div class="farm-form-group"><label class="farm-form-label">Location</label><input class="farm-form-input" id="pf-edit-loc" placeholder="e.g. Ihiagwa, Owerri"/></div>
          </div>
          <div class="farm-form-row" style="margin-bottom:0.75rem;">
            <div class="farm-form-group"><label class="farm-form-label">Phone</label><input class="farm-form-input" id="pf-edit-phone" placeholder="+234 812 345 6789"/></div>
            <div class="farm-form-group"><label class="farm-form-label">Speciality (crops you grow)</label><input class="farm-form-input" id="pf-edit-specialty" placeholder="e.g. Tomatoes, Yam, Peppers"/></div>
          </div>
          <div class="farm-form-group" style="margin-bottom:1rem;"><label class="farm-form-label">Bio / Description</label><textarea class="farm-form-input" id="pf-edit-bio" placeholder="Tell buyers about your farm, your farming practices, and what makes your produce special..."></textarea></div>
          <button class="modal-submit" onclick="saveProfile()">Save Profile Changes</button>
        </div>
      </div>

    </main>
  </div>
</div>

<!-- ======== ADD/EDIT LISTING MODAL ======== -->
<div class="modal-overlay" id="listing-modal">
  <div class="modal">
    <div class="modal-header">
      <h3 id="modal-title">Add New Listing</h3>
      <button class="modal-close" onclick="closeModal('listing-modal')">&#215;</button>
    </div>
    <div class="modal-body">
      <input type="hidden" id="edit-id"/>
      <div class="farm-form-group">
        <label class="farm-form-label">Crop Photo</label>
        <div class="upload-zone" onclick="document.getElementById('photo-input').click()" id="upload-zone">
          <img class="upload-preview" id="upload-preview" src="" alt=""/>
          <div id="upload-ph"><div class="upload-plus">+</div><div class="upload-hint">Click to upload — <strong>JPG, PNG or WebP</strong>, max 5MB</div></div>
        </div>
        <input type="file" id="photo-input" accept="image/*" onchange="handlePhoto(this)"/>
      </div>
      <div class="farm-form-group"><label class="farm-form-label">Crop Name *</label><input class="farm-form-input" id="m-name" placeholder="e.g. Fresh Tomatoes"/></div>
      <div class="farm-form-group"><label class="farm-form-label">Description</label><textarea class="farm-form-input" id="m-desc" placeholder="Harvested fresh this morning, pesticide-free..."></textarea></div>
      <div class="farm-form-row">
        <div class="farm-form-group"><label class="farm-form-label">Price (₦) *</label><input class="farm-form-input" type="number" id="m-price" placeholder="800"/></div>
        <div class="farm-form-group"><label class="farm-form-label">Unit</label>
          <select class="farm-form-input" id="m-unit"><option>per kg</option><option>per basket</option><option>per bunch</option><option>per piece</option><option>per bag</option><option>per crate</option></select>
        </div>
      </div>
      <div class="farm-form-row">
        <div class="farm-form-group"><label class="farm-form-label">Quantity</label><input class="farm-form-input" type="number" id="m-qty" placeholder="50"/></div>
        <div class="farm-form-group"><label class="farm-form-label">Category</label>
          <select class="farm-form-input" id="m-cat"><option value="veg">Vegetables</option><option value="fruit">Fruits</option><option value="grain">Grains and Tubers</option><option value="leaf">Leafy Greens</option></select>
        </div>
      </div>
    </div>
    <div class="modal-footer">
      <button class="modal-cancel" onclick="closeModal('listing-modal')">Cancel</button>
      <button class="modal-submit" onclick="saveListing()">Save Listing</button>
    </div>
  </div>
</div>

<!-- DELETE MODAL -->
<div class="modal-overlay" id="delete-modal">
  <div class="modal" style="max-width:400px;">
    <div class="modal-body" style="padding:2.5rem 2rem;text-align:center;">
      <div style="font-size:1.25rem;font-weight:700;color:#e05c4a;margin-bottom:0.75rem;">Delete Listing</div>
      <p style="color:var(--farm-muted);font-size:0.9rem;margin-bottom:2rem;">This will permanently remove this crop from the marketplace.</p>
      <div style="display:flex;gap:0.75rem;justify-content:center;">
        <button class="modal-cancel" onclick="closeModal('delete-modal')">Cancel</button>
        <button class="modal-del-confirm" onclick="confirmDelete()">Yes, Delete</button>
      </div>
    </div>
  </div>
</div>

<!-- ======== FARMER PROFILE MODAL (student side) ======== -->
<!-- Floating report button shown when profile modal is open -->
<button class="fp-floating-report" id="fp-floating-report" onclick="openReportFromProfile()" title="Report this Farmer">
  <svg viewBox="0 0 24 24"><circle cx="12" cy="12" r="10"/><line x1="12" y1="8" x2="12" y2="12" stroke-linecap="round"/><circle cx="12" cy="16" r="0.5" fill="white"/></svg>
</button>

<div class="fp-modal-overlay" id="fp-modal">
  <div class="fp-modal">
    <div class="fp-modal-hero">
      <button class="fp-modal-close" onclick="closeFpModal()">&#215;</button>
      <div class="fp-modal-avatar-wrap">
        <div class="fp-modal-avatar" id="fp-avatar">
          <span id="fp-avatar-letter">F</span>
        </div>
        <div class="fp-verified-badge" style="font-size:0.6rem;font-weight:800;">V</div>
      </div>
    </div>
    <div class="fp-modal-body">
      <div class="fp-name" id="fp-name">Farmer Name</div>
      <div class="fp-title" id="fp-title">Local Farmer · Ihiagwa</div>
      <div class="fp-stats-row">
        <div class="fp-stat"><div class="fp-stat-val" id="fp-stat-listings">0</div><div class="fp-stat-lbl">Listings</div></div>
        <div class="fp-stat"><div class="fp-stat-val" id="fp-stat-rating">4.8★</div><div class="fp-stat-lbl">Rating</div></div>
        <div class="fp-stat"><div class="fp-stat-val" id="fp-stat-sales">—</div><div class="fp-stat-lbl">Sales</div></div>
      </div>
      <div class="fp-info-section">
        <div class="fp-info-label">Farm Details</div>
        <div class="fp-info-items">
          <div class="fp-info-item"><div class="fp-info-icon">Location</div><span id="fp-location-text">Location not set</span></div>
          <div class="fp-info-item"><div class="fp-info-icon">Phone</div><span id="fp-phone-text">Phone not provided</span></div>
          <div class="fp-info-item"><div class="fp-info-icon">Farm</div><span id="fp-farmname-text">Farm name not set</span></div>
        </div>
      </div>
      <div class="fp-info-section" id="fp-bio-section">
        <div class="fp-info-label">About this Farm</div>
        <p id="fp-bio-text" style="font-size:0.88rem;color:var(--text-mid);line-height:1.65;"></p>
      </div>
      <div class="fp-info-section" id="fp-crops-section">
        <div class="fp-info-label">Available Crops</div>
        <div id="fp-crops-list"></div>
      </div>
      <div class="fp-actions">
        <button class="fp-close-btn" onclick="closeFpModal()">Close Profile</button>
      </div>
    </div>
  </div>
</div>

<script>
// ===== STATE =====
var currentUser = null;
var loginRole = 'student';
var regRole = 'student';
var cart = [];
var currentFilter = 'all';
var pendingDeleteId = null;
var photoDataURL = null;
var currentFarmerForReport = null; // tracks which farmer is being reported

// farmerProfiles stores per-farmerName profile data (including photo, bio etc)
// keyed by farmer display name
var farmerProfiles = {};

var farmerProfile = { farmName:'', location:'Ihiagwa, Owerri', phone:'', bio:'', specialty:'', photo: null };

var products = [
  { id:1, name:'Fresh Tomatoes', image:'https://img.freepik.com/premium-photo/fresh-organic-tomatoes_66869-583.jpg', price:800, unit:'per basket', farmer:'Musa Okafor', location:'Ihiagwa', stars:5, category:'veg', badge:'Fresh Today', fid:null },
  { id:2, name:'Sweet Pineapples', image:'https://tse1.mm.bing.net/th/id/OIP.LFTllfCXBmxXIyVmTjaZ0QHaE7?cb=defcache2&defcache=1&rs=1&pid=ImgDetMain&o=7&rm=3', price:500, unit:'each', farmer:'Ada Nwosu', location:'Obinze', stars:4, category:'fruit', badge:'Popular', fid:null },
  { id:3, name:'Green Peppers', image:'https://img.freepik.com/premium-photo/capsicum-green-bell-pepper_974629-18950.jpg', price:600, unit:'per kg', farmer:'Emeka Eze', location:'Eziobodo', stars:5, category:'veg', badge:'Fresh Today', fid:null },
  { id:4, name:'Garden Eggs', image:'https://9jafoods.com/wp-content/uploads/2018/09/Garden-egg-2.jpg', price:300, unit:'per cup', farmer:'Ngozi Uche', location:'Ihiagwa', stars:4, category:'veg', badge:'', fid:null },
  { id:5, name:'Plantains', image:'https://thumbs.dreamstime.com/b/green-bananas-fresh-raw-asian-big-collected-to-transport-south-asia-194040741.jpg', price:1200, unit:'per bunch', farmer:'Chidi Obi', location:'Obinze', stars:5, category:'fruit', badge:'Best Seller', fid:null },
  { id:6, name:'Ugu Leaves', image:'https://tse3.mm.bing.net/th/id/OIP.WMffkCx-wDzf7Nikuja36QHaFj?cb=defcache2&defcache=1&rs=1&pid=ImgDetMain&o=7&rm=3', price:200, unit:'per bunch', farmer:'Musa Okafor', location:'Ihiagwa', stars:4, category:'leaf', badge:'', fid:null },
  { id:7, name:'Yellow Corn', image:'https://images.squarespace-cdn.com/content/v1/6064cb7418b622722c221663/1630006723933-WBP0378C5FI50IE3UUGR/corn2.jpeg', price:250, unit:'per cob', farmer:'Ada Nwosu', location:'Eziobodo', stars:5, category:'grain', badge:'Seasonal', fid:null },
  { id:8, name:'Fresh Okra', image:'https://media.gettyimages.com/id/72664829/photo/basket-of-okra-at-market-stall.jpg?s=612x612&w=gi&k=20&c=0VjDQ55Jnr77u8S7ftpZP4ZB_atQo8-yTlXt3emK7vU=', price:400, unit:'per kg', farmer:'Emeka Eze', location:'Ihiagwa', stars:4, category:'veg', badge:'', fid:null },
  { id:9, name:'Yam', image:'https://nigerianfinder.com/wp-content/uploads/2020/03/How-to-Preserve-Yam-in-Nigeria.jpg', price:800, unit:'per tuber', farmer:'Chidi Obi', location:'Eziobodo', stars:5, category:'grain', badge:'Farm Fresh', fid:null },
  { id:10, name:'Groundnut', image:'https://tse1.explicit.bing.net/th/id/OIP._pxhb-2zRYr0dO2yFnqwEgHaHa?cb=defcache2&defcache=1&w=500&h=500&rs=1&pid=ImgDetMain&o=7&rm=3', price:200, unit:'per cup', farmer:'Ada Nwosu', location:'Obinze', stars:4, category:'grain', badge:'', fid:null },
  { id:11, name:'Banana', image:'https://th.bing.com/th/id/OIP.UVy2b85VJffWYhf50Wzz-AHaFN?o=7&cb=defcache2&rm=3&defcache=1&rs=1&pid=ImgDetMain&o=7&rm=3', price:500, unit:'per bunch', farmer:'Musa Okafor', location:'Ihiagwa', stars:4, category:'fruit', badge:'', fid:null }
];

// Seed demo profiles for default farmers
farmerProfiles['Musa Okafor'] = { farmName:"Okafor's Green Farm", location:'Ihiagwa, near FUTO Gate', phone:'+234 803 111 2222', bio:'We have been farming in Ihiagwa for over 15 years. All our produce is grown without harmful pesticides. We supply to many FUTO staff and students weekly.', specialty:'Tomatoes, Ugu Leaves, Bananas', photo: null };
farmerProfiles['Ada Nwosu'] = { farmName:"Ada's Fresh Harvest", location:'Obinze, Owerri West', phone:'+234 805 333 4444', bio:'Family-run farm specializing in sweet pineapples and local grains. Visit us at the Obinze farm gate any morning.', specialty:'Pineapples, Corn, Groundnut', photo: null };
farmerProfiles['Emeka Eze'] = { farmName:"Eze Organic Farms", location:'Eziobodo, near Nekede', phone:'+234 806 555 6666', bio:'Certified organic farm. All crops grown using natural fertilizer. Supplying FUTO community since 2019.', specialty:'Green Peppers, Okra', photo: null };
farmerProfiles['Ngozi Uche'] = { farmName:"Ngozi's Garden", location:'Ihiagwa, Owerri', phone:'+234 807 777 8888', bio:'Passionate about growing healthy vegetables for the campus community.', specialty:'Garden Eggs, Vegetables', photo: null };
farmerProfiles['Chidi Obi'] = { farmName:"Obi Farms Ltd", location:'Obinze / Eziobodo', phone:'+234 808 999 0000', bio:'Large-scale farm supplying plantains, yam and other tubers. Bulk orders welcome.', specialty:'Plantains, Yam', photo: null };

// ===== PAGE NAVIGATION =====
function showPage(p) {
  if (p === 'home' && currentUser) return;
  document.querySelectorAll('.page').forEach(function(el){ el.classList.remove('active'); });
  var t = document.getElementById('page-' + p);
  if (t) { t.classList.add('active'); window.scrollTo(0,0); }
  var navbar = document.getElementById('main-navbar');
  if (navbar) navbar.style.display = (p === 'farmer-dashboard') ? 'none' : '';
  if (p === 'home') renderFeatured();
  if (p === 'marketplace') renderMarket();
  if (p === 'cart') renderCart();
  if (p === 'payment') renderPaySummary();
  if (p === 'farmer-dashboard') { renderDashListings(); updateStats(); }
  if (p === 'student-profile') loadStudentProfilePage();
}

function switchSection(s) {
  document.querySelectorAll('.farm-section').forEach(function(el){ el.classList.remove('active'); });
  document.getElementById('farm-section-' + s).classList.add('active');
  document.querySelectorAll('.farm-nav-btn,.farm-sb-btn').forEach(function(el){ el.classList.remove('active'); });
  var fn = document.getElementById('fn-' + s);
  var fb = document.getElementById('fsb-' + s);
  if (fn) fn.classList.add('active');
  if (fb) fb.classList.add('active');
  if (s === 'listings') renderDashListings();
  if (s === 'profile') populateProfile();
  if (s === 'orders') renderOrders();
}

// ===== GET FARMER PROFILE (merged data) =====
function getFarmerData(name) {
  return farmerProfiles[name] || { farmName: name + "'s Farm", location: 'Owerri, Imo State', phone: 'Not provided', bio: '', specialty: '', photo: null };
}

// ===== PRODUCT CARD (student side) =====
function buildCard(p, loginRedirect) {
  var stars = '';
  for (var i=0;i<(p.stars||4);i++) stars += '&#9733;';
  for (var i=(p.stars||4);i<5;i++) stars += '&#9734;';
  var badgeHtml = p.badge ? '<div class="product-badge' + (p.badge==='Fresh Today'?' fresh':'') + '">' + p.badge + '</div>' : '';
  var imgHtml = p.image
    ? '<img src="' + p.image + '" alt="' + p.name + '" style="width:100%;height:100%;object-fit:cover;display:block;" onerror="this.parentNode.innerHTML=\'<div class=no-img-text>No image</div>\'">'
    : '<div class="no-img-text">No image</div>';

  // Farmer avatar (photo or initial)
  var fd = getFarmerData(p.farmer);
  var farmerAvatarHtml = fd.photo
    ? '<img src="' + fd.photo + '" alt="' + p.farmer + '" style="width:100%;height:100%;object-fit:cover;border-radius:50%;">'
    : '<span style="font-size:0.7rem;font-weight:700;color:white;">' + p.farmer.charAt(0).toUpperCase() + '</span>';

  var btnHtml;
  if (loginRedirect) {
    btnHtml = '<button class="btn btn-primary btn-sm" style="width:100%;justify-content:center;" onclick="showPage(\'login\')">Buy Now</button>';
  } else {
    btnHtml = '<div style="display:flex;gap:6px;align-items:center;">'
      + '<button class="btn btn-primary btn-sm" style="flex:1;justify-content:center;" onclick="addToCart(' + p.id + ')">Add to Cart</button>'
      + '<button onclick="openFarmerProfile(\'' + escStr(p.farmer) + '\')" style="width:36px;height:36px;min-width:36px;border-radius:50%;border:2px solid var(--green-light);background:linear-gradient(135deg,var(--green-fresh),var(--green-mid));display:flex;align-items:center;justify-content:center;cursor:pointer;transition:all .2s;overflow:hidden;" title="View ' + p.farmer + '\'s profile">'
      + farmerAvatarHtml
      + '</button>'
    + '</div>';
  }

  return '<div class="product-card" data-cat="' + p.category + '">'
    + '<div class="product-img">' + badgeHtml + imgHtml + '</div>'
    + '<div class="product-body">'
    + '<div class="product-farmer"><div class="farmer-dot"></div>' + p.farmer + ' &middot; ' + p.location + '</div>'
    + '<div class="product-name">' + p.name + '</div>'
    + '<div class="product-meta"><div><span class="product-price">&#8358;' + Number(p.price).toLocaleString() + '</span><br><span class="product-unit">' + p.unit + '</span></div><div class="product-stars">' + stars + '</div></div>'
    + '<div>' + btnHtml + '</div>'
    + '</div></div>';
}

function escStr(s) { return s.replace(/'/g, "\\'"); }

function renderFeatured() {
  var g = document.getElementById('featured-grid');
  if (!g) return;
  g.innerHTML = products.map(function(p){ return buildCard(p, true); }).join('');
}

function renderMarket(filter, search) {
  filter = filter || 'all'; search = (search||'').toLowerCase();
  var g = document.getElementById('market-grid');
  if (!g) return;
  var list = products;
  if (filter !== 'all') list = list.filter(function(p){ return p.category === filter; });
  if (search) list = list.filter(function(p){ return p.name.toLowerCase().includes(search) || p.farmer.toLowerCase().includes(search); });
  if (!list.length) { g.innerHTML = '<div style="grid-column:1/-1;text-align:center;padding:3rem;color:var(--text-light);">No products found</div>'; return; }
  g.innerHTML = list.map(function(p){ return buildCard(p, false); }).join('');
}

function filterHome(cat, btn) {
  document.querySelectorAll('#page-home .filter-btn').forEach(function(b){ b.classList.remove('active'); });
  btn.classList.add('active');
  var cards = document.getElementById('featured-grid').querySelectorAll('.product-card');
  cards.forEach(function(c){ c.style.display = (cat==='all' || c.dataset.cat===cat) ? '' : 'none'; });
}

function filterMarket(cat, btn) {
  document.querySelectorAll('#page-marketplace .filter-btn').forEach(function(b){ b.classList.remove('active'); });
  btn.classList.add('active');
  currentFilter = cat;
  renderMarket(cat, document.getElementById('search-input') ? document.getElementById('search-input').value : '');
}

function searchProducts() {
  var s = document.getElementById('search-input') ? document.getElementById('search-input').value : '';
  renderMarket(currentFilter, s);
}

// ===== FARMER PROFILE MODAL (student side) =====
function openFarmerProfile(name) {
  currentFarmerForReport = name;
  var fd = getFarmerData(name);
  var farmerProds = products.filter(function(p){ return p.farmer === name; });
  var avg = farmerProds.length ? (farmerProds.reduce(function(a,p){ return a+(p.stars||0); },0)/farmerProds.length).toFixed(1) : '—';

  // Avatar
  var avEl = document.getElementById('fp-avatar');
  var avLetter = document.getElementById('fp-avatar-letter');
  var oldImg = avEl.querySelector('img');
  if (oldImg) oldImg.remove();
  if (fd.photo) {
    avLetter.style.display = 'none';
    var img = document.createElement('img');
    img.src = fd.photo; img.alt = name;
    img.style.cssText = 'width:100%;height:100%;object-fit:cover;';
    avEl.appendChild(img);
  } else {
    if(oldImg) oldImg.remove();
    avLetter.style.display = '';
    avLetter.textContent = name.charAt(0).toUpperCase();
  }

  document.getElementById('fp-name').textContent = fd.farmName || name;
  document.getElementById('fp-title').textContent = name + ' · ' + (fd.location || 'Local Farmer');
  document.getElementById('fp-stat-listings').textContent = farmerProds.length;
  document.getElementById('fp-stat-rating').textContent = avg + '★';
  document.getElementById('fp-stat-sales').textContent = '100+';
  document.getElementById('fp-location-text').textContent = fd.location || 'Not specified';
  document.getElementById('fp-phone-text').textContent = fd.phone || 'Not provided';
  document.getElementById('fp-farmname-text').textContent = fd.farmName || name + "'s Farm";

  var bioEl = document.getElementById('fp-bio-text');
  var bioSection = document.getElementById('fp-bio-section');
  if (fd.bio) {
    bioEl.textContent = fd.bio;
    bioSection.style.display = '';
  } else {
    bioSection.style.display = 'none';
  }

  // Crops with Buy Now buttons
  var cropsList = document.getElementById('fp-crops-list');
  var cropsSection = document.getElementById('fp-crops-section');
  if (farmerProds.length) {
    cropsSection.style.display = '';
    cropsList.innerHTML = '<div class="fp-crop-cards">'
      + farmerProds.map(function(p){
          var imgHtml = p.image
            ? '<img src="' + p.image + '" alt="' + p.name + '" onerror="this.parentNode.innerHTML=\'<div class=fp-crop-img-placeholder>No image</div>\'">'
            : '<div class="fp-crop-img-placeholder">No image</div>';
          return '<div class="fp-crop-card">'
            + '<div class="fp-crop-img">' + imgHtml + '</div>'
            + '<div class="fp-crop-info">'
            + '<div class="fp-crop-name">' + p.name + '</div>'
            + '<div><span class="fp-crop-price">&#8358;' + Number(p.price).toLocaleString() + '</span> <span class="fp-crop-unit">' + p.unit + '</span></div>'
            + '</div>'
            + '<button class="fp-buy-btn" onclick="buyFromProfile(' + p.id + ')">Buy Now</button>'
            + '</div>';
        }).join('')
      + '</div>';
  } else {
    cropsSection.style.display = 'none';
  }

  document.getElementById('fp-modal').classList.add('open');
  document.getElementById('fp-floating-report').classList.add('show');
}

function buyFromProfile(id) {
  var p = products.find(function(x){ return x.id===id; });
  if (!p) return;
  addToCart(id);
  // small visual feedback on the button
}

function closeFpModal() {
  document.getElementById('fp-modal').classList.remove('open');
  document.getElementById('fp-floating-report').classList.remove('show');
}

function openReportFromProfile() {
  closeFpModal();
  openReportPage(currentFarmerForReport);
}

function closeFarmerProfileAndGoBack() {
  currentFarmerForReport = null;
  showPage('marketplace');
}

// ===== REPORT PAGE =====
function openReportPage(farmerName) {
  var fd = getFarmerData(farmerName);
  // Populate report farmer card
  var avLetter = document.getElementById('report-farmer-av-letter');
  var avEl = document.getElementById('report-farmer-av');
  var oldImg = avEl.querySelector('img');
  if (oldImg) oldImg.remove();
  if (fd.photo) {
    avLetter.style.display = 'none';
    var img = document.createElement('img');
    img.src = fd.photo; img.alt = farmerName;
    img.style.cssText = 'width:100%;height:100%;object-fit:cover;';
    avEl.appendChild(img);
  } else {
    avLetter.style.display = '';
    avLetter.textContent = farmerName.charAt(0).toUpperCase();
  }
  document.getElementById('report-farmer-name').textContent = fd.farmName || farmerName;
  document.getElementById('report-farmer-loc').textContent = farmerName + ' · ' + (fd.location || 'FUTO Area');
  // Clear form
  document.querySelectorAll('.report-cat-btn').forEach(function(b){ b.classList.remove('active'); });
  var desc = document.getElementById('report-desc'); if(desc) desc.value = '';
  var ref = document.getElementById('report-order-ref'); if(ref) ref.value = '';
  showPage('report');
}

function selectReportCat(btn) {
  document.querySelectorAll('.report-cat-btn').forEach(function(b){ b.classList.remove('active'); });
  btn.classList.add('active');
}

function submitReport() {
  var desc = document.getElementById('report-desc').value.trim();
  var cat = document.querySelector('.report-cat-btn.active');
  if (!cat) { toast('Please select a report category.'); return; }
  if (!desc) { toast('Please describe the issue.'); return; }
  toast('Report submitted. Our team will review within 24-48 hours.');
  setTimeout(function(){ showPage('marketplace'); }, 1500);
}

// ===== CART =====
function addToCart(id) {
  var p = products.find(function(x){ return x.id===id; });
  if (!p) return;
  var ex = cart.find(function(c){ return c.id===id; });
  if (ex) { ex.qty++; } else { cart.push(Object.assign({}, p, {qty:1})); }
  updateBadge();
  toast(p.name + ' added to cart.');
}

function updateBadge() {
  var total = cart.reduce(function(a,c){ return a+c.qty; }, 0);
  var b = document.getElementById('cart-badge');
  if (b) b.textContent = total;
}

function renderCart() {
  var list = document.getElementById('cart-items-list');
  var empty = document.getElementById('empty-cart');
  if (!list) return;
  if (!cart.length) { list.innerHTML=''; if(empty) empty.style.display='block'; updateTotals(); return; }
  if(empty) empty.style.display='none';
  list.innerHTML = cart.map(function(item, i){
    var imgHtml = item.image ? '<img src="' + item.image + '" alt="' + item.name + '" style="width:100%;height:100%;object-fit:cover;">' : '';
    return '<div class="cart-item">'
      + '<div class="cart-item-img">' + imgHtml + '</div>'
      + '<div class="cart-item-info"><div class="cart-item-name">' + item.name + '</div><div class="cart-item-farmer">' + item.farmer + ' &middot; ' + item.location + '</div><div class="cart-item-price">&#8358;' + Number(item.price).toLocaleString() + ' ' + item.unit + '</div></div>'
      + '<div class="qty-ctrl"><button class="qty-btn" onclick="changeQty(' + i + ',-1)">&#8722;</button><span class="qty-num">' + item.qty + '</span><button class="qty-btn" onclick="changeQty(' + i + ',1)">+</button></div>'
      + '<div style="font-family:\'Space Mono\',monospace;font-weight:700;color:var(--green-fresh);min-width:80px;text-align:right;">&#8358;' + (item.price*item.qty).toLocaleString() + '</div>'
      + '<button onclick="removeFromCart(' + i + ')" style="background:none;border:none;cursor:pointer;color:#e05c4a;font-size:1.2rem;padding:0 0.3rem;">&#215;</button>'
      + '</div>';
  }).join('');
  updateTotals();
}

function changeQty(i, d) { cart[i].qty+=d; if(cart[i].qty<=0) cart.splice(i,1); updateBadge(); renderCart(); }
function removeFromCart(i) { cart.splice(i,1); updateBadge(); renderCart(); }

function updateTotals() {
  var sub = cart.reduce(function(a,c){ return a + c.price*c.qty; }, 0);
  var s = document.getElementById('cart-subtotal'); if(s) s.textContent = '&#8358;' + sub.toLocaleString();
  var t = document.getElementById('cart-total'); if(t) t.textContent = (sub+500).toLocaleString();
}

function renderPaySummary() {
  var con = document.getElementById('pay-order-items');
  if(!con) return;
  var sub = cart.reduce(function(a,c){ return a+c.price*c.qty; }, 0);
  if (!cart.length) { con.innerHTML='<div style="color:var(--text-light);text-align:center;padding:1rem;">Cart is empty</div>'; }
  else {
    con.innerHTML = cart.map(function(c){
      var imgHtml = c.image ? '<img src="' + c.image + '" style="width:40px;height:40px;object-fit:cover;border-radius:6px;margin-right:8px;">' : '';
      return '<div class="order-item"><div style="display:flex;align-items:center;">' + imgHtml + c.name + ' x' + c.qty + '</div><span style="font-weight:600;">&#8358;' + (c.price*c.qty).toLocaleString() + '</span></div>';
    }).join('');
  }
  var ps = document.getElementById('pay-sub'); if(ps) ps.textContent = '&#8358;'+sub.toLocaleString();
  var pt = document.getElementById('pay-total'); if(pt) pt.textContent = (sub+500).toLocaleString();
}

// ===== AUTH =====
function setLoginRole(r) {
  loginRole = r;
  document.getElementById('ls-btn').classList.toggle('active', r==='student');
  document.getElementById('lf-btn').classList.toggle('active', r==='farmer');
}

function setRegRole(r) {
  regRole = r;
  document.getElementById('rs-btn').classList.toggle('active', r==='student');
  document.getElementById('rf-btn').classList.toggle('active', r==='farmer');
  document.getElementById('r-matric-grp').style.display = r==='student' ? '' : 'none';
  document.getElementById('r-farm-grp').style.display = r==='farmer' ? '' : 'none';
}

function doLogin() {
  var email = document.getElementById('l-email').value;
  var pass = document.getElementById('l-pass').value;
  if (!email || !pass) { toast('Please fill in all fields.'); return; }
  currentUser = { name: email.split('@')[0], email: email, role: loginRole, id: email + '-' + loginRole };
  if (loginRole==='farmer') {
    var fn2 = currentUser.name;
    if (!farmerProfiles[fn2]) {
      farmerProfiles[fn2] = { farmName: fn2 + "'s Farm", location:'Ihiagwa, Owerri', phone:'', bio:'', specialty:'', photo: null };
    }
    farmerProfile = farmerProfiles[fn2];
  }
  setupNavAfterLogin();
  toast('Welcome back, ' + currentUser.name + '!');
  if (loginRole==='farmer') showPage('farmer-dashboard');
  else showPage('marketplace');
}

function doRegister() {
  var fn = document.getElementById('r-fname').value.trim();
  var ln = document.getElementById('r-lname').value.trim();
  var email = document.getElementById('r-email').value.trim();
  var pass = document.getElementById('r-pass').value;
  var cpass = document.getElementById('r-cpass').value;
  if (!fn || !ln || !email || !pass) { toast('Please fill all required fields.'); return; }
  if (pass !== cpass) { toast('Passwords do not match.'); return; }
  currentUser = { name: fn + ' ' + ln, email: email, role: regRole, id: email + '-' + regRole };
  if (regRole==='farmer') {
    var loc = document.getElementById('r-farmloc').value;
    var profileKey = currentUser.name;
    farmerProfiles[profileKey] = { farmName: fn + "'s Farm", location: loc || 'Ihiagwa, Owerri', phone:'', bio:'', specialty:'', photo: null };
    farmerProfile = farmerProfiles[profileKey];
  }
  setupNavAfterLogin();
  toast('Account created! Welcome, ' + fn + '.');
  if (regRole==='farmer') showPage('farmer-dashboard');
  else showPage('marketplace');
}

function setupNavAfterLogin() {
  if (!currentUser) return;
  if (currentUser.role === 'student') {
    document.getElementById('nav-signin-btn').style.display = 'none';
    document.getElementById('nav-home-btn').style.display = 'none';
    document.getElementById('nav-about-btn').style.display = 'none';
    document.getElementById('nav-market-btn').style.display = '';
    document.getElementById('user-nav-info').style.display = 'flex';
    // Update nav avatar
    var avEl = document.getElementById('user-avatar');
    var avLetter = document.getElementById('user-avatar-letter');
    avLetter.textContent = currentUser.name.charAt(0).toUpperCase();
    document.getElementById('user-nav-name').textContent = currentUser.name;
    document.getElementById('floating-cart').classList.add('show');
    updateBadge();
    var brand = document.querySelector('.nav-brand');
    if (brand) { brand.onclick = function(){}; brand.style.cursor='default'; }
  } else {
    var brand2 = document.querySelector('.nav-brand');
    if (brand2) { brand2.onclick = function(){}; brand2.style.cursor='default'; }
    var avt = document.getElementById('farm-avatar-top');
    var avLt = document.getElementById('farm-avatar-top-letter');
    var nm = document.getElementById('farm-name-top');
    if (avLt) avLt.textContent = currentUser.name.charAt(0).toUpperCase();
    if (nm) nm.textContent = currentUser.name;
    var greet = document.getElementById('farm-greeting');
    if (greet) greet.textContent = 'Good day, ' + currentUser.name;
  }
}

function logout() {
  currentUser = null;
  cart = [];
  farmerProfile = { farmName:'', location:'Ihiagwa, Owerri', phone:'', bio:'', specialty:'', photo: null };
  document.getElementById('nav-signin-btn').style.display = '';
  document.getElementById('nav-home-btn').style.display = '';
  document.getElementById('nav-about-btn').style.display = '';
  document.getElementById('nav-market-btn').style.display = 'none';
  document.getElementById('user-nav-info').style.display = 'none';
  document.getElementById('floating-cart').classList.remove('show');
  document.getElementById('main-navbar').style.display = '';
  var brand = document.querySelector('.nav-brand');
  if (brand) { brand.onclick = function(){ showPage('home'); }; brand.style.cursor='pointer'; }
  showPage('home');
  toast('You have been signed out.');
}

function scrollToAbout() {
  showPage('home');
  setTimeout(function(){
    var s = document.getElementById('about-home');
    if (s) s.scrollIntoView({ behavior:'smooth', block:'center' });
  }, 120);
}

// ===== FARMER DASHBOARD =====
function updateStats() {
  if (!currentUser) return;
  var mine = products.filter(function(p){ return p.fid === currentUser.id; });
  var el = document.getElementById('stat-active'); if(el) el.textContent = mine.length;
  var pl = document.getElementById('pf-listings'); if(pl) pl.textContent = mine.length;
  // Update pending orders count in overview
  var myOrders = getMyOrders ? getMyOrders() : [];
  var pending = myOrders.filter(function(o){ return o.status === 'pending'; }).length;
  var pendingEl = document.getElementById('stat-pending'); if(pendingEl) pendingEl.textContent = pending;
}

function renderDashListings() {
  if (!currentUser) return;
  var grid = document.getElementById('dash-listings-grid');
  var none = document.getElementById('no-listings');
  var search = (document.getElementById('farm-search') ? document.getElementById('farm-search').value : '').toLowerCase();
  var mine = products.filter(function(p){ return p.fid === currentUser.id && (!search || p.name.toLowerCase().includes(search)); });
  if (!grid) return;
  if (!mine.length) { grid.innerHTML=''; if(none) none.style.display='block'; updateStats(); return; }
  if(none) none.style.display='none';
  grid.innerHTML = mine.map(function(p){
    var imgHtml = p.image
      ? '<img src="' + p.image + '" alt="' + p.name + '" style="width:100%;height:100%;object-fit:cover;">'
      : '<div class="no-img">No image</div>';
    return '<div class="farm-listing-card">'
      + '<div class="farm-listing-img">' + imgHtml + '<div class="farm-listing-status">Active</div></div>'
      + '<div class="farm-listing-body">'
      + '<div class="farm-listing-name">' + p.name + '</div>'
      + '<div class="farm-listing-meta">' + p.unit + ' &middot; ' + p.category + '</div>'
      + '<div class="farm-listing-price">&#8358;' + Number(p.price).toLocaleString() + '</div>'
      + '<div class="farm-listing-actions"><button class="farm-btn farm-btn-edit" onclick="openEditModal(' + p.id + ')">Edit</button><button class="farm-btn farm-btn-del" onclick="openDelModal(' + p.id + ')">Delete</button></div>'
      + '</div></div>';
  }).join('');
  updateStats();
}

function populateProfile() {
  if (!currentUser) return;
  var fp = farmerProfiles[currentUser.name] || farmerProfile;
  // Avatar circle
  var circleEl = document.getElementById('prof-photo-circle');
  var letterEl = document.getElementById('prof-avatar-letter');
  var oldImg = circleEl ? circleEl.querySelector('img') : null;
  if (oldImg) oldImg.remove();
  if (fp.photo) {
    if(letterEl) letterEl.style.display = 'none';
    var img = document.createElement('img');
    img.src = fp.photo; img.alt = currentUser.name;
    img.style.cssText = 'width:100%;height:100%;object-fit:cover;position:absolute;inset:0;';
    circleEl.appendChild(img);
  } else {
    if(letterEl){ letterEl.style.display = ''; letterEl.textContent = currentUser.name.charAt(0).toUpperCase(); }
    if(oldImg) oldImg.remove();
  }
  // Update navbar avatar too
  updateFarmNavAvatar(fp.photo, currentUser.name);

  var nm = document.getElementById('prof-name'); if(nm) nm.textContent = currentUser.name;
  var em = document.getElementById('prof-email'); if(em) em.textContent = currentUser.email;
  var fn2 = document.getElementById('pf-farmname'); if(fn2) fn2.textContent = fp.farmName || currentUser.name + "'s Farm";
  var lc = document.getElementById('pf-location'); if(lc) lc.textContent = fp.location || 'Ihiagwa, Owerri';
  var ph = document.getElementById('pf-phone'); if(ph) ph.textContent = fp.phone || 'Not set';
  var bi = document.getElementById('pf-bio'); if(bi) bi.textContent = fp.bio || 'Not set';
  var en = document.getElementById('pf-edit-name'); if(en) en.value = fp.farmName || '';
  var el2 = document.getElementById('pf-edit-loc'); if(el2) el2.value = fp.location || '';
  var ep = document.getElementById('pf-edit-phone'); if(ep) ep.value = fp.phone || '';
  var eb = document.getElementById('pf-edit-bio'); if(eb) eb.value = fp.bio || '';
  var es = document.getElementById('pf-edit-specialty'); if(es) es.value = fp.specialty || '';
  updateStats();
}

function updateFarmNavAvatar(photo, name) {
  var topAv = document.getElementById('farm-avatar-top');
  var topLetter = document.getElementById('farm-avatar-top-letter');
  if (!topAv) return;
  var oldImg = topAv.querySelector('img');
  if (oldImg) oldImg.remove();
  if (photo) {
    if(topLetter) topLetter.style.display = 'none';
    var img = document.createElement('img');
    img.src = photo; img.alt = name;
    img.style.cssText = 'width:100%;height:100%;object-fit:cover;';
    topAv.appendChild(img);
  } else {
    if(topLetter){ topLetter.style.display = ''; topLetter.textContent = (name||'F').charAt(0).toUpperCase(); }
  }
}

// ===== PROFILE PHOTO UPLOAD (dashboard) =====
function handleProfilePhoto(input) {
  var file = input.files[0];
  if (!file) return;
  if (file.size > 5*1024*1024) { toast('Image too large (max 5MB).'); return; }
  var reader = new FileReader();
  reader.onload = function(e) {
    var dataUrl = e.target.result;
    // Save to farmerProfiles
    if (currentUser) {
      if (!farmerProfiles[currentUser.name]) farmerProfiles[currentUser.name] = farmerProfile;
      farmerProfiles[currentUser.name].photo = dataUrl;
      farmerProfile.photo = dataUrl;
    }
    // Update products for this farmer
    products.filter(function(p){ return p.fid === currentUser.id; }).forEach(function(p){
      // photo stored in farmerProfiles, not on product directly
    });
    populateProfile();
    // Re-render marketplace if needed
    toast('Profile photo updated! Buyers will now see your photo.');
  };
  reader.readAsDataURL(file);
}

function saveProfile() {
  if (!currentUser) return;
  var newFarmName = document.getElementById('pf-edit-name').value;
  var newLoc = document.getElementById('pf-edit-loc').value;
  var newPhone = document.getElementById('pf-edit-phone').value;
  var newBio = document.getElementById('pf-edit-bio').value;
  var newSpec = document.getElementById('pf-edit-specialty').value;

  if (!farmerProfiles[currentUser.name]) farmerProfiles[currentUser.name] = {};
  farmerProfiles[currentUser.name].farmName = newFarmName;
  farmerProfiles[currentUser.name].location = newLoc;
  farmerProfiles[currentUser.name].phone = newPhone;
  farmerProfiles[currentUser.name].bio = newBio;
  farmerProfiles[currentUser.name].specialty = newSpec;
  // preserve photo
  farmerProfiles[currentUser.name].photo = farmerProfile.photo;

  // Sync farmerProfile reference
  farmerProfile = farmerProfiles[currentUser.name];

  // Update location on products listed by this farmer
  products.filter(function(p){ return p.fid === currentUser.id; }).forEach(function(p){
    p.farmer = currentUser.name;
    p.location = newLoc || p.location;
  });

  populateProfile();
  toast('Profile updated! Changes are now visible to buyers.');
}

// ===== LISTING MODALS =====
function openAddModal() {
  document.getElementById('edit-id').value = '';
  document.getElementById('modal-title').textContent = 'Add New Listing';
  document.getElementById('m-name').value = '';
  document.getElementById('m-desc').value = '';
  document.getElementById('m-price').value = '';
  document.getElementById('m-qty').value = '';
  photoDataURL = null;
  document.getElementById('upload-preview').style.display = 'none';
  document.getElementById('upload-ph').style.display = 'block';
  document.getElementById('photo-input').value = '';
  document.getElementById('listing-modal').classList.add('open');
}

function openEditModal(id) {
  var p = products.find(function(x){ return x.id===id; });
  if (!p) return;
  document.getElementById('edit-id').value = id;
  document.getElementById('modal-title').textContent = 'Edit Listing';
  document.getElementById('m-name').value = p.name;
  document.getElementById('m-desc').value = p.desc || '';
  document.getElementById('m-price').value = p.price;
  document.getElementById('m-qty').value = p.qty || '';
  document.getElementById('m-unit').value = p.unit;
  document.getElementById('m-cat').value = p.category;
  photoDataURL = p.image || null;
  if (p.image) {
    var prev = document.getElementById('upload-preview');
    prev.src = p.image; prev.style.display='block';
    document.getElementById('upload-ph').style.display='none';
  } else {
    document.getElementById('upload-preview').style.display='none';
    document.getElementById('upload-ph').style.display='block';
  }
  document.getElementById('listing-modal').classList.add('open');
}

function closeModal(id) {
  document.getElementById(id).classList.remove('open');
}

function handlePhoto(input) {
  var file = input.files[0];
  if (!file) return;
  if (file.size > 5*1024*1024) { toast('Image too large (max 5MB).'); return; }
  var reader = new FileReader();
  reader.onload = function(e) {
    photoDataURL = e.target.result;
    var prev = document.getElementById('upload-preview');
    prev.src = photoDataURL; prev.style.display='block';
    document.getElementById('upload-ph').style.display='none';
  };
  reader.readAsDataURL(file);
}

function saveListing() {
  var name = document.getElementById('m-name').value.trim();
  var price = document.getElementById('m-price').value;
  if (!name || !price) { toast('Name and price are required.'); return; }
  var editId = document.getElementById('edit-id').value;
  var fp = farmerProfiles[currentUser.name] || farmerProfile;
  var farmerName = currentUser.name;
  var farmerLoc = fp.location || 'Ihiagwa, Owerri';

  if (editId) {
    var idx = -1;
    for (var i=0;i<products.length;i++){ if(products[i].id===parseInt(editId)){ idx=i; break; } }
    if (idx !== -1) {
      products[idx].name = name;
      products[idx].price = parseInt(price);
      products[idx].unit = document.getElementById('m-unit').value;
      products[idx].category = document.getElementById('m-cat').value;
      products[idx].desc = document.getElementById('m-desc').value;
      if (photoDataURL) products[idx].image = photoDataURL;
      products[idx].farmer = farmerName;
      products[idx].location = farmerLoc;
    }
    toast('"' + name + '" updated.');
  } else {
    var newId = Date.now();
    products.unshift({ id:newId, name:name, image:photoDataURL||null, price:parseInt(price), unit:document.getElementById('m-unit').value, category:document.getElementById('m-cat').value, desc:document.getElementById('m-desc').value, farmer:farmerName, location:farmerLoc, stars:5, badge:'New', fid:currentUser.id });
    toast('"' + name + '" listed on the marketplace.');
  }
  closeModal('listing-modal');
  renderDashListings();
  updateStats();
}

function openDelModal(id) {
  pendingDeleteId = id;
  document.getElementById('delete-modal').classList.add('open');
}

function confirmDelete() {
  if (pendingDeleteId === null) return;
  var idx = -1;
  for (var i=0;i<products.length;i++){ if(products[i].id===pendingDeleteId){ idx=i; break; } }
  var name = idx !== -1 ? products[idx].name : '';
  if (idx !== -1) products.splice(idx, 1);
  var ci = cart.findIndex(function(c){ return c.id===pendingDeleteId; });
  if (ci !== -1) cart.splice(ci, 1);
  updateBadge();
  pendingDeleteId = null;
  closeModal('delete-modal');
  renderDashListings();
  updateStats();
  if (name) toast('"' + name + '" removed.');
}

// ===== ORDERS STATE =====
// allOrders: array of order objects, each { id, studentName, studentEmail, studentPhoto, studentPhone, studentHostel, studentRoom, studentNotes, items:[{...product, qty}], total, date, status, farmerName }
var allOrders = [];
var currentOrderFilter = 'all';
var viewingOrderId = null;

// ===== PAYMENT =====
function selectPay(el) {
  document.querySelectorAll('.pay-method').forEach(function(m){ m.classList.remove('active'); });
  el.classList.add('active');
}

function fmtCard(input) {
  var val = input.value.replace(/\D/g,'').slice(0,16);
  input.value = val.replace(/(.{4})/g,'$1 ').trim();
  var d = document.getElementById('card-display');
  if (d) d.textContent = (input.value || '.... .... .... ....').padEnd(19,'.').slice(0,19);
}

function completePurchase() {
  if (!cart.length) { toast('Your cart is empty.'); return; }
  var oid = '#AGM-' + Math.floor(Math.random()*900000+100000);
  var el = document.getElementById('order-id'); if(el) el.textContent = oid;

  // Group cart items by farmer and record orders
  var now = new Date();
  var dateStr = now.toLocaleDateString('en-NG', { day:'numeric', month:'short', year:'numeric' })
              + ' · ' + now.toLocaleTimeString('en-NG', { hour:'2-digit', minute:'2-digit' });
  var byFarmer = {};
  cart.forEach(function(item) {
    if (!byFarmer[item.farmer]) byFarmer[item.farmer] = [];
    byFarmer[item.farmer].push(item);
  });
  Object.keys(byFarmer).forEach(function(farmerName) {
    var items = byFarmer[farmerName];
    var total = items.reduce(function(a,c){ return a + c.price*c.qty; }, 0) + 500;
    allOrders.push({
      id: oid + (Object.keys(byFarmer).length > 1 ? '-' + farmerName.split(' ')[0].toUpperCase() : ''),
      studentName: currentUser ? currentUser.name : 'Student',
      studentEmail: currentUser ? currentUser.email : '',
      studentPhoto: studentProfile.photo || null,
      studentPhone: studentProfile.phone || 'Not provided',
      studentHostel: studentProfile.hostel || 'Not provided',
      studentRoom: studentProfile.room || 'Not provided',
      studentNotes: studentProfile.notes || 'None',
      items: items.map(function(i){ return Object.assign({}, i); }),
      total: total,
      date: dateStr,
      status: 'pending',
      farmerName: farmerName
    });
  });

  cart = []; updateBadge();
  showPage('success');
}

// ===== ORDERS SECTION (farmer dashboard) =====
function getMyOrders() {
  if (!currentUser) return [];
  return allOrders.filter(function(o){ return o.farmerName === currentUser.name; });
}

function renderOrders() {
  var orders = getMyOrders();
  var filtered = currentOrderFilter === 'all' ? orders
    : orders.filter(function(o){ return o.status === currentOrderFilter; });

  var list = document.getElementById('farm-orders-list');
  var none = document.getElementById('farm-no-orders');
  var count = document.getElementById('orders-count');
  if (count) count.textContent = filtered.length + ' order' + (filtered.length !== 1 ? 's' : '');

  if (!filtered.length) {
    if(list) list.innerHTML = '';
    if(none) none.style.display = 'block';
    return;
  }
  if(none) none.style.display = 'none';

  list.innerHTML = filtered.map(function(o) {
    var statusCls = o.status === 'delivered' ? 'order-status-delivered' : 'order-status-pending';
    var statusLabel = o.status === 'delivered' ? 'Delivered' : 'Pending';
    var avHtml = o.studentPhoto
      ? '<img src="' + o.studentPhoto + '" alt="' + o.studentName + '">'
      : '<span>' + o.studentName.charAt(0).toUpperCase() + '</span>';
    var itemNames = o.items.map(function(i){ return i.name; }).join(', ');
    return '<div class="farm-order-row" onclick="openOrderDetail(\'' + o.id.replace(/'/g,"\\'") + '\')">'
      + '<div class="farm-order-student">'
      + '<div class="farm-order-stu-av">' + avHtml + '</div>'
      + '<div><div class="farm-order-stu-name">' + o.studentName + '</div><div class="farm-order-stu-email">' + o.studentEmail + '</div></div>'
      + '</div>'
      + '<div class="farm-order-id">' + o.id + '</div>'
      + '<div class="farm-order-items-count">' + o.items.length + ' item' + (o.items.length!==1?'s':'') + '</div>'
      + '<div class="farm-order-amount">&#8358;' + Number(o.total).toLocaleString() + '</div>'
      + '<div><span class="farm-order-status ' + statusCls + '">' + statusLabel + '</span></div>'
      + '<div class="farm-order-action"><button class="farm-order-view-btn" onclick="event.stopPropagation();openOrderDetail(\'' + o.id.replace(/'/g,"\\'") + '\')">View</button></div>'
      + '</div>';
  }).join('');

  // Update pending count in stat card
  var pending = orders.filter(function(o){ return o.status === 'pending'; }).length;
  var pendingEl = document.querySelector('.farm-stat-card:nth-child(2) .farm-stat-val');
  if (pendingEl) pendingEl.textContent = pending;
}

function filterOrders(filter, btn) {
  currentOrderFilter = filter;
  document.querySelectorAll('.farm-order-filter-btn').forEach(function(b){ b.classList.remove('active'); });
  btn.classList.add('active');
  renderOrders();
}

function openOrderDetail(orderId) {
  var o = allOrders.find(function(x){ return x.id === orderId; });
  if (!o) return;
  viewingOrderId = orderId;

  // Student avatar
  var avEl = document.getElementById('omd-stu-av');
  var avLetter = document.getElementById('omd-stu-letter');
  var oldImg = avEl.querySelector('img');
  if (oldImg) oldImg.remove();
  if (o.studentPhoto) {
    avLetter.style.display = 'none';
    var img = document.createElement('img');
    img.src = o.studentPhoto; img.alt = o.studentName;
    avEl.appendChild(img);
  } else {
    avLetter.style.display = '';
    avLetter.textContent = o.studentName.charAt(0).toUpperCase();
  }

  document.getElementById('omd-stu-name').textContent = o.studentName;
  document.getElementById('omd-stu-meta').textContent = o.studentEmail + (o.studentPhone !== 'Not provided' ? ' · ' + o.studentPhone : '');
  document.getElementById('omd-order-id').textContent = o.id;
  document.getElementById('omd-date').textContent = o.date;
  document.getElementById('omd-items-count').textContent = o.items.length + ' item' + (o.items.length!==1?'s':'');
  var statusCls = o.status === 'delivered' ? 'order-status-delivered' : 'order-status-pending';
  var statusLabel = o.status === 'delivered' ? 'Delivered' : 'Pending';
  document.getElementById('omd-status').innerHTML = '<span class="farm-order-status ' + statusCls + '">' + statusLabel + '</span>';

  // Items
  var itemsHtml = o.items.map(function(item) {
    var imgHtml = item.image
      ? '<img src="' + item.image + '" alt="' + item.name + '">'
      : '<div class="order-item-img-ph">No img</div>';
    return '<div class="order-item-row">'
      + '<div class="order-item-img">' + imgHtml + '</div>'
      + '<div class="order-item-info">'
      + '<div class="order-item-name">' + item.name + '</div>'
      + '<div class="order-item-meta">Qty: ' + item.qty + ' &middot; ' + item.unit + '</div>'
      + '</div>'
      + '<div class="order-item-price">&#8358;' + (item.price * item.qty).toLocaleString() + '</div>'
      + '</div>';
  }).join('');
  document.getElementById('omd-items-list').innerHTML = itemsHtml;
  document.getElementById('omd-total').textContent = Number(o.total).toLocaleString();

  // Delivery
  document.getElementById('omd-hostel').textContent = o.studentHostel;
  document.getElementById('omd-room').textContent = o.studentRoom;
  document.getElementById('omd-phone').textContent = o.studentPhone;
  document.getElementById('omd-notes').textContent = o.studentNotes;

  // Mark btn
  var markBtn = document.getElementById('omd-mark-btn');
  if (o.status === 'delivered') {
    markBtn.disabled = true;
    markBtn.textContent = 'Already Delivered';
  } else {
    markBtn.disabled = false;
    markBtn.textContent = 'Mark as Delivered';
  }

  document.getElementById('order-detail-modal').classList.add('open');
}

function markOrderDelivered() {
  var o = allOrders.find(function(x){ return x.id === viewingOrderId; });
  if (!o) return;
  o.status = 'delivered';
  var statusEl = document.getElementById('omd-status');
  if (statusEl) statusEl.innerHTML = '<span class="farm-order-status order-status-delivered">Delivered</span>';
  var markBtn = document.getElementById('omd-mark-btn');
  if (markBtn) { markBtn.disabled = true; markBtn.textContent = 'Already Delivered'; }
  renderOrders();
  toast('Order marked as delivered.');
}

// ===== STUDENT PROFILE STATE =====
var studentProfile = {
  phone: '', dept: '', matric: '', level: '', hostel: '', room: '', notes: '', photo: null
};

// ===== STUDENT PROFILE PAGE =====
function loadStudentProfilePage() {
  if (!currentUser) return;
  // Hero
  document.getElementById('stu-hero-name').textContent = currentUser.name;
  document.getElementById('stu-hero-email').textContent = currentUser.email;
  // Avatar
  var circle = document.getElementById('stu-avatar-circle');
  var letter = document.getElementById('stu-avatar-letter');
  var oldImg = circle.querySelector('img');
  if (oldImg) oldImg.remove();
  if (studentProfile.photo) {
    letter.style.display = 'none';
    var img = document.createElement('img');
    img.src = studentProfile.photo;
    img.style.cssText = 'width:100%;height:100%;object-fit:cover;';
    circle.appendChild(img);
  } else {
    letter.style.display = '';
    letter.textContent = currentUser.name.charAt(0).toUpperCase();
  }
  // View values
  document.getElementById('stu-view-name').textContent = currentUser.name;
  document.getElementById('stu-view-email').textContent = currentUser.email;
  document.getElementById('stu-view-phone').textContent = studentProfile.phone || 'Not set';
  document.getElementById('stu-view-dept').textContent = studentProfile.dept || 'Not set';
  document.getElementById('stu-view-matric').textContent = studentProfile.matric || 'Not set';
  document.getElementById('stu-view-level').textContent = studentProfile.level || 'Not set';
  document.getElementById('stu-view-hostel').textContent = studentProfile.hostel || 'Not set';
  document.getElementById('stu-view-room').textContent = studentProfile.room || 'Not set';
  document.getElementById('stu-view-notes').textContent = studentProfile.notes || 'None';
  // Edit field prefill
  document.getElementById('stu-edit-name').value = currentUser.name;
  document.getElementById('stu-edit-phone').value = studentProfile.phone;
  document.getElementById('stu-edit-dept').value = studentProfile.dept;
  document.getElementById('stu-edit-matric').value = studentProfile.matric;
  document.getElementById('stu-edit-level').value = studentProfile.level;
  document.getElementById('stu-edit-hostel').value = studentProfile.hostel;
  document.getElementById('stu-edit-room').value = studentProfile.room;
  document.getElementById('stu-edit-notes').value = studentProfile.notes;
  // Stats
  document.getElementById('stu-stat-orders').textContent = cart.length > 0 ? cart.length : '0';
}

function toggleStuEdit(section) {
  var viewEl = document.getElementById('stu-' + section + '-view');
  var editEl = document.getElementById('stu-' + section + '-edit');
  var isEditing = editEl.style.display !== 'none';
  viewEl.style.display = isEditing ? '' : 'none';
  editEl.style.display = isEditing ? 'none' : '';
  // Update toggle button text
  var cards = document.querySelectorAll('.stu-section-card');
  cards.forEach(function(card) {
    var btn = card.querySelector('.stu-edit-toggle');
    if (!btn) return;
    var editDiv = card.querySelector('[id$="-edit"]');
    if (editDiv && editDiv.id === 'stu-' + section + '-edit') {
      btn.textContent = editEl.style.display !== 'none' ? 'Cancel' : 'Edit';
    }
  });
}

function saveStudentProfile() {
  var newName = document.getElementById('stu-edit-name').value.trim();
  if (newName) currentUser.name = newName;
  studentProfile.phone = document.getElementById('stu-edit-phone').value.trim();
  studentProfile.dept = document.getElementById('stu-edit-dept').value.trim();
  studentProfile.matric = document.getElementById('stu-edit-matric').value.trim();
  studentProfile.level = document.getElementById('stu-edit-level').value;
  // Update nav name and avatar letter
  document.getElementById('user-nav-name').textContent = currentUser.name;
  document.getElementById('user-avatar-letter').textContent = currentUser.name.charAt(0).toUpperCase();
  toggleStuEdit('info');
  loadStudentProfilePage();
  toast('Profile updated successfully.');
}

function saveStudentAddress() {
  studentProfile.hostel = document.getElementById('stu-edit-hostel').value.trim();
  studentProfile.room = document.getElementById('stu-edit-room').value.trim();
  studentProfile.notes = document.getElementById('stu-edit-notes').value.trim();
  toggleStuEdit('address');
  loadStudentProfilePage();
  toast('Delivery address saved.');
}

function handleStudentPhoto(input) {
  var file = input.files[0];
  if (!file) return;
  if (file.size > 5*1024*1024) { toast('Image too large (max 5MB).'); return; }
  var reader = new FileReader();
  reader.onload = function(e) {
    studentProfile.photo = e.target.result;
    // Update navbar avatar
    var navAv = document.getElementById('user-avatar');
    var navLetter = document.getElementById('user-avatar-letter');
    var oldNavImg = navAv.querySelector('img');
    if (oldNavImg) oldNavImg.remove();
    navLetter.style.display = 'none';
    var navImg = document.createElement('img');
    navImg.src = e.target.result;
    navImg.style.cssText = 'width:100%;height:100%;object-fit:cover;border-radius:50%;';
    navAv.appendChild(navImg);
    loadStudentProfilePage();
    toast('Profile photo updated.');
  };
  reader.readAsDataURL(file);
}

// ===== TOAST =====
function toast(msg) {
  var t = document.getElementById('toast');
  var m = document.getElementById('toast-msg');
  if (!t || !m) return;
  m.textContent = msg;
  t.classList.add('show');
  clearTimeout(t._timer);
  t._timer = setTimeout(function(){ t.classList.remove('show'); }, 3200);
}

// Close modals on overlay click
document.querySelectorAll('.modal-overlay').forEach(function(o){
  o.addEventListener('click', function(e){ if(e.target===o) closeModal(o.id); });
});
document.getElementById('fp-modal').addEventListener('click', function(e){
  if (e.target === this) closeFpModal();
});

// Seed demo orders for default farmers
(function seedDemoOrders() {
  var demoOrders = [
    { id:'#AGM-481203', studentName:'Chukwuemeka Obi', studentEmail:'c.obi@futo.edu.ng', studentPhoto:null, studentPhone:'+234 803 456 7890', studentHostel:'Alvan Ikoku Hall, Block B', studentRoom:'Room 14', studentNotes:'Please drop at the block entrance', items:[{id:1,name:'Fresh Tomatoes',image:'https://img.freepik.com/premium-photo/fresh-organic-tomatoes_66869-583.jpg',price:800,unit:'per basket',qty:2,farmer:'Musa Okafor'},{id:6,name:'Ugu Leaves',image:'https://tse3.mm.bing.net/th/id/OIP.WMffkCx-wDzf7Nikuja36QHaFj?cb=defcache2&defcache=1&rs=1&pid=ImgDetMain&o=7&rm=3',price:200,unit:'per bunch',qty:3,farmer:'Musa Okafor'}], total:2700, date:'19 Feb 2026 · 10:32 AM', status:'pending', farmerName:'Musa Okafor' },
    { id:'#AGM-312874', studentName:'Amaka Nwofor', studentEmail:'a.nwofor@futo.edu.ng', studentPhoto:null, studentPhone:'+234 807 123 4567', studentHostel:'Post Graduate Hostel, Block A', studentRoom:'Room 3', studentNotes:'', items:[{id:11,name:'Banana',image:'https://th.bing.com/th/id/OIP.UVy2b85VJffWYhf50Wzz-AHaFN?o=7&cb=defcache2&rm=3&defcache=1&rs=1&pid=ImgDetMain&o=7&rm=3',price:500,unit:'per bunch',qty:1,farmer:'Musa Okafor'}], total:1000, date:'18 Feb 2026 · 08:15 AM', status:'delivered', farmerName:'Musa Okafor' },
    { id:'#AGM-567921', studentName:'Ngozi Eze', studentEmail:'n.eze@futo.edu.ng', studentPhoto:null, studentPhone:'+234 805 987 6543', studentHostel:'Female Hostel, Block C', studentRoom:'Room 22', studentNotes:'Call on arrival', items:[{id:1,name:'Fresh Tomatoes',image:'https://img.freepik.com/premium-photo/fresh-organic-tomatoes_66869-583.jpg',price:800,unit:'per basket',qty:1,farmer:'Musa Okafor'}], total:1300, date:'17 Feb 2026 · 02:45 PM', status:'delivered', farmerName:'Musa Okafor' },
    { id:'#AGM-734510', studentName:'Bolarinwa Adeyemi', studentEmail:'b.adeyemi@futo.edu.ng', studentPhoto:null, studentPhone:'+234 812 345 6789', studentHostel:'Biobaku Hall, Block D', studentRoom:'Room 7', studentNotes:'', items:[{id:2,name:'Sweet Pineapples',image:'https://tse1.mm.bing.net/th/id/OIP.LFTllfCXBmxXIyVmTjaZ0QHaE7?cb=defcache2&defcache=1&rs=1&pid=ImgDetMain&o=7&rm=3',price:500,unit:'each',qty:3,farmer:'Ada Nwosu'},{id:7,name:'Yellow Corn',image:'https://images.squarespace-cdn.com/content/v1/6064cb7418b622722c221663/1630006723933-WBP0378C5FI50IE3UUGR/corn2.jpeg',price:250,unit:'per cob',qty:5,farmer:'Ada Nwosu'}], total:3250, date:'19 Feb 2026 · 09:00 AM', status:'pending', farmerName:'Ada Nwosu' },
    { id:'#AGM-819233', studentName:'Kelechi Mgbemena', studentEmail:'k.mgbemena@futo.edu.ng', studentPhoto:null, studentPhone:'+234 806 654 3210', studentHostel:'Awolowo Hall, Block A', studentRoom:'Room 11', studentNotes:'', items:[{id:5,name:'Plantains',image:'https://thumbs.dreamstime.com/b/green-bananas-fresh-raw-asian-big-collected-to-transport-south-asia-194040741.jpg',price:1200,unit:'per bunch',qty:1,farmer:'Chidi Obi'},{id:9,name:'Yam',image:'https://nigerianfinder.com/wp-content/uploads/2020/03/How-to-Preserve-Yam-in-Nigeria.jpg',price:800,unit:'per tuber',qty:2,farmer:'Chidi Obi'}], total:3300, date:'18 Feb 2026 · 11:20 AM', status:'pending', farmerName:'Chidi Obi' }
  ];
  allOrders = demoOrders;
})();

// INIT
renderFeatured();
</script>
<!-- ORDER DETAIL MODAL -->
<div class="modal-overlay" id="order-detail-modal">
  <div class="order-modal">
    <div class="order-modal-hero">
      <div class="order-modal-stu-av" id="omd-stu-av"><span id="omd-stu-letter">S</span></div>
      <div class="order-modal-stu-info">
        <div class="order-modal-stu-name" id="omd-stu-name">Student Name</div>
        <div class="order-modal-stu-meta" id="omd-stu-meta">email · phone</div>
        <div class="order-modal-id" id="omd-order-id">#AGM-000000</div>
      </div>
      <button class="order-modal-close" onclick="closeModal('order-detail-modal')">&#215;</button>
    </div>
    <div class="order-modal-body">
      <div class="order-modal-section">
        <div class="order-modal-section-title">Order Summary</div>
        <div class="order-info-grid">
          <div class="order-info-tile"><div class="order-info-tile-label">Date &amp; Time</div><div class="order-info-tile-val" id="omd-date">—</div></div>
          <div class="order-info-tile"><div class="order-info-tile-label">Status</div><div class="order-info-tile-val" id="omd-status">—</div></div>
          <div class="order-info-tile"><div class="order-info-tile-label">Items</div><div class="order-info-tile-val" id="omd-items-count">—</div></div>
          <div class="order-info-tile"><div class="order-info-tile-label">Payment</div><div class="order-info-tile-val">Card</div></div>
        </div>
      </div>
      <div class="order-modal-section">
        <div class="order-modal-section-title">Items Ordered</div>
        <div class="order-items-list" id="omd-items-list"></div>
        <div class="order-total-bar">
          <span class="order-total-lbl">Total Paid</span>
          <span class="order-total-val" id="omd-total">₦0</span>
        </div>
      </div>
      <div class="order-modal-section">
        <div class="order-modal-section-title">Delivery Details</div>
        <div class="order-delivery-box">
          <div class="order-delivery-row"><span class="order-delivery-label">Hostel / Block</span><span class="order-delivery-val" id="omd-hostel">Not provided</span></div>
          <div class="order-delivery-row"><span class="order-delivery-label">Room</span><span class="order-delivery-val" id="omd-room">Not provided</span></div>
          <div class="order-delivery-row"><span class="order-delivery-label">Phone</span><span class="order-delivery-val" id="omd-phone">Not provided</span></div>
          <div class="order-delivery-row"><span class="order-delivery-label">Notes</span><span class="order-delivery-val" id="omd-notes">None</span></div>
        </div>
      </div>
    </div>
    <div class="order-modal-footer">
      <button class="modal-cancel" onclick="closeModal('order-detail-modal')">Close</button>
      <button class="order-mark-btn" id="omd-mark-btn" onclick="markOrderDelivered()">Mark as Delivered</button>
    </div>
  </div>
</div>

</body>
</html>
