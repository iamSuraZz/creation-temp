<template>
  <ClientOnly>
    <div class="w-full relative">
      <NuxtPage></NuxtPage>
      <A-Header></A-Header>
    </div>
  </ClientOnly>
</template>

<script setup>
import gsap from "gsap";
import Lenis from "@studio-freight/lenis";
import { ScrollTrigger } from "gsap/ScrollTrigger";
import { useRoute } from "vue-router";
gsap.registerPlugin(ScrollTrigger);
//#TODO add image moving animation to the the second section

// useHead({
//   title: "Creation Furnishings | Premium Curtains & Upholstery in India",
//   meta: [
//     {
//       name: "description",
//       content:
//         "Discover high-quality curtains and upholstery at Creation Furnishings. Explore blackout, sheer, and embroidered curtains, along with premium upholstery fabrics. Serving Hyderabad and all over India.",
//     },
//   ],
// });

const route = useRoute();

watch(
  () => route.name,
  (newName) => {
    console.log("this is " + newName);

    let pageTitle =
      "Creation Furnishings | Premium Curtains & Upholstery in India";
    let pageContent =
      "Discover high-quality curtains and upholstery at Creation Furnishings. Explore blackout, sheer, and embroidered curtains, along with premium upholstery fabrics. Serving Hyderabad and all over India.";
    if (newName === "curtains-blackout") {
      pageTitle =
        "Blackout Curtains Online | High-Quality Blackout Curtains India";
      pageContent =
        "Buy blackout curtains online at Creation Furnishings. Perfect for blocking out light and enhancing privacy. Available in Hyderabad and all over India.";
    } else if (newName === "curtains-digital-prints") {
      pageTitle = "Digital Print Curtains | Stylish Curtains Online India";
      pageContent =
        "Explore stylish digital print curtains at Creation Furnishings. Enhance your home decor with vibrant prints. Available in Hyderabad and all over India.";
    } else if (newName === "curtains-embroidery") {
      pageTitle =
        "Embroidery Curtains Online | Elegant Embroidered Curtains India";
      pageContent =
        "Shop elegant embroidered curtains at Creation Furnishings. Perfect for adding a touch of luxury to your home. Serving Hyderabad and all over India.";
    } else if (newName === "curtains-jackquard") {
      pageTitle = "Jackquard Curtains Online | Premium Jacquard Curtains India";
      pageContent =
        "Discover premium Jacquard curtains at Creation Furnishings. Stylish and durable options for your home. Available in Hyderabad and all over India.";
    } else if (newName === "curtains-sheers") {
      pageTitle = "Sheer Curtains Online | Light and Airy Sheer Curtains India";
      pageContent =
        "Buy sheer curtains online at Creation Furnishings. Perfect for a light and airy feel in your home. Available in Hyderabad and all over India.";
    } else if (newName === "curtains-textures") {
      pageTitle =
        "Textured Curtains Online | High-Quality Textured Curtains India";
      pageContent =
        "Shop high-quality textured curtains at Creation Furnishings. Enhance your home decor with unique textures. Available in Hyderabad and all over India.";
    } else if (newName === "curtains-wilder") {
      pageTitle = "Wilder Curtains Online | Stylish Wilder Curtains India";
      pageContent =
        "Explore stylish wilder curtains at Creation Furnishings. Unique designs to elevate your home decor. Available in Hyderabad and all over India.";
    } else if (newName === "upholstery-design") {
      pageTitle = "Designer Upholstery Fabrics | Stylish Upholstery India";
      pageContent =
        "Shop designer upholstery fabrics at Creation Furnishings. Perfect for stylish and unique furniture. Available in Hyderabad and all over India.";
    } else if (newName === "upholstery-rexin") {
      pageTitle = "Rexin Upholstery Fabrics | Durable Rexin Materials India";
      pageContent =
        "Buy durable rexin upholstery fabrics at Creation Furnishings. Ideal for long-lasting furniture. Available in Hyderabad and all over India.";
    } else if (newName === "upholstery-texture") {
      pageTitle =
        "Textured Upholstery Fabrics | Quality Textured Materials India";
      pageContent =
        "Shop quality textured upholstery fabrics at Creation Furnishings. Enhance your furniture with unique textures. Available in Hyderabad and all over India.";
    } else if (newName === "upholstery-suede") {
      pageTitle = "Suede Upholstery Fabrics | Luxurious Suede Materials India";
      pageContent =
        "Discover luxurious suede upholstery fabrics at Creation Furnishings. Perfect for elegant furniture. Available in Hyderabad and all over India.";
    } else if (newName === "upholstery-plain") {
      pageTitle =
        "Plain Upholstery Fabrics | High-Quality Plain Materials India";
      pageContent =
        "Buy high-quality plain upholstery fabrics at Creation Furnishings. Simple and elegant options for your furniture. Available in Hyderabad and all over India.";
    }

    useHead({
      title: pageTitle,
      meta: [{ name: "description", content: pageContent }],
    });
  },
  { immediate: true }
);

onMounted(() => {
  const lenis = new Lenis({
    smooth: true,
  });

  lenis.on("scroll", ScrollTrigger.update);

  gsap.ticker.add((time) => {
    lenis.raf(time * 1000);
  });
  function raf(time) {
    lenis.raf(time);
    requestAnimationFrame(raf);
  }

  requestAnimationFrame(raf);
  //  // Google Analytics tracking code
  //  window.dataLayer = window.dataLayer || [];
  // function gtag(){dataLayer.push(arguments);}
  // gtag('js', new Date());
  // gtag('config', 'G-EHRG7XD53Z');
});
</script>
<!-- Google tag (gtag.js)
<script async src="https://www.googletagmanager.com/gtag/js?id=G-EHRG7XD53Z"></script>
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());

  gtag('config', 'G-EHRG7XD53Z');
</script> -->
<style>
* {
  box-sizing: border-box;
  padding: 0px;
  margin: 0px;
}

body,
html {
  width: 100%;
  font-family: "URW Gothic";
}

html.lenis {
  height: auto;
}

.page-enter-active,
.page-leave-active {
  transition: all 0.4s;
}

.page-enter-from,
.page-leave-to {
  opacity: 0;
  filter: blur(1rem);
}

.lenis.lenis-smooth {
  scroll-behavior: auto;
}

.lenis.lenis-smooth [data-lenis-prevent] {
  overscroll-behavior: contain;
}

.lenis.lenis-stopped {
  overflow: hidden;
}

.lenis.lenis-scrolling iframe {
  pointer-events: none;
}
</style>
