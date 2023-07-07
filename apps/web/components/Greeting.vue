<template>
  <div>
    <p v-if="greeting">{{ greeting }}</p>
    <p v-else>no greeting {{ ':(' }}</p>
  </div>
</template>

<script setup lang="ts">
  import axios from 'axios';

  const greeting: Ref<string> = ref('');
  async function getGreeting(): Promise<void> {
    try {
      const resp = await axios.get('http://localhost:8080/api');
      if (resp) {
        greeting.value = resp.data;
      }
    } catch (error) {
      console.log('error');
    }
  }
  await getGreeting();
</script>
