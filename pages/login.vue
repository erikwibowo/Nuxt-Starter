<script setup lang="ts">
import { Button } from "@/components/ui/button";
import {
  Card,
  CardContent,
  CardDescription,
  CardFooter,
  CardHeader,
  CardTitle,
} from "@/components/ui/card";
import { Checkbox } from "@/components/ui/checkbox";
import { Input } from "@/components/ui/input";
import { Label } from "@/components/ui/label";
import ColorSwitch from "@/components/color-switch.vue";

useHead({
  title: "Login",
});

const auth = "auth";
</script>
<template>
  <NuxtLayout :name="auth">
    <Card class="w-full sm:max-w-md">
      <CardHeader>
        <CardTitle class="flex justify-between items-start">
          <div class="space-y-4">
            <NuxtLink to="/" class="flex items-center gap-4">
              <img src="/favicon.ico" />
              <p>Nuxt Starter</p>
            </NuxtLink>
            <div class="space-y-1">
              <p>Login</p>
              <CardDescription>Login into your account</CardDescription>
            </div>
          </div>
          <ColorSwitch />
        </CardTitle>
      </CardHeader>
      <CardContent>
        <form class="space-y-4">
          <div class="w-full space-y-1">
            <Label for="email">Email</Label>
            <Input id="email" type="email" placeholder="Email" />
          </div>
          <div class="w-full space-y-1">
            <Label for="password">Password</Label>
            <Input id="password" type="password" placeholder="********" />
          </div>
          <div class="w-full flex items-center space-x-2">
            <Checkbox id="remember" />
            <label
              for="remember"
              class="text-sm font-medium leading-none peer-disabled:cursor-not-allowed peer-disabled:opacity-70"
            >
              Remember Me
            </label>
          </div>
        </form>
      </CardContent>
      <CardFooter class="flex justify-between items-center gap-4">
        <Button variant="link" class="px-0">Forgot password?</Button>
        <Button>Login</Button>
      </CardFooter>
    </Card>
  </NuxtLayout>
</template>
