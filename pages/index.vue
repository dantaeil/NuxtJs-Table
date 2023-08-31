<script>
let id = 0;
export default {
  data() {
    return {
      data: [
        { id: id++, first: "Mark", last: "Otto", handle: "@mdo" },
        { id: id++, first: "Jacob", last: "Thornton", handle: "@fat" },
        { id: id++, first: "Larry", last: "the Bird", handle: "@twitter" },
      ],
      firstInput: "",
      lastInput: "",
      handleInput: "",
    };
  },
  methods: {
    onAdd() {
      this.data.push({
        id: id++,
        first: this.firstInput,
        last: this.lastInput,
        handle: this.handleInput,
      });
    },
    onDelete(id) {
      this.data = this.data.filter((item) => item.id != id);
    },
  },
};
</script>

<template>
  <div>
    <table class="table table-striped">
      <thead>
        <tr>
          <th scope="col">#</th>
          <th scope="col">First</th>
          <th scope="col">Last</th>
          <th scope="col">Handle</th>
        </tr>
        <tr>
          <th scope="col">
            <button type="button" class="btn btn-primary" @click="onAdd">
              Add
            </button>
          </th>
          <th scope="col">
            <input
              class="form-control form-control-sm"
              type="text"
              placeholder="First"
              v-model="firstInput"
            />
          </th>
          <th scope="col">
            <input
              class="form-control form-control-sm"
              type="text"
              placeholder="Last"
              v-model="lastInput"
            />
          </th>
          <th scope="col">
            <input
              class="form-control form-control-sm"
              type="text"
              placeholder="Handle"
              v-model="handleInput"
            />
          </th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="item in data" :key="item.first">
          <th scope="row">
            <button
              type="button"
              class="btn btn-secondary"
              @click="onDelete(item.id)"
            >
              Del
            </button>
          </th>
          <td>{{ item.first }}</td>
          <td>{{ item.last }}</td>
          <td>{{ item.handle }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>
