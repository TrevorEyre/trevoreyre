<template>
  <section class='project-summary'>
    <container size='small' class='description'>
      <h2 class='title'>{{ title }}</h2>
      <slot></slot>
      <slot name='actions'></slot>
    </container>
    <div class='image'>
      <slot name='image'></slot>
    </div>
  </section>
</template>

<script>
  import ButtonGroup from '~/components/ButtonGroup'
  import Container from '~/components/Container'
  import DeviceGroup from '~/components/DeviceGroup'

  export default {
    name: 'project-summary',
    components: {
      ButtonGroup,
      Container,
      DeviceGroup
    },
    props: {
      title: {
        type: String,
        default: '',
        required: true
      }
    }
  }
</script>

<style lang='scss' scoped>
  @import '~common/variables';
  @import '~common/mixins';

  .project-summary {
    display: flex;
    flex-direction: column;
    @include breakpoint-tablet() {
      flex-direction: row;
      align-items: center;
    }
  }

  .description {
    flex: 1;
  }

  .image {
    min-height: 250px;
    flex: 2;
  }

  .project-summary > *:first-child {
    margin-bottom: $spacing-l;
    @include breakpoint-tablet() {
      margin-bottom: 0;
      margin-right: $spacing-xl;
    }
  }

  .project-logo {
    width: auto;
    max-width: 100%;
  }
</style>