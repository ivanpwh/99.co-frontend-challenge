<template>
  <div class="card-content">
    <div class="picture-container">
      <img class="picture" :src="isMap ? map : data.picture" alt="Gambar Rumah">
      <img class="marker" src="@/assets/icon/marker.svg" alt="marker" v-if="isMap">
    </div>
    <div class="card-container">
      <div class="card-status" v-if="!isMap">
        <div class="box">
          <button class="box-sale">Dijual</button>
          <button class="box-nego">Nego</button>
        </div>
        <img class="box-love" src="@/assets/icon/love.svg" alt="love">
      </div>
      <div class="card-detail map" v-if="isMap">
        <p><b>{{data.address}}</b></p>
        <p>{{data.details}}</p>
      </div>
      <div class="card-detail" v-else>
        <p><b>Rp {{data.price}} jt</b> cicilan Rp {{data.credit}}jt/bln</p>
        <div v-if="isModal" class="desc">
          <p><b>{{data.description}}</b></p>
          <p>{{data.address}}</p>
        </div>
        <div class="specification">
          <p><span><img src="@/assets/icon/Kamar Tidur.svg" alt="Kamar Tidur"></span> {{data.bedRm}} K. Tidur</p>
          <p><span><img src="@/assets/icon/Kamar Mandi.svg" alt="Kamar Mandi"></span> {{data.bathRm}} K. Mandi</p>
          <p><span><img src="@/assets/icon/Luas Bangunan.svg" alt="Luas Bangunan"></span> {{data.building}} m2</p>
          <p><span><img src="@/assets/icon/Luas Tanah.svg" alt="Luas Tanah"></span> {{data.surface}} m2</p>
        </div>
      </div>
      <button class="card-show" @click="closeModal()" v-if="isMap"> Tutup </button>
      <button class="card-show" @click="isModal ? openMap() : openModal()" v-else>{{isModal ? 'Lihat Peta' : 'Lihat Detail'}}</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Card',
  props: {
    data: Object,
    isModal: Boolean
  },
  data: () => ({
    isMap: false,
    map: require('@/assets/image/map@2x.png')
  }),
  methods: {
    // function open modal
    openModal () {
      this.$emit('openModal')
    },

    // function close modal
    closeModal () {
      this.$emit('closeModal')
    },

    // change view map modal
    openMap () {
      this.isMap = true
    }
  },
  watch: {
    isModal (data) {
      if (!data) {
        this.isMap = false
      }
    }
  }
}
</script>
