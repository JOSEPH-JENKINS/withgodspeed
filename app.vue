<template>
  <div class="layout-grid container-spacing">
    <NuxtPage />
    <Footer />
    <Analytics />
  </div>
</template>

<script setup>
import { onMounted } from "vue";
import { Analytics } from "@vercel/analytics/nuxt";

useSeoMeta({
  title:
    "Godspeed — The Booking Engine Behind Med Spa Brands Clients Obsess Over",
  ogTitle:
    "Godspeed — The Booking Engine Behind Med Spa Brands Clients Obsess Over.",
  description:
    "We help med spas book 30+ clients/month using AI-powered systems that boost bookings, build brand loyalty, and eliminate $20K+ in lost revenue.",
  ogDescription:
    "We help med spas book 30+ clients/month using AI-powered systems that boost bookings, build brand loyalty, and eliminate $20K+ in lost revenue.",
  twitterCard: "summary_large_image",
  twitterTitle:
    "Godspeed — The Booking Engine Behind Med Spa Brands Clients Obsess Over",
  twitterDescription:
    "We help med spas book 30+ clients/month using AI-powered systems that boost bookings, build brand loyalty, and eliminate $20K+ in lost revenue.",
  ogUrl: "https://www.withgodspeed.com",
});

onMounted(() => {
  const textElements = document.querySelectorAll(".animate-text");
  const characters =
    "ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789";
  const animationDuration = 2000;
  const frameRate = 50;
  const totalFrames = animationDuration / frameRate;

  function extractTextNodesWithBr(element) {
    const nodes = [];
    function recurse(node) {
      if (node.nodeType === Node.TEXT_NODE && node.nodeValue.trim() !== "") {
        nodes.push({ type: "text", node });
      } else if (node.nodeType === Node.ELEMENT_NODE) {
        if (node.tagName === "BR") {
          nodes.push({ type: "br", node });
        } else {
          node.childNodes.forEach(recurse);
        }
      }
    }
    recurse(element);
    return nodes;
  }

  function shuffleText(element, frames) {
    const nodes = extractTextNodesWithBr(element);
    const finalTexts = nodes.map((item) =>
      item.type === "text" ? item.node.nodeValue : null
    );
    let currentFrame = 0;
    let resolvedIndices = new Set();

    const interval = setInterval(() => {
      nodes.forEach((item, nodeIndex) => {
        if (item.type !== "text") return;
        const finalChars = finalTexts[nodeIndex].split("");
        let currentText = finalChars
          .map((char, i) => {
            if (resolvedIndices.has(`${nodeIndex}-${i}`)) return finalChars[i];
            if (currentFrame >= frames - i * 2) {
              resolvedIndices.add(`${nodeIndex}-${i}`);
              return finalChars[i];
            }
            return characters[Math.floor(Math.random() * characters.length)];
          })
          .join("");
        item.node.nodeValue = currentText;
      });
      currentFrame++;
      if (
        resolvedIndices.size ===
        finalTexts.reduce((acc, txt) => acc + (txt ? txt.length : 0), 0)
      )
        clearInterval(interval);
    }, frameRate);
  }

  textElements.forEach((element) => {
    shuffleText(element, totalFrames);
  });
});
</script>
