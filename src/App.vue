<template>
  <header>
    <div class="title">
      <img src="./assets/heart.svg" alt="" />
      <h1>HYRULE JOBS</h1>
    </div>
    <div class="order">
      <button @click="handleClick('title')">Order by title</button>
      <button @click="handleClick('salary')">Order by salary</button>
      <button @click="handleClick('location')">Order by location</button>
    </div>
  </header>
  <JobsList :jobs="jobs" :order="order" />
</template>

<script lang="ts">
import { defineComponent, ref } from "vue";
import Job from "./types/Job";
import OrderTerm from "./types/OrderTerm";
import JobsList from "./components/JobsList.vue";

export default defineComponent({
  name: "App",
  components: {
    JobsList,
  },

  setup() {
    const jobs = ref<Job[]>([
      {
        id: 1,
        title: "carpenter",
        location: "bethlehem",
        number: 900,
        salary: 2000,
      },
      {
        id: 1,
        title: "thief",
        location: "birmingham",
        number: 90,
        salary: 100000,
      },
      {
        id: 1,
        title: "cobbler",
        location: "paris",
        number: 100,
        salary: 8000,
      },
      {
        id: 1,
        title: "painter",
        location: "marseille",
        number: 900,
        salary: 1000,
      },
    ]);

    const order = ref<OrderTerm>("title");
    const handleClick = (term: OrderTerm) => {
      order.value = term;
    };

    return { jobs, handleClick, order };
  },
});
</script>

<style>
header {
  text-align: center;
}
header .order {
  margin-top: 20px;
}
button {
  margin: 0 10px;
  color: #1195c9;
  border: 3px solid #1195c9;
  background: #d5f0ff;
  padding: 8px 16px;
  border-radius: 4px;
  cursor: pointer;
  font-weight: bold;
}
header .title {
  display: flex;
  justify-content: center;
}
header img {
  width: 60px;
  margin-right: 20px;
}
header h1 {
  font-size: 3em;
}
</style>
