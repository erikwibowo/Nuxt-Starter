<script setup lang="ts">
import { ref, onMounted, onUnmounted } from "vue";
import ColorSwitch from "~/components/color-switch.vue";
import type Button from "~/components/ui/button/Button.vue";

const navigation = [
  { name: "Product", href: "#" },
  { name: "Features", href: "#" },
  { name: "Marketplace", href: "#" },
  { name: "Company", href: "#" },
];

const mobileMenuOpen = ref(false);

const isFixed = ref(false);

const handleScroll = () => {
  if (window.scrollY > 100) {
    isFixed.value = true;
  } else {
    isFixed.value = false;
  }
};

onMounted(() => {
  window.addEventListener("scroll", handleScroll);
});

onUnmounted(() => {
  window.removeEventListener("scroll", handleScroll);
});
</script>
<template>
  <header
    v-bind:class="isFixed ? 'fixed bg-background/20 backdrop-blur border border-b-border' : 'absolute'"
    class="inset-x-0 top-0 z-50"
  >
    <nav
      class="flex items-center justify-between p-4 lg:px-8"
      aria-label="Global"
    >
      <div class="flex lg:flex-1">
        <a href="#" class="-m-1.5 p-1.5 flex gap-2 items-center">
          <img class="h-8 w-auto" src="/favicon.ico" alt="" />
          <h2 class="text-lg uppercase tracking-widest">Nuxt Starter</h2>
        </a>
      </div>
      <div class="flex lg:hidden">
        <button
          type="button"
          class="-m-2.5 inline-flex items-center justify-center rounded-md p-2.5 text-gray-700"
          @click="mobileMenuOpen = true"
        >
          <span class="sr-only">Open main menu</span>
          <Icon name="uil:bar" aria-hidden="true" />
        </button>
      </div>
      <div class="hidden lg:flex lg:gap-x-12">
        <NuxtLink
          v-for="item in navigation"
          :key="item.name"
          :to="item.href"
          class="text-sm font-semibold leading-6"
          >{{ item.name }}
        </NuxtLink>
      </div>
      <div class="flex lg:flex-1 lg:justify-end items-center gap-2">
        <ColorSwitch />
        <NuxtLink to="/login">
          <Button variant="outline" size="icon">
            <Icon name="uil:user" />
          </Button>
        </NuxtLink>
      </div>
    </nav>
  </header>
</template>
