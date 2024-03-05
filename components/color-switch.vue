<script setup lang="ts">
import { Button } from "@/components/ui/button";
const colorMode = useColorMode();
const changeColor = () => {
  if (colorMode.preference === "system") {
    colorMode.preference = "dark";
  } else if (colorMode.preference === "dark") {
    colorMode.preference = "light";
  } else {
    colorMode.preference = "system";
  }
};
</script>
<template>
  <ClientOnly>
    <Button @click.prevent="changeColor()" variant="outline" size="icon">
      <Icon v-if="colorMode.preference === 'system'" name="uil:desktop" />
      <Icon v-if="colorMode.preference === 'dark'" name="uil:moon" />
      <Icon v-if="colorMode.preference === 'light'" name="uil:sun" />
    </Button>
  </ClientOnly>
</template>
