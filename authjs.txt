document.addEventListener('DOMContentLoaded', function() {

  // Toggle between Sign In and Sign Up
  const signinToggle = document.getElementById("signin-toggle");
  const signupToggle = document.getElementById("signup-toggle");
  const signinFormContainer = document.getElementById("signin-form-container");
  const signupFormContainer = document.getElementById("signup-form-container");

  if (signinToggle && signupToggle && signinFormContainer && signupFormContainer) {

    signinToggle.addEventListener("click", () => {
      signinToggle.classList.add("active");
      signupToggle.classList.remove("active");
      signinFormContainer.classList.remove("hidden");
      signupFormContainer.classList.add("hidden");
    });

    signupToggle.addEventListener("click", () => {
      signupToggle.classList.add("active");
      signinToggle.classList.remove("active");
      signupFormContainer.classList.remove("hidden");
      signinFormContainer.classList.add("hidden");
    });

  } else {
    console.error("Elements missing");
  }
});

// SIGN IN FORM
document.getElementById("signin-form").addEventListener("submit", (e) => {
  e.preventDefault();

  const email = document.getElementById("signin-email").value.trim();
  const password = document.getElementById("signin-password").value;

  if (!email || !password) {
    alert("Please fill in all fields.");
    return;
  }

  alert("Signing in...");
  window.location.href = "index.html";
});

// SIGN UP FORM
document.getElementById("signup-form").addEventListener("submit", (e) => {
  e.preventDefault();

  const name = document.getElementById("signup-name").value.trim();
  const email = document.getElementById("signup-email").value.trim();
  const password = document.getElementById("signup-password").value;
  const confirmPassword = document.getElementById("signup-confirm-password").value;
  const terms = document.getElementById("terms").checked;

  if (!name || !email || !password || !confirmPassword) {
    alert("Please fill in all fields.");
    return;
  }

  if (password !== confirmPassword) {
    alert("Passwords do not match!");
    return;
  }

  if (!terms) {
    alert("You must accept the Terms.");
    return;
  }

  alert("Account created!");
  window.location.href = "index.html";
});
