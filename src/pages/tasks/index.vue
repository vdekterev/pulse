<script setup lang="ts">
import { supabase } from "@/lib/supabaseClient.ts";
import { ref } from "vue";
import type { Tables } from "../../../database/types.ts";

const tasks = ref<Tables<'tasks'>[] | null>(null);

(async () => {
  const {data, error} = await supabase.from('tasks').select();
  if (error) console.error(error);
  tasks.value = data;
})();

</script>

<template>
  <main>
    <h1>Welcome Tasks</h1>
    <div>
      <ul>
        <li v-for="t in tasks" :key="t.id">
          {{ t.name }}
        </li>
      </ul>
    </div>
    <RouterLink :to="{ name: '/' }">
      Home
    </RouterLink>
  </main>
</template>
