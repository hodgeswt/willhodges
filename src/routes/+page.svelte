<script lang="ts">
  import { onMount } from 'svelte';
  import { fade, fly, scale } from 'svelte/transition';
  import me from "$lib/assets/me.png";
  
  let name = "Will Hodges";
  let title = "Full Stack Developer";
  let bio = [
    "Passionate developer with a love for creating backend applications. I enjoy turning complex problems into simple solutions.",
    "I work full-time as a full-stack developer with NCR Voyix Corporation. There, I lead development on two large-scale international retail point-of-sale systems, and have contributed development to two additional large-scale grocery point-of-sale systems.",
    "I have a passion for development, aiming to create clean and readable code that can be easily maintained. I am an advocate for best practices."
  ];
  
  let skills = ["C#", ".NET", ".NET Framework", "PowerShell", "Golang", "TypeScript", "JavaScript", "React.js", "React Native"]
  
  let projects = [
    {
      title: "cinemadle",
      description: "A web game built with Svelte and .NET",
      tech: ["C#", ".NET", "Svelte", "Sqlite"],
      link: "https://cinemadle.com"
    },
    {
      title: "WH-02",
      description: "Simulated 8-Bit CPU",
      tech: ["Logisim"],
      link: "https://github.com/hodgeswt/WH-02"
    },
    {
      title: "utilw",
      description: "Shared utilities library",
      tech: ["Golang"],
      link: "https://github.com/hodgeswt/utilw"
    }
  ];
  
  let socialLinks = [
    { name: "GitHub", url: "https://github.com/hodgeswt", icon: "fab fa-github" },
    { name: "LinkedIn", url: "https://linkedin.com/in/hodgeswt", icon: "fab fa-linkedin" },
    { name: "Email", url: "mailto:hodges.wt@gmail.com", icon: "fas fa-envelope" }
  ];
  
  let visible = false;
  let activeSection = 'home';
  
  onMount(() => {
    visible = true;
  });
  
  function scrollToSection(sectionId: string) {
    document.getElementById(sectionId)?.scrollIntoView({ behavior: 'smooth' });
    activeSection = sectionId;
  }
</script>

<svelte:head>
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css">
</svelte:head>

<nav class="navbar">
  <div class="nav-container">
    <div class="nav-brand">{name}</div>
    <ul class="nav-menu">
      <li><button on:click={() => scrollToSection('home')} class:active={activeSection === 'home'}>Home</button></li>
      <li><button on:click={() => scrollToSection('about')} class:active={activeSection === 'about'}>About</button></li>
      <li><button on:click={() => scrollToSection('projects')} class:active={activeSection === 'projects'}>Projects</button></li>
      <li><button on:click={() => scrollToSection('contact')} class:active={activeSection === 'contact'}>Contact</button></li>
    </ul>
  </div>
</nav>

<section id="home" class="hero">
  {#if visible}
    <div class="hero-content" in:fade={{ duration: 1000 }}>
      <h1 class="hero-title" in:fly={{ y: 30, duration: 800, delay: 200 }}>
        Hi, I'm <span class="accent">{name}</span>
      </h1>
      <p class="hero-subtitle" in:fly={{ y: 30, duration: 800, delay: 400 }}>
        {title}
      </p>
      <div class="hero-buttons" in:fly={{ y: 30, duration: 800, delay: 600 }}>
        <button class="btn btn-primary" on:click={() => scrollToSection('projects')}>
          View My Work
        </button>
        <button class="btn btn-secondary" on:click={() => scrollToSection('contact')}>
          Get In Touch
        </button>
      </div>
    </div>
  {/if}
</section>

<section id="about" class="about">
  <div class="container">
    <h2 class="section-title">About Me</h2>
    <div class="about-content">
      <div class="about-text">
        {#each bio as line}
            <p>{line}</p>
        {/each}
      </div>
      <div class="about-image">
        <div class="image-placeholder">
          <img src={me} alt="will hodges" />
        </div>
      </div>
    </div>
  </div>
</section>

<section id="skills" class="skills">
  <div class="container">
    <h2 class="section-title">Skills</h2>
    <div class="skills-grid">
      {#each skills as skill}
        <div class="skill-item" in:scale={{ duration: 500, delay: 100 }}>
          <div class="skill-header">
            <span class="skill-name">{skill}</span>
          </div>
          <div class="skill-bar">
            <div class="skill-progress" style="width: 100%"></div>
          </div>
        </div>
      {/each}
    </div>
  </div>
</section>

<section id="projects" class="projects">
  <div class="container">
    <h2 class="section-title">Featured Projects</h2>
    <div class="projects-grid">
      {#each projects as project, i}
        <div class="project-card" in:fly={{ x: -30, duration: 600, delay: i * 150 }}>
          <div class="project-header">
            <h3>{project.title}</h3>
            <a href={project.link} class="project-link" aria-label="Visit {project.title} project">
              <i class="fas fa-external-link-alt"></i>
            </a>
          </div>
          <p class="project-description">{project.description}</p>
          <div class="project-tech">
            {#each project.tech as tech}
              <span class="tech-tag">{tech}</span>
            {/each}
          </div>
        </div>
      {/each}
    </div>
  </div>
</section>

<section id="contact" class="contact">
  <div class="container">
    <h2 class="section-title">Get In Touch</h2>
    <p class="contact-subtitle">Feel free to reach out if you want to connect.</p>
    <div class="social-links">
      {#each socialLinks as link}
        <a href={link.url} class="social-link" target="_blank" rel="noopener noreferrer" aria-label="social link" style="text-decoration: none">
          <i class={link.icon}></i>
        </a>
      {/each}
    </div>
  </div>
</section>

<style>
  :global(body) {
    margin: 0;
    padding: 0;
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, sans-serif;
    background-color: #0a0a0a;
    color: #ffffff;
    overflow-x: hidden;
  }

  .navbar {
    position: fixed;
    top: 0;
    width: 100%;
    background: rgba(10, 10, 10, 0.95);
    backdrop-filter: blur(10px);
    z-index: 1000;
    padding: 1rem 0;
    border-bottom: 1px solid rgba(255, 255, 255, 0.1);
  }

  .nav-container {
    max-width: 1200px;
    margin: 0 auto;
    padding: 0 2rem;
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  .nav-brand {
    font-size: 1.5rem;
    font-weight: 700;
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    -webkit-background-clip: text;
    background-clip: text;
    -webkit-text-fill-color: transparent;
  }

  .nav-menu {
    display: flex;
    list-style: none;
    gap: 2rem;
    margin: 0;
    padding: 0;
  }

  .nav-menu button {
    background: none;
    border: none;
    color: #ffffff;
    cursor: pointer;
    font-size: 1rem;
    transition: all 0.3s ease;
    position: relative;
  }

  .nav-menu button:hover {
    color: #667eea;
  }

  .nav-menu button.active {
    color: #667eea;
  }

  .nav-menu button.active::after {
    content: '';
    position: absolute;
    bottom: -5px;
    left: 0;
    width: 100%;
    height: 2px;
    background: #667eea;
  }

  .hero {
    min-height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
    background: radial-gradient(ellipse at center, #1a1a2e 0%, #0a0a0a 100%);
    position: relative;
    overflow: hidden;
  }

  .hero::before {
    content: '';
    position: absolute;
    width: 200%;
    height: 200%;
    background: url("data:image/svg+xml,%3Csvg width='60' height='60' viewBox='0 0 60 60' xmlns='http://www.w3.org/2000/svg'%3E%3Cg fill='none' fill-rule='evenodd'%3E%3Cg fill='%23667eea' fill-opacity='0.05'%3E%3Cpath d='M36 34v-4h-2v4h-4v2h4v4h2v-4h4v-2h-4zm0-30V0h-2v4h-4v2h4v4h2V6h4V4h-4zM6 34v-4H4v4H0v2h4v4h2v-4h4v-2H6zM6 4V0H4v4H0v2h4v4h2V6h4V4H6z'/%3E%3C/g%3E%3C/g%3E%3C/svg%3E");
    animation: float 20s infinite linear;
  }

  @keyframes float {
    0% { transform: translate(-50%, -50%) rotate(0deg); }
    100% { transform: translate(-50%, -50%) rotate(360deg); }
  }

  .hero-content {
    text-align: center;
    z-index: 1;
    padding: 0 2rem;
  }

  .hero-title {
    font-size: 4rem;
    font-weight: 700;
    margin-bottom: 1rem;
    line-height: 1.2;
  }

  .accent {
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    -webkit-background-clip: text;
    background-clip: text;
    -webkit-text-fill-color: transparent;
  }

  .hero-subtitle {
    font-size: 1.5rem;
    color: #a0a0a0;
    margin-bottom: 2rem;
  }

  .hero-buttons {
    display: flex;
    gap: 1rem;
    justify-content: center;
  }

  .btn {
    padding: 0.75rem 2rem;
    border: none;
    border-radius: 50px;
    font-size: 1rem;
    font-weight: 600;
    cursor: pointer;
    transition: all 0.3s ease;
    text-decoration: none;
    display: inline-block;
  }

  .btn-primary {
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    color: white;
  }

  .btn-primary:hover {
    transform: translateY(-2px);
    box-shadow: 0 10px 20px rgba(102, 126, 234, 0.3);
  }

  .btn-secondary {
    background: transparent;
    color: #667eea;
    border: 2px solid #667eea;
  }

  .btn-secondary:hover {
    background: #667eea;
    color: white;
  }

  section {
    padding: 5rem 0;
  }

  .container {
    max-width: 1200px;
    margin: 0 auto;
    padding: 0 2rem;
  }

  .section-title {
    font-size: 2.5rem;
    text-align: center;
    margin-bottom: 3rem;
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    -webkit-background-clip: text;
    background-clip: text;
    -webkit-text-fill-color: transparent;
  }

  .about {
    background: #0f0f0f;
  }

  .about-content {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 4rem;
    align-items: center;
  }

  .about-text p {
    font-size: 1.1rem;
    line-height: 1.8;
    color: #a0a0a0;
    margin-bottom: 1rem;
  }

  .image-placeholder {
    width: 300px;
    height: 300px;
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    border-radius: 20px;
    display: flex;
    align-items: center;
    justify-content: center;
    margin: 0 auto;
  }

  .about-image {
  display: flex;
  justify-content: center;
  align-items: center;
}

.about-image img {
  width: 300px;
  height: 300px;
  border-radius: 20px;
  object-fit: cover;
  box-shadow: 0 20px 40px rgba(0, 0, 0, 0.3);
  border: 3px solid rgba(102, 126, 234, 0.3);
  transition: all 0.3s ease;
}

.about-image img:hover {
  transform: scale(1.05);
  border-color: #667eea;
  box-shadow: 0 25px 50px rgba(102, 126, 234, 0.3);
}



/* Optional: Add a gradient overlay effect */
.about-image {
  position: relative;
}

.about-image::after {
  content: '';
  position: absolute;
  top: 0;
  left: 50%;
  transform: translateX(-50%);
  width: 300px;
  height: 300px;
  border-radius: 20px;
  background: linear-gradient(135deg, rgba(102, 126, 234, 0.1) 0%, rgba(118, 75, 162, 0.1) 100%);
  pointer-events: none;
  transition: opacity 0.3s ease;
}

.about-image:hover::after {
  opacity: 0;
}

/* Responsive */
@media (max-width: 768px) {
  .about-image img {
    width: 250px;
    height: 250px;
  }
  
  .about-image::after {
    width: 250px;
    height: 250px;
  }
}

  .projects {
    background: #0f0f0f;
  }

  .projects-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
    gap: 2rem;
  }

  .project-card {
    background: #1a1a1a;
    padding: 2rem;
    border-radius: 10px;
    border: 1px solid rgba(255, 255, 255, 0.1);
    transition: all 0.3s ease;
  }

  .project-card:hover {
    transform: translateY(-5px);
    border-color: #667eea;
    box-shadow: 0 10px 30px rgba(102, 126, 234, 0.2);
  }

  .project-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 1rem;
  }

  .project-header h3 {
    margin: 0;
    font-size: 1.5rem;
  }

  .project-link {
    color: #667eea;
    font-size: 1.2rem;
    transition: transform 0.3s ease;
  }

  .project-link:hover {
    transform: scale(1.2);
  }

  .project-description {
    color: #a0a0a0;
    margin-bottom: 1.5rem;
    line-height: 1.6;
  }

  .project-tech {
    display: flex;
    flex-wrap: wrap;
    gap: 0.5rem;
  }

  .tech-tag {
    background: rgba(102, 126, 234, 0.2);
    color: #667eea;
    padding: 0.25rem 0.75rem;
    border-radius: 20px;
    font-size: 0.875rem;
  }

  .contact {
    text-align: center;
  }

  .contact-subtitle {
    font-size: 1.2rem;
    color: #a0a0a0;
    margin-bottom: 2rem;
  }

  .social-links {
    display: flex;
    justify-content: center;
    gap: 2rem;
  }

  .social-link {
    width: 50px;
    height: 50px;
    background: #1a1a1a;
    border: 2px solid rgba(255, 255, 255, 0.1);
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    color: #ffffff;
    font-size: 1.5rem;
    transition: all 0.3s ease;
  }

  .social-link:hover {
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    border-color: transparent;
    transform: translateY(-3px);
  }

  @media (max-width: 768px) {
    .nav-menu {
      gap: 1rem;
      font-size: 0.9rem;
    }

    .hero-title {
      font-size: 2.5rem;
    }

    .hero-subtitle {
      font-size: 1.2rem;
    }

    .hero-buttons {
      flex-direction: column;
      align-items: center;
    }

    .about-content {
      grid-template-columns: 1fr;
      text-align: center;
    }

    .projects-grid {
      grid-template-columns: 1fr;
    }
  }

  /* Skills Section */
  .skills-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 2rem;
  }

  .skill-item {
    background: #1a1a1a;
    padding: 1.5rem;
    border-radius: 10px;
    border: 1px solid rgba(255, 255, 255, 0.1);
  }

  .skill-header {
    display: flex;
    justify-content: space-between;
    margin-bottom: 0.5rem;
  }

  .skill-name {
    font-weight: 600;
  }

  .skill-percentage {
    color: #667eea;
  }

  .skill-bar {
    width: 100%;
    height: 8px;
    background: #2a2a2a;
    border-radius: 4px;
    overflow: hidden;
  }

  .skill-progress {
    height: 100%;
    background: linear-gradient(90deg, #667eea 0%, #764ba2 100%);
    border-radius: 4px;
    transition: width 1s ease;
  }

</style>