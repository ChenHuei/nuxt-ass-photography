<template>
  <nav class="layout-header-wrapper">
    <div class="layout-header-container">
      <div class="layout-header">
        <div class="layout-header-title">ASS PHOTOGRAPHY</div>
        <div class="layout-header-icons">
          <a
            v-for="icon in iconList"
            :key="icon.link"
            :href="icon.link"
            class="layout-header-icons-item"
            rel="noopener"
            target="_blank"
          >
            <font-awesome-icon :icon="iconClassHandler(icon.icon)" />
          </a>
        </div>
        <div class="layout-header-links">
          <nuxt-link
            v-for="link in linkList"
            :key="link.route"
            :to="link.route"
            :class="activeClassHandler(link.route)"
          />
        </div>
      </div>
    </div>
  </nav>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator'

// constants
import { ICON_LIST, LINK_LIST } from '@/constants/project/layout/header'

// types
import { ClassObject } from '@/types'
import { IconItem, LinkItem } from '@/types/project/layout/header'

@Component
export default class LayoutHeader extends Vue {
  iconList: IconItem[] = ICON_LIST
  linkList: LinkItem[] = LINK_LIST

  get current(): string {
    return this.$route.name ?? ''
  }

  activeClassHandler(route: string): ClassObject {
    return {
      'layout-header-links-item': true,
      active: this.current === route,
    }
  }

  iconClassHandler(icon: string): string[] {
    return ['fab', icon]
  }
}
</script>

<style lang="scss" scoped>
.layout-header {
  @include size(100%, auto);
  @include display-flex();

  flex-direction: column;
  padding: 48px 32px 32px;
}
</style>
