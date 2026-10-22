
document.addEventListener("DOMContentLoaded", () => {

  // =====================================
  // 1. MENU MOBILE
  // =====================================

  const menuToggle = document.querySelector(".menu-toggle");
  const nav = document.querySelector("#nav-menu");
  const navLinks = document.querySelectorAll("#nav-menu a");

  function closeMenu() {
    if (!menuToggle || !nav) return;

    nav.classList.remove("open");
    menuToggle.setAttribute("aria-expanded", "false");
    menuToggle.setAttribute("aria-label", "Ouvrir le menu");

    const icon = menuToggle.querySelector(".menu-icon");

    if (icon) {
      icon.textContent = "☰";
    }
  }

  if (menuToggle && nav) {
    menuToggle.addEventListener("click", () => {
      const isOpen = nav.classList.toggle("open");

      menuToggle.setAttribute("aria-expanded", String(isOpen));
      menuToggle.setAttribute(
        "aria-label",
        isOpen ? "Fermer le menu" : "Ouvrir le menu"
      );

      const icon = menuToggle.querySelector(".menu-icon");

      if (icon) {
        icon.textContent = isOpen ? "✕" : "☰";
      }
    });

    // Fermer le menu après sélection d'une section
    navLinks.forEach((link) => {
      link.addEventListener("click", closeMenu);
    });

    // Fermer le menu avec la touche Échap
    document.addEventListener("keydown", (event) => {
      if (event.key === "Escape") {
        closeMenu();
      }
    });

    // Fermer le menu lorsqu'on repasse en grand écran
    window.addEventListener("resize", () => {
      if (window.innerWidth > 700) {
        closeMenu();
      }
    });
  }


  // =====================================
  // 2. ANIMATIONS AU DÉFILEMENT
  // =====================================

  const revealElements = document.querySelectorAll(".reveal");

  const prefersReducedMotion = window.matchMedia(
    "(prefers-reduced-motion: reduce)"
  ).matches;

  if ("IntersectionObserver" in window && !prefersReducedMotion) {

    const revealObserver = new IntersectionObserver(
      (entries, observer) => {
        entries.forEach((entry) => {
          if (entry.isIntersecting) {
            entry.target.classList.add("visible");
            observer.unobserve(entry.target);
          }
        });
      },
      {
        threshold: 0.12,
        rootMargin: "0px 0px -30px 0px"
      }
    );

    revealElements.forEach((element) => {
      revealObserver.observe(element);
    });

  } else {

    // Afficher immédiatement les éléments si nécessaire
    revealElements.forEach((element) => {
      element.classList.add("visible");
    });
  }


  // =====================================
  // 3. ANNÉE AUTOMATIQUE DU FOOTER
  // =====================================

  const yearElement = document.querySelector("#year");

  if (yearElement) {
    yearElement.textContent = new Date().getFullYear();
  }


  // =====================================
  // 4. PHOTO DE PROFIL GITHUB
  // =====================================

  const profilePhoto = document.querySelector(
    "[data-profile-photo]"
  );

  const portraitFallback = document.querySelector(
    ".portrait-fallback"
  );

  if (profilePhoto && portraitFallback) {

    function showFallback() {
      profilePhoto.hidden = true;
      portraitFallback.hidden = false;
    }

    function showPhoto() {
      profilePhoto.hidden = false;
      portraitFallback.hidden = true;
    }

    profilePhoto.addEventListener("load", showPhoto);
    profilePhoto.addEventListener("error", showFallback);

    // Vérifier si le navigateur a déjà chargé l'image
    if (profilePhoto.complete) {
      if (profilePhoto.naturalWidth > 0) {
        showPhoto();
      } else {
        showFallback();
      }
    }
  }


  // =====================================
  // 5. LIEN ACTIF DU MENU
  // =====================================

  const sections = document.querySelectorAll(
    "main section[id]"
  );

  if ("IntersectionObserver" in window && sections.length > 0) {

    const sectionObserver = new IntersectionObserver(
      (entries) => {
        entries.forEach((entry) => {
          if (!entry.isIntersecting) return;

          const currentId = entry.target.id;

          navLinks.forEach((link) => {
            const isActive =
              link.getAttribute("href") === `#${currentId}`;

            link.classList.toggle("active", isActive);
          });
        });
      },
      {
        rootMargin: "-30% 0px -60% 0px",
        threshold: 0
      }
    );

    sections.forEach((section) => {
      sectionObserver.observe(section);
    });
  }


  // =====================================
  // 6. ACCESSIBILITÉ DES LIENS E-MAIL
  // =====================================

  const emailLinks = document.querySelectorAll(
    'a[href^="mailto:"]'
  );

  emailLinks.forEach((link) => {
    link.setAttribute(
      "aria-label",
      "Envoyer un e-mail à Aya"
    );
  });

});
