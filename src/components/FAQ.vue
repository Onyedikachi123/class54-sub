<template>
  <div :class="open ? 'faq open' : 'faq'" @click="$emit('toggleOpen', index)" class="animate__animated animate__fadeInUpBig">
    <div class="question">{{ faq.question }}</div>
     <div class="answer">{{ faq.answer }}</div>
  </div>
</template>

<script>
export default {
 name: 'FAQ',
 props: ['faq', 'index', 'open']
}
</script>

<style>

</style>