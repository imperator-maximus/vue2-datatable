# § Getting started

`>_ npm i -S vue2-datatable-component`

```js
import Vue from 'vue'
import Datatable from 'vue2-datatable-component'

Vue.use(Datatable) // OK
```

Let's roll up with the basic example (source - [`examples/src/Basic/index.vue`](https://github.com/OneWayTech/vue2-datatable/blob/master/examples/src/Basic/index.vue) , demo - [examples#basic](https://OneWayTech.github.io/vue2-datatable/examples/dist))

```html
<template>
  <div>
    <code>query: {{ query }}</code>
    <datatable v-bind="$data" />
  </div>
</template>
<script>
import mockData from '../_mockData'

export default {
  data: () => ({
    columns: [
      { title: 'User ID', field: 'uid', sort: true },
      { title: 'Username', field: 'name' },
      { title: 'Age', field: 'age', sort: true },
      { title: 'Email', field: 'email' },
      { title: 'Country', field: 'country' }
    ],
    data: [],
    total: 0,
    query: {}
  }),
  watch: {
    query: {
      handler (query) {
        mockData(query).then(({ rows, total }) => {
          this.data = rows
          this.total = total
        })
      },
      deep: true
    }
  }
}
</script>
```
