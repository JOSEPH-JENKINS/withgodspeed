<template>
  <div class="footer container-grid">
    <h1 class="animate-text">
      Built with AI to give you back hours, not take them
    </h1>
    <p class="header animate-text">
      Want to see how it works? Tap below for a live walkthrough. We'll show you
      the exact system and where you're leaking clients right now.
    </p>
    <NuxtLink
      to="https://calendar.app.google/fsvtvReGv3qrMGyg7"
      class="animate-text"
      >See the live demo</NuxtLink
    >
    <NuxtLink
      to="https://docs.google.com/forms/d/e/1FAIpQLSdSlUg0RbCnO_EPdMxCrIzAgWuSLglzkh7ACjsg3ljDV1W-tg/viewform?usp=header"
      class="animate-text"
      >Or see if your spa qualifies for the Godspeed system.</NuxtLink
    >
    <!-- <h2 class="header animate-text">
      Join now. Drop your email, phone number and get the one Simple Growth Plan
      the best brands use to break through.
    </h2>
    <button class="cta animate-text" id="leadFormOpen">Enter details</button>
    <form
      method="POST"
      action="https://script.google.com/macros/s/AKfycbyw0kfMiXezbBa5dZ4jTfLepYxD0XIdYq_Ap6kHwnaqrDIt1NF-MErew2KcZUnvBE_L/exec"
      class="lead-form"
      id="leadForm"
    >
      <input
        type="text"
        name="Name"
        id="name"
        placeholder="Type in your name"
        required
      />
      <input
        type="tel"
        name="Phone Number"
        id="phone"
        placeholder="Type in your phone number (with country code)"
        required
      />
      <input
        type="email"
        name="Email"
        id="email"
        placeholder="Type in your email"
        required
        autocomplete="email"
      />
      <input
        type="text"
        name="Company"
        id="company"
        placeholder="Type in your company"
        required
      />

      <button type="submit" class="form-submit">Submit details</button>
    </form>
    <h1 class="lead-success-message disappear">
      You're In. <br />

      Most brands stay stuck because they try to figure it all out alone.<br />
      You won't be one of them.<br />

      I just sent the community link to your inbox. Check it now.<br />
      This is where founders break through.<br />

      Welcome to Godspeed. — Jenkins
    </h1> -->
    <nav class="links">
      <ul>
        <li>
          <NuxtLink
            to="https://instagram.com/withgodspeedd"
            class="animate-text"
            >Instagram</NuxtLink
          >
        </li>
        <li>
          <NuxtLink to="https://x.com/withgodspeedd" class="animate-text"
            >Twitter/X</NuxtLink
          >
        </li>
        <li>
          <a href="mailto:jenkins@withgodspeed.com" class="animate-text"
            >Email Jenkins</a
          >
        </li>
        <li>
          <NuxtLink
            to="https://calendar.app.google/fsvtvReGv3qrMGyg7"
            class="animate-text"
            >Live Demo</NuxtLink
          >
        </li>
      </ul>
    </nav>
  </div>
</template>

<!-- <script setup>
import { onMounted } from "vue";

onMounted(() => {
  const leadOpenFormButton = document.querySelector("#leadFormOpen");
  const leadForm = document.querySelector("#leadForm");
  const leadSuccessMessage = document.querySelector(".lead-success-message");

  leadOpenFormButton.addEventListener("click", function (e) {
    leadForm.classList.remove("lead-form");
  });

  if (localStorage.getItem("leadForm")) {
    leadForm.classList.add("lead-form");
    leadOpenFormButton.style.display = "none";
    leadSuccessMessage.classList.remove("disappear");
  }

  leadForm.addEventListener("submit", async function (e) {
    e.preventDefault();
    const formdata = new FormData(leadForm);
    const action = e.target.action;

    const { data, status, error, refresh } = await useFetch(action, {
      method: "POST",
      body: formdata,
    });

    if (data) {
      localStorage.setItem("leadForm", true);

      leadForm.classList.add("lead-form");
      leadOpenFormButton.style.display = "none";
      leadSuccessMessage.classList.remove("disappear");
    } else {
      console.error(error);
    }
  });
});
</script> -->
