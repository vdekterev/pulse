<script setup lang="ts">
import { Button } from '@/components/ui/button'
</script>

<template>
  <main>
    <h1>Welcome Home</h1>
    <RouterLink :to="{ name: '/projects/' }">
      Projects
    </RouterLink>
    <Button>
      Click me
    </Button>
  </main>
</template>
