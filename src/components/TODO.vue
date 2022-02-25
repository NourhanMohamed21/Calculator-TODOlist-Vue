<template>
  <div id="image">
    <h1>My TODO List</h1>
    <b-container fluid>
      <b-row class="my-1">
        <b-col sm="2"> </b-col>
        <b-col sm="7">
          <b-form-input
            type="text"
            v-model="TodoTask"
            placeholder="TODO task"
          ></b-form-input>
        </b-col>
        <b-col sm="1">
          <b-button @click="SubmitTask" variant="primary">Submit</b-button>
        </b-col>
      </b-row>
    </b-container>
    <div class="container-fluid">
      <div class="offset-md-2 col-md-8 col-12">
        <table class="table table-bordered table-responsive-sm">
          <thead>
            <tr class="">
              <th>No.</th>
              <th>Task</th>
              <th>Status</th>
              <th>#</th>
              <th>#</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="(task, index) in task" :key="index">
              <td>{{ index + 1 }}</td>
              <td>
                <span :class="{ finished: task.status === 'Finished' }">
                  {{ task.name }}
                </span>
              </td>

              <td>
                <span
                  @click="ProgFun(index)"
                  class="pointer"
                  :class="{
                    'text-danger': task.status === 'TODO',
                    'text-warning': task.status === 'InProgress',
                    'text-success': task.status === 'Finished',
                  }"
                  >{{ task.status }}</span
                >
              </td>
              <td>
                <div @click="edit(index)">
                  <span class="pointer">
                    <font-awesome-icon :icon="['fas', 'pen']" />
                  </span>
                </div>
              </td>
              <td>
                <div @click="Delete(index)">
                  <span class="pointer">
                    <font-awesome-icon :icon="['fas', 'trash']" />
                  </span>
                </div>
              </td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "TODO",
  data() {
    return {
      TodoTask: "",
      editedTask: null,
      progress: ["TODO", "InProgress", "Finished"],
      task: [
        { name: "Task1", status: "TODO" },
        {
          name: "Task2",
          status: "InProgress",
        },
      ],
    };
  },
  methods: {
    SubmitTask() {
      if (this.editedTask === null) {
        if (this.task.length === 0) return;

        this.task.push({
          name: this.TodoTask,
          status: "TODO",
        });
      } else {
        this.task[this.editedTask].name = this.TodoTask;
        this.editedTask = null;
        console.log(this.TodoTask);
      }
      this.TodoTask = "";
    },
    edit(index) {
      this.TodoTask = this.task[index].name;
      this.editedTask = index;
    },
    Delete(index) {
      this.task.splice(index, 1);
    },
    ProgFun(index) {
      console.log(this.task[index].name);
      let x = this.progress.indexOf(this.task[index].status);
      x += 1;
      if (x > 2) x = 0;
      console.log(this.progress[x]);
      this.task[index].status = this.progress[x];
    },
  },
};
</script>
<style scoped>
.pointer {
  cursor: pointer;
}
.finished {
  text-decoration: line-through;

}

</style>