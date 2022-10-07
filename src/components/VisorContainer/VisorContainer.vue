<template>
  <div class="component-input-value">
    <slot></slot>
  </div>
</template>

<script>
import { Options, Vue } from 'vue-class-component';

export default class VisorContainer extends Vue {}
</script>

<style lang="scss" scoped>
@import './VisorContainer.scss';
</style>
