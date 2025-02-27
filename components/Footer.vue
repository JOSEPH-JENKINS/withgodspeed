<template>
  <div class="footer container-grid">
    <h2 class="header animate-text">
      SEND US THREE MONTHS OF DATA AND WE'LL SHOW YOU ACTIONABLE STEPS TO
      IMPROVE YOUR MARKETING.
    </h2>
    <span class="cta animate-text" id="leadFormOpen">Enter details</span>
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
        type="url"
        name="Company"
        id="company"
        placeholder="Type in your company website link. ex- https://company.com"
        required
      />
      <input
        type="url"
        name="M.Data"
        id="marketing"
        placeholder="Link to your 3 months marketing data"
        required
      />

      <button type="submit" class="form-submit">Submit details</button>
    </form>
    <h1 class="lead-success-message disappear">
      Data sent: Thanks for the info. if you check your inbox, you should have
      an email from us.
    </h1>
    <nav class="links">
      <ul>
        <li>
          <NuxtLink
            to="https://instagram.com/amjosephjenkins"
            class="animate-text"
            >Instagram</NuxtLink
          >
        </li>
        <li><NuxtLink to="" class="animate-text">Linkedin</NuxtLink></li>
        <li>
          <a href="mailto:jenkins@withgodspeed.com" class="animate-text"
            >Email Jenkins</a
          >
        </li>
        <li>
          <NuxtLink
            to="https://calendar.app.google/fsvtvReGv3qrMGyg7"
            class="animate-text"
            >Calendar</NuxtLink
          >
        </li>
      </ul>
    </nav>
  </div>
</template>

<script setup>
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
</script>
