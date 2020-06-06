<template>
  <div class="modal" id="modal" :class="showModal ? 'active' : ''">
    <Card
      :data=data
      :isModal=isModal
      @closeModal=closeModal
    />
  </div>
</template>

<script>
import Card from '@/components/Card.vue'

export default {
  name: 'Modal',
  components: { Card },
  props: {
    showModal: Boolean,
    data: Object
  },
  data: () => ({
    isModal: true
  }),
  methods: {
    closeModal () {
      this.$emit('closeModal')
    }
  },
  watch: {
    showModal (data) {
      if (data === true) {
        this.isModal = true
      } else {
        this.isModal = false
      }
    }
  }
}
</script>
