<script setup lang="ts">
import { supabase } from "@/lib/supabaseClient.ts";
import { ref } from "vue";
import type { Tables } from "../../../database/types.ts";

const projects = ref<Tables<'projects'>[] | null>(null);

(async () => {
  const {data, error} = await supabase.from('projects').select();
  if (error) console.error(error);
  projects.value = data;
})();

</script>

<template>
  <main>
    <h1>Welcome Projects</h1>
    <div>
      <ul>
        <li v-for="p in projects" :key="p.id">
          {{ p.name }}
        </li>
      </ul>
    </div>
    <RouterLink :to="{ name: '/' }">
      Home
    </RouterLink>
  </main>
</template>
