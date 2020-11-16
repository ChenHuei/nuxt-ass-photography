<template>
  <div>index</div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator'

@Component
export default class IndexPage extends Vue {
  mounted() {
    this.$fire.firestore
      .collection('test')
      .doc('jTC0nEEKNWCz9X9uQUj9')
      .get()
      .then((res) => {
        console.log(res.data())
      })

    this.$fire.storage
      .ref('test')
      .child('test.jpeg')
      .getDownloadURL()
      .then((res) => {
        console.log(res)
      })
  }
}
</script>
