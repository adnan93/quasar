<template>
  <q-page class="bg-grey-3 column">
    <q-list class="bg-white" separator bordered>
      <q-item v-for="task in tasks" :key="task.title" v-ripple>
        <q-item-section avatar>
          <q-checkbox v-model="task.done" val="teal" color="secondary" />
        </q-item-section>

        <q-item-section>
          <q-item-label> {{ task.title }} </q-item-label>
        </q-item-section>
      </q-item>
    </q-list>
  </q-page>
</template>

<script>
export default {
  data() {
    return {
      color: "red",
      tasks: [
        { title: "Get banana", done: false },
        { title: "Eat banana", done: true },
        { title: "Poo banana", done: false },
      ],
    };
  },
};
</script>
