<template>
  <card class='experiment'
    :href='experiment.link'
    :title='experiment.title'
    :actions="[{href: experiment.link, text: 'Check it out'}]"
  >
    <div slot='image' class='image-container'>
      <img slot='image'
        :src='experiment.image'
        width='400'
        height='225'
      >
    </div>
    <p v-if='experiment.details'>{{ experiment.details }}</p>
  </card>
</template>

<script>
  import Button from '~/components/Button'
  import ButtonGroup from '~/components/ButtonGroup'
  import Card from '~/components/Card'

  export default {
    name: 'experiment',
    components: {
      'te-button': Button,
      ButtonGroup,
      Card
    },
    props: {
      experiment: {
        type: Object,
        default: () => ({
          title: '',
          details: '<p></p>',
          link: '#',
          image: ''
        }),
        require: true
      }
    }
  }
</script>

<style lang='scss' scoped>
  @import '~common/variables';

  .experiment {
    width: 100%;
    max-width: $experiment-width;
    height: 100%;
  }

  .image-container {
    padding-bottom: 56.25%;
    height: 0;
    overflow: hidden;
    background: #eee;
  }

  .image-container img {
    position: absolute;
    top: 0;
    left: 0;
  }
</style>
