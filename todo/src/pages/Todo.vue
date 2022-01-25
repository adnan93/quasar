<template>
  <q-page class="bg-grey-3 column">
    <row class="q-pa-sm bg-primary">
      <q-input
        class="col"
        square
        v-model="newTask"
        @keyup.enter="addTask"
        bg-color="white"
        label="اضافه جديد"
        dense
        filled
        maxlength="12"
      >
        <template v-slot:hint> اضافه جديد </template>

        <template v-slot:append>
          <q-btn @click="addTask" round dense flat icon="add" />
        </template>
      </q-input>
    </row>
    <q-list class="bg-white" separator bordered>
      <q-item
        v-for="(task, index) in tasks"
        :key="task.title"
        @click="task.done = !task.done"
        :class="{ 'done bg-blue-1': task.done }"
        clickable
        v-ripple
      >
        <q-item-section avatar>
          <q-checkbox
            v-model="task.done"
            class="no-pointer-events"
            val="teal"
            color="secondary"
          />
        </q-item-section>

        <q-item-section>
          <q-item-label> {{ task.title }} </q-item-label>
        </q-item-section>

        <q-item-section v-if="task.done" side>
          <q-btn @click="deleteTask(index)" dense round color="primary" icon="delete" />
        </q-item-section>
      </q-item>
    </q-list>

    <div
    v-if="!tasks.length"
     class="no-tasks absolute-center">
      <q-icon name="check"
      size="100px"
      color="primary" /> 
      <div class="text-5 text-primary text-center "> No Tasks</div>


    </div>

  </q-page>
</template>

<script>
export default {
  data() {
    return {
      newTask: "",
      color: "red",
      tasks: [
        // { title: "Get banana", done: false },
        // { title: "Eat banana", done: true },
        // { title: "Poo banana", done: false },
      ],
    };
  },
  methods: {
    deleteTask(index) {
      this.$q
        .dialog({
          title: "حذف",
          message: "متاكد ؟  مطمئنی؟",
          cancel: true,
          persistent: true,
        })
        .onOk(() => {
          this.tasks.splice(index, 1);
          this.$q.notify(" ! والله انحذفت ");
        });
    },
    addTask() {
      this.tasks.push({
        title: this.newTask,
        done: false,
      });
    this.newTask= "";
    },
  },
};
</script>

<style lang="scss">
.done {
  .q-item__label {
    text-decoration: line-through;
  }
}

.no-tasks{
  opacity: 0.5;

}
</style>
