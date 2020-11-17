<template>
  <div class="default-layout">
    <layout-header />
    <div class="default-layout-wrapper">
      <div class="default-layout-container">
        <Nuxt />
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator'

// components
import LayoutHeader from '@/components/project/layout/Header.vue'

@Component({
  components: { LayoutHeader },
})
export default class DefaultLayout extends Vue {}
</script>

<style lang="scss" scoped>
.default-layout {
  @include size(100vw, 100vh);

  display: felx;
  flex-direction: column;
  color: var(--white);
  background-color: var(--primary);
}
</style>
