<script setup lang="ts">
import { computed } from 'vue';

const { status, signIn, signOut } = useAuth();

const loggedIn = computed(() => status.value === 'authenticated');

async function handleSignIn() {
 const githubProvider = 'github';
 await signIn(githubProvider);
}

async function handleSignOut() {
 await signOut();
}
</script>

<template>
 <div>
  <button v-if="loggedIn" @click="handleSignOut">Sign Out</button>
  <button v-else @click="handleSignIn">Sign In</button>
 </div>
</template>
