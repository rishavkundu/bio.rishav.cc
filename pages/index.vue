<template>
  <link rel="icon" href="<%= BASE_URL %>favicon.ico">
  <div class="h-screen grid grid-cols-3 divide-x">
    <div class="col-span-2 h-screen flex flex-col bg-slate-100">
      <div class="flex-1 overflow-y-auto p-8">
        <app-form-profile
          v-model:name="data.n"
          v-model:desc="data.d"
          v-model:image="data.i"
        />
        <app-form-hr />
        <app-form-social-links
          v-model:facebook="data.f"
          v-model:twitter="data.t"
          v-model:instagram="data.ig"
          v-model:github="data.gh"
          v-model:telegram="data.tg"
          v-model:linkedin="data.l"
          v-model:email="data.e"
          v-model:whatsapp="data.w"
          v-model:youtube="data.y"
        />
        <app-form-hr />
        <app-form-links v-model="data.ls" />
      </div>
      <div class="border-t bg-white flex items-center">
        <button
          @click="prefillDemoData"
          class="h-12 flex items-center space-x-2 px-4 border-r text-xs font-medium bg-white text-slate-700"
        >
          <span> Add demo data </span>
          <icon name="mdi:code-json" class="h-4 w-4" />
        </button>
        <button
          @click="publish"
          class="h-12 flex items-center space-x-2 px-4 border-r text-xs font-medium bg-white text-slate-700"
        >
          <span> Publish </span>
          <icon name="ph:paper-plane-tilt-bold" class="h-4 w-4" />
        </button>
      </div>
    </div>
    <app-form-preview :data="data" />
    <a
  href="https://rishavkundu.com"
  target="_blank"
  class="absolute bottom-0 right-0 bg-white rounded-tl-lg shadow px-4 py-1 font-medium text-sm text-gray-500 flex items-center"
>
  Made with
  <svg
    class="heart-icon mx-1"
    xmlns="http://www.w3.org/2000/svg"
    viewBox="0 0 24 24"
    fill="red"
    width="16px"
    height="16px"
  >
    <path d="M12 21.35l-1.45-1.32C5.4 15.36 2 12.28 2 8.5 2 5.42 4.42 3 7.5 3c1.74 0 3.41 1.01 4.5 2.09C13.09 4.01 14.76 3 16.5 3 19.58 3 22 5.42 22 8.5c0 3.78-3.4 6.86-8.55 11.54L12 21.35z" />
  </svg>
  by Rishav Kundu
</a>

<style>
  .heart-icon {
    animation: pulse 1.5s infinite;
  }

  @keyframes pulse {
    0% {
      transform: scale(1);
    }
    50% {
      transform: scale(1.1);
    }
    100% {
      transform: scale(1);
    }
  }
</style>

  </div>
</template>

<script setup>
import { encodeData } from "../utils/transformer";
const data = ref({
  n: "",
  d: "",
  i: "",
  f: "",
  t: "",
  ig: "",
  gh: "",
  tg: "",
  l: "",
  e: "",
  w: "",
  y: "",
  ls: [],
});

const prefillDemoData = () => {
  data.value = {
    n: "Sir King Charles",
    d: "A distinguished feline of leisure, with a penchant for fine cheeses and solving mysteries.  Those whiskers might be fluffy, but this cat's mind is sharp as his claws.",
    i: "https://plain.rishavkundu.com/data/img/charlie.png",
    f: "https://www.facebook.com/SirCharlie",
    t: "https://twitter.com/kingcharles",
    ig: "https://www.instagram.com/kingcharles",
    e: "ckingcharlie@purrfectmail.com",
    gh: "https://github.com/rishavkundu",
    tg: "https://t.me/CharlieTheCat",
    w: "+1 (555) BIG-MEOW",
    y: "https://youtube.com/channel/kingcharles",
    l: "https://www.linkedin.com/kingcharles",
    ls: [
      {
        l: "My Meow-gical Blog",
        i: "ph:globe-duotone",
        u: "https://charlie_whiskers.blogspot.com",
      },
      {
        l: "My Amazon Wishlist (Catnip Required)",
        i: "ant-design:amazon-outlined",
        u: "https://amzn.to/CatnipForCharlie",
      },
      {
        l: "My Guide to Being a Purrfectly Lazy Cat",
        i: "ph:book-open",
        u: "https://www.kingcharles.com/lazinessguide",
      },
      {
        l: "Donate to the Cat Shelter (They Need Help!)",
        i: "iconoir:donate",
        u: "https://www.localcatshelter.org",
      },
      {
        l: "My Resume (Don't Judge, I'm a Cat)",
        i: "ph:file-pdf",
        u: "https://www.kingcharles.com/resume",
      },
    ],
  };
};

const publish = () => {
  const url = `${window.location.origin}/1?data=${encodeData(data.value)}`;
  navigator.clipboard.writeText(url).then(() => {
    alert("Link copied to clipboard");
  });
};
</script>
