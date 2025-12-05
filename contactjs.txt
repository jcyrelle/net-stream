// SUBSCRIPTION POPUP
document.querySelector(".subscribe-btn").addEventListener("click", () => {
  document.getElementById("subscription-popup").style.display = "flex";
});

document.getElementById("close-popup").addEventListener("click", () => {
  document.getElementById("subscription-popup").style.display = "none";
});

// Plan Buttons
document.querySelectorAll(".choose-btn").forEach(btn => {
  btn.addEventListener("click", () => {
    alert("Thank you for choosing a plan! 🎉");
  });
});

// Close popup when clicking outside
document.getElementById("subscription-popup").addEventListener("click", (e) => {
  if (e.target.id === "subscription-popup") {
    document.getElementById("subscription-popup").style.display = "none";
  }
});

// CONTACT FORM SUBMISSION
document.getElementById("submit-btn").addEventListener("click", (e) => {
  e.preventDefault();
  
  // Get form values
  const firstName = document.getElementById("first-name").value.trim();
  const lastName = document.getElementById("last-name").value.trim();
  const email = document.getElementById("email").value.trim();
  const subject = document.getElementById("subject").value;
  const message = document.getElementById("message").value.trim();

  // Basic validation
  if (!firstName || !lastName || !email || !subject || !message) {
    alert("Please fill in all required fields.");
    return;
  }

  // Email validation
  const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
  if (!emailRegex.test(email)) {
    alert("Please enter a valid email address.");
    return;
  }

  // Show success message
  document.getElementById("success-message").style.display = "flex";

  // Clear form
  document.getElementById("first-name").value = "";
  document.getElementById("last-name").value = "";
  document.getElementById("email").value = "";
  document.getElementById("phone").value = "";
  document.getElementById("subject").value = "";
  document.getElementById("message").value = "";
});

// Close success message
document.getElementById("close-success").addEventListener("click", () => {
  document.getElementById("success-message").style.display = "none";
});

// FAQ ACCORDION
document.querySelectorAll(".faq-question").forEach(question => {
  question.addEventListener("click", () => {
    const faqItem = question.parentElement;
    const isActive = faqItem.classList.contains("active");

    // Close all FAQ items
    document.querySelectorAll(".faq-item").forEach(item => {
      item.classList.remove("active");
    });

    // Toggle current item
    if (!isActive) {
      faqItem.classList.add("active");
    }
  });
});

// LIVE CHAT BUTTON
document.querySelector(".chat-btn").addEventListener("click", () => {
  alert("Live chat feature coming soon! 💬\n\nFor now, please use the contact form or email us at support@netstream.com");
});

// SMOOTH SCROLL ANIMATIONS
const observerOptions = {
  threshold: 0.1,
  rootMargin: "0px 0px -50px 0px"
};

const observer = new IntersectionObserver((entries) => {
  entries.forEach(entry => {
    if (entry.isIntersecting) {
      entry.target.style.animation = "fadeInUp 0.8s ease-out forwards";
      observer.unobserve(entry.target);
    }
  });
}, observerOptions);

// Observe elements for animation
document.querySelectorAll('.contact-form-wrapper, .contact-info-wrapper, .faq-container').forEach(el => {
  el.style.opacity = "0";
  observer.observe(el);
});