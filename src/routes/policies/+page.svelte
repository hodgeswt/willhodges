<script>
  import { onMount } from 'svelte';
  import { fade, fly } from 'svelte/transition';
  
  let visible = false;
  
  onMount(() => {
    visible = true;
  });
</script>

<svelte:head>
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css">
</svelte:head>

<!-- Header -->
<header class="header">
  <div class="container">
    <h1 class="logo">Product Policies</h1>
    <p class="tagline">Policies relating to my products</p>
  </div>
</header>

<!-- Main Content -->
<main class="main-content">
  {#if visible}
    <!-- About Section -->
    <section class="section" in:fade={{ duration: 600 }}>
      <div class="container">
        <h2 class="section-title">About My Products</h2>
        <div class="content-card">
          <p>
            This page provides information about my products, their privacy practices, refund policies, etc. All information applies to my products, including but not limited to Cinemadle.
          </p>
        </div>
      </div>
    </section>

    <section class="section" in:fly={{ y: 30, duration: 600, delay: 200 }}>
      <div class="container">
        <h2 class="section-title">Cinemadle</h2>
        <div class="content-card">
          <p>
            Cinemadle is an engaging web-based game that challenges movie enthusiasts to test their film knowledge. 
            Players guess movies based on various clues including genres, MPAA rating, and cast information.
          </p>
        </div>
      </div>
    </section>

    <!-- Services Section -->
    <section class="section alt-bg" in:fly={{ y: 30, duration: 600, delay: 200 }}>
      <div class="container">
        <h2 class="section-title">Cinemadle Services</h2>
        <div class="content-card">
          <div class="service-item">
            <h3>Standard - Free</h3>
            <p>Play without an account -- limited features, no clues</p>
          </div>
          <div class="service-item">
            <h3>Cinemadle Account - Free</h3>
            <p>Unlock extra features including:</p>
            <ul>
              <li>Limited hints near game-end</li>
            </ul>
          </div>
          <div class="service-item">
            <h3>Cinemadle Pro - Paid (coming soon)</h3>
            <p>Unlock extra features including:</p>
            <ul>
              <li>Unlimited hints</li>
              <li>Data insights</li>
              <li>Strategy review</li>
            </ul>
          </div>
        </div>
      </div>
    </section>

    <!-- Policies Section -->
    <section class="section" in:fly={{ y: 30, duration: 600, delay: 400 }}>
      <div class="container">
        <h2 class="section-title">Policies & Terms (All Products)</h2>
        
        <!-- Refund Policy -->
        <div class="policy-card">
          <h3><i class="fas fa-undo"></i> Refund & Dispute Policy</h3>
          <p>
            I want you to be satisfied with your subscriptions and payments. If you're not completely happy:
          </p>
          <ul>
            <li>Full refund available within 7 days of purchase</li>
            <li>To request a refund, contact me via email with your order details</li>
          </ul>
        </div>

        <!-- Cancellation Policy -->
        <div class="policy-card">
          <h3><i class="fas fa-times-circle"></i> Subscription Cancellation Policy</h3>
          <p>
            You can cancel your subscription at any time:
          </p>
          <ul>
            <li>Cancel directly from your account settings</li>
            <li>Access continues until the end of your billing period</li>
            <li>No cancellation fees</li>
            <li>Re-subscribe anytime to regain benefits</li>
          </ul>
        </div>

        <!-- Terms of Service -->
        <div class="policy-card">
          <h3><i class="fas fa-file-contract"></i> Terms and Conditions</h3>
          <p>By using my products, you agree to:</p>
          <ul>
            <li>Use the service for personal, non-commercial purposes only</li>
            <li>Not share account credentials with others</li>
            <li>Not use automated tools or bots to play the game</li>
            <li>Respect intellectual property rights</li>
            <li>Follow our community guidelines and fair play rules</li>
          </ul>
        </div>
      </div>
    </section>

    <!-- Contact Section -->
    <section class="section alt-bg" in:fly={{ y: 30, duration: 600, delay: 600 }}>
      <div class="container">
        <h2 class="section-title">Contact</h2>
        <div class="contact-grid">
          <div class="contact-card">
            <i class="fas fa-envelope"></i>
            <h3>Email Support</h3>
            <p>hodges.wt@gmail.com</p>
            <p class="response-time">Response within 24 hours</p>
          </div>
        </div>
      </div>
    </section>
  {/if}
</main>

<!-- Footer -->
<footer class="footer">
  <div class="container">
    <p>&copy; 2025 Will Hodges. All rights reserved.</p>
  </div>
</footer>

<style>
  :global(body) {
    margin: 0;
    padding: 0;
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, sans-serif;
    background-color: #0a0a0a;
    color: #ffffff;
    line-height: 1.6;
  }

  /* Header */
  .header {
    background: linear-gradient(135deg, #1a1a2e 0%, #0a0a0a 100%);
    padding: 3rem 0;
    text-align: center;
    border-bottom: 1px solid rgba(255, 255, 255, 0.1);
  }

  .logo {
    font-size: 3rem;
    margin: 0;
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    -webkit-background-clip: text;
    background-clip: text;
    -webkit-text-fill-color: transparent;
    font-weight: 700;
  }

  .tagline {
    color: #a0a0a0;
    font-size: 1.2rem;
    margin-top: 0.5rem;
  }

  /* Layout */
  .container {
    max-width: 1000px;
    margin: 0 auto;
    padding: 0 2rem;
  }

  .main-content {
    min-height: calc(100vh - 200px);
  }

  .section {
    padding: 4rem 0;
  }

  .alt-bg {
    background-color: #0f0f0f;
  }

  .section-title {
    font-size: 2rem;
    text-align: center;
    margin-bottom: 2rem;
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    -webkit-background-clip: text;
    background-clip: text;
    -webkit-text-fill-color: transparent;
  }

  /* Content Cards */
  .content-card {
    background: #1a1a1a;
    padding: 2rem;
    border-radius: 10px;
    border: 1px solid rgba(255, 255, 255, 0.1);
  }

  .content-card p {
    color: #e0e0e0;
    margin-bottom: 1rem;
  }

  /* Services */
  .service-item {
    margin-bottom: 2rem;
    padding-bottom: 2rem;
    border-bottom: 1px solid rgba(255, 255, 255, 0.1);
  }

  .service-item:last-child {
    border-bottom: none;
    margin-bottom: 0;
    padding-bottom: 0;
  }

  .service-item h3 {
    color: #667eea;
    margin-bottom: 1rem;
  }

  .service-item ul {
    margin: 1rem 0;
    padding-left: 1.5rem;
  }

  .service-item li {
    color: #e0e0e0;
    margin-bottom: 0.5rem;
  }

  /* Policy Cards */
  .policy-card {
    background: #1a1a1a;
    padding: 2rem;
    border-radius: 10px;
    border: 1px solid rgba(255, 255, 255, 0.1);
    margin-bottom: 2rem;
  }

  .policy-card h3 {
    color: #ffffff;
    margin-bottom: 1rem;
    display: flex;
    align-items: center;
    gap: 0.5rem;
  }

  .policy-card h3 i {
    color: #667eea;
  }

  .policy-card p {
    color: #e0e0e0;
    margin-bottom: 1rem;
  }

  .policy-card ul {
    margin: 0;
    padding-left: 1.5rem;
  }

  .policy-card li {
    color: #e0e0e0;
    margin-bottom: 0.5rem;
  }

  /* Contact Grid */
  .contact-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
    gap: 2rem;
  }

  .contact-card {
    background: #1a1a1a;
    padding: 2rem;
    border-radius: 10px;
    border: 1px solid rgba(255, 255, 255, 0.1);
    text-align: center;
    transition: all 0.3s ease;
  }

  .contact-card:hover {
    border-color: #667eea;
    transform: translateY(-5px);
  }

  .contact-card i {
    font-size: 3rem;
    color: #667eea;
    margin-bottom: 1rem;
  }

  .contact-card h3 {
    color: #ffffff;
    margin-bottom: 0.5rem;
  }

  .contact-card p {
    color: #e0e0e0;
    margin: 0.5rem 0;
  }

  .response-time {
    color: #a0a0a0;
    font-size: 0.9rem;
  }

  /* Footer */
  .footer {
    background: #0f0f0f;
    padding: 2rem 0;
    text-align: center;
    border-top: 1px solid rgba(255, 255, 255, 0.1);
  }

  .footer p {
    color: #a0a0a0;
    margin: 0.5rem 0;
  }

  /* Responsive */
  @media (max-width: 768px) {
    .logo {
      font-size: 2rem;
    }

    .tagline {
      font-size: 1rem;
    }

    .section {
      padding: 3rem 0;
    }

    .section-title {
      font-size: 1.5rem;
    }

    .contact-grid {
      grid-template-columns: 1fr;
    }
  }
</style>