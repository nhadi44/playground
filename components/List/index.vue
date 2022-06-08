<template>
  <div
    class="
      d-flex
      flex-column
      justify-content-center
      align-items-center
      w-100
      bg-light
    "
    style="height: 100vh; margin: 0 auto"
  >
    <h1 class="mb-4 text-uppercase">To do list</h1>
    <div class="card w-25">
      <div class="card-body bg-info p-5">
        <form class="mb-4" @submit="onSubmit">
          <div class="row g-2 align-items-center">
            <div class="col-10">
              <input v-model="name" type="text" class="form-control" />
            </div>
            <div class="col-2">
              <button class="btn btn-success" type="submit">Submit</button>
            </div>
          </div>
          <span>{{ status }}</span>
        </form>
        <div class="my-3">
          <h4>List:</h4>
          <div
            v-for="(list, index) in lists"
            :key="index"
            class="row g-2 align-items-center justify-content-between mb-3"
          >
            <div class="col-11">
              <label
                class="form-col-label fs-5 bg-light w-100 px-2 py-1 rounded"
                >{{ list.name }}</label
              >
            </div>
            <div class="col-1">
              <button class="btn btn-danger" @click="removeList(index)">
                <span>X</span>
              </button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: 'ListComponent',
  data() {
    return {
      lists: [
        {
          name: 'Create a new Vue.js project',
        },
      ],
      name: '',
      status: '',
    }
  },
  methods: {
    removeList(index) {
      this.lists.splice(index, 1)
    },
    onSubmit(e) {
      e.preventDefault()
      if (!this.name) return (this.status = 'Name is required')
      this.lists.push({ name: this.name })
      this.name = ''
    },
  },
}
</script>