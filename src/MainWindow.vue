<template>
  <Window title="Tasky" width="400" height="500" margined v-on:close="exit">
    <Box>
      <Text>Task {{ tasks.length }}</Text>
        <TextInput label="Write new task..." type="text" v-model="newTask"/>
      <Button @click="aggTask">Add task</Button>
      <Separator horizontal/>
      <Text v-for="(task, item) in tasks" :key="item">
        {{ task }}
      </Text>
    </Box>
  </Window>
</template>

<script>
export default {
  data: () => ({
    newTask: '',
    tasks: [],
  }),
  methods: {
    aggTask() {
      this.tasks.push(this.newTask);
      this.newTask = '';
    },
    deleteTask(item) {
      this.tasks.splice(item, 1);
    },
    exit() {
      this.$exit();
    }
  }
}
</script>
