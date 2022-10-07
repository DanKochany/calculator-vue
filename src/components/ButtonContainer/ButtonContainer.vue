<template>
  <div class="background">
    <slot><button></button></slot>
  </div>
</template>

<script>
import { Options, Vue } from 'vue-class-component';
export default class ButtonContainer extends Vue {}
</script>

<style lang="scss" scoped>
@import './ButtonContainer.scss';
</style>
