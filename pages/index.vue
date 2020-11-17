<template>
  <div>index</div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator'

@Component
export default class IndexPage extends Vue {
  mounted() {
    this.$fire.firestore
      .collection('album')
      .get()
      .then((res) => {
        res.docs.forEach((item) => {
          item.data().photos.map((id: string) => {
            return this.$fire.firestore
              .collection('photo')
              .doc(id)
              .get()
              .then((image) => {
                console.log(image.data())
              })
          })
        })
      })
    // .collection('album')
    // .doc()
    // .get()
    // .then((res) => {
    //   console.log(res.data())
    // })
    // .doc('jTC0nEEKNWCz9X9uQUj9')
    // .get()
    // .then((res) => {
    //   console.log(res.data())
    // })

    // this.$fire.storage
    //   .ref()
    //   .listAll()
    //   .then((res) => {
    //     res.prefixes.forEach((folder) => {
    //       console.log(folder)
    //     })
    //     res.items.forEach((photo) => {
    //       photo.getDownloadURL().then((url) => {
    //         console.log(url)
    //       })
    //     })
    //   })
  }
}
</script>
