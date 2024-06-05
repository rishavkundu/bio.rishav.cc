<template>
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
        <a
          href="https://rishavkundu.com"
          target="_blank"
          class="h-12 flex items-center space-x-2 px-4 border-r text-xs font-medium bg-white text-slate-700"
        >
          <span> Github </span>
          <icon name="mdi:github" class="h-4 w-4" />
        </a>
      </div>
    </div>
    <app-form-preview :data="data" />
    <a
      href="https://twitter.com/rishavvk"
      target="_blank"
      class="absolute bottom-0 right-0 bg-white rounded-tl-lg shadow px-4 py-1 font-medium text-sm text-gray-500"
    >
      Made by Rishav
    </a>
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
    n: "Sir Charlie 'Eleanor' Whiskers",
    d: "A distinguished feline of leisure, with a penchant for fine cheeses and solving mysteries.  Those whiskers might be fluffy, but this cat's mind is sharp as his claws.",
    i: "https://images.unsplash.com/photo-1543466835-00a7904e90c3?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=870&q=80", //  (Replace with a fun cat picture!)
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
