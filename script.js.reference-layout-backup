(() => {
  "use strict";

  const config = window.CLAUDE_GOTO_CONFIG || {};
  const owner = config.githubOwner || "YOUR_GITHUB_USERNAME";
  const repo = config.repository || "claude-go-to";
  const repositoryUrl = `https://github.com/${owner}/${repo}`;
  const root = document.documentElement;
  const themeButton = document.querySelector("#theme-toggle");
  const themeColor = document.querySelector('meta[name="theme-color"]');

  const setTheme = (theme, save = true) => {
    const light = theme === "light";
    root.dataset.theme = light ? "light" : "dark";
    if (themeButton) {
      themeButton.setAttribute("aria-pressed", String(light));
      themeButton.setAttribute("aria-label", light ? "Switch to dark theme" : "Switch to light theme");
      themeButton.querySelector(".theme-label").textContent = light ? "Light" : "Dark";
    }
    if (themeColor) themeColor.content = light ? "#f5f4ed" : "#0c1713";
    if (save) {
      try { localStorage.setItem("claude-go-to-theme", theme); } catch (_) { /* Storage can be unavailable in private contexts. */ }
    }
  };

  let savedTheme = null;
  try { savedTheme = localStorage.getItem("claude-go-to-theme"); } catch (_) { /* Use the device preference instead. */ }
  const prefersLight = window.matchMedia && window.matchMedia("(prefers-color-scheme: light)").matches;
  setTheme(savedTheme || (prefersLight ? "light" : "dark"), false);
  themeButton?.addEventListener("click", () => setTheme(root.dataset.theme === "light" ? "dark" : "light"));

  document.querySelectorAll("[data-github-link]").forEach((link) => { link.href = repositoryUrl; });

  const header = document.querySelector(".site-header");
  const updateHeader = () => header?.classList.toggle("is-scrolled", window.scrollY > 6);
  updateHeader();
  window.addEventListener("scroll", updateHeader, { passive: true });

  const menuButton = document.querySelector(".menu-toggle");
  const nav = document.querySelector("#site-nav");
  menuButton?.addEventListener("click", () => {
    const open = nav?.classList.toggle("is-open") || false;
    menuButton.setAttribute("aria-expanded", String(open));
  });
  nav?.querySelectorAll("a").forEach((link) => link.addEventListener("click", () => {
    nav.classList.remove("is-open");
    menuButton?.setAttribute("aria-expanded", "false");
  }));

  const paths = {
    beginner: {
      kicker: "Foundation path · about 90 minutes",
      title: "Make every session start with the right context.",
      text: "Begin with dependable prompts, then create one shared context file for your project. You will finish with a small workflow you can reuse tomorrow.",
      modules: ["01 Prompt playbooks", "02 Project context", "03 Reusable skills"]
    },
    intermediate: {
      kicker: "Practice path · about 3 hours",
      title: "Turn good habits into an intentional practice.",
      text: "Package repeated work into reusable skills, introduce focused quality gates, and add only the tool connections that reduce real uncertainty.",
      modules: ["03 Reusable skills", "05 Tool connections", "06 Quality gates", "07 Extensions"]
    },
    advanced: {
      kicker: "Systems path · about 5 hours",
      title: "Coordinate complex work without hiding decisions.",
      text: "Define specialist roles, create safe checkpoints, and connect every handoff into a delivery loop that the team can understand and improve.",
      modules: ["04 Specialist agents", "08 Checkpoints", "09 Delivery systems", "10 Command-line fluency"]
    }
  };
  const pathDetail = document.querySelector("#path-detail");
  const selectPath = (path) => {
    const content = paths[path] || paths.beginner;
    if (pathDetail) {
      pathDetail.innerHTML = `<p class="detail-kicker">${content.kicker}</p><h3>${content.title}</h3><p>${content.text}</p><div class="detail-modules">${content.modules.map((module) => `<span>${module}</span>`).join("")}</div>`;
    }
    document.querySelectorAll("[data-path]").forEach((button) => {
      const selected = button.dataset.path === path;
      button.classList.toggle("is-selected", selected);
      button.setAttribute("aria-selected", String(selected));
    });
  };
  document.querySelectorAll("[data-path]").forEach((button) => button.addEventListener("click", () => selectPath(button.dataset.path)));
  selectPath("beginner");

  const modules = [
    ["01", "Prompt playbooks", "Turn a reliable prompt into a fast, repeatable start.", "20 min"],
    ["02", "Project context", "Give every session the architecture and boundaries it needs.", "30 min"],
    ["03", "Reusable skills", "Package a useful method so strong work is easy to repeat.", "40 min"],
    ["04", "Specialist agents", "Split independent work among focused roles with clear handoffs.", "45 min"],
    ["05", "Tool connections", "Bring in the right source of truth with deliberate permissions.", "35 min"],
    ["06", "Quality gates", "Run the smallest useful check at the best possible moment.", "35 min"],
    ["07", "Extensions", "Bundle a team workflow into something people can adopt quickly.", "40 min"],
    ["08", "Checkpoints", "Create safe points for ambitious work and fast reversals.", "25 min"],
    ["09", "Delivery systems", "Connect roles and review steps into a dependable delivery loop.", "50 min"],
    ["10", "Command-line fluency", "Move efficiently while keeping your work visible and controlled.", "25 min"]
  ];
  const grid = document.querySelector("#module-grid");
  if (grid) {
    grid.innerHTML = modules.map(([number, title, description, duration]) => {
      const slug = title.toLowerCase().replaceAll(" ", "-");
      return `<article class="module-card"><div class="module-meta"><span>MODULE ${number}</span><time>${duration}</time></div><h3>${title}</h3><p>${description}</p><a href="guides/${number}-${slug}.md" aria-label="Open ${title} guide">Open ${title}</a></article>`;
    }).join("");
  }

  const assessment = document.querySelector("#assessment-form");
  const assessmentResult = document.querySelector("#assessment-result");
  assessment?.addEventListener("submit", (event) => {
    event.preventDefault();
    const answers = new FormData(assessment);
    const values = ["context", "repeat", "agents"].map((name) => answers.get(name));
    if (values.includes(null)) {
      if (assessmentResult) assessmentResult.textContent = "Choose one answer in each section to get a recommendation.";
      return;
    }
    const score = values.map(Number).reduce((total, value) => total + value, 0);
    const recommendation = score === 0
      ? "Start with Module 01: Prompt playbooks."
      : score < 3
        ? "Start with Module 03: Reusable skills."
        : "You are ready for Module 04: Specialist agents.";
    if (assessmentResult) assessmentResult.textContent = recommendation;
  });
})();
