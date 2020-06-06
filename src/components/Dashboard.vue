<template>
  <div class="dashboard">
    <div class="dashboard-head">
      <img src="@/assets/image/TEST.png" alt="TEST">
      <img src="@/assets/image/FRONTend.png" alt="FRONTend">
    </div>
    <div class="dashboard-content">
      <div class="detail">
        <h1 class="detail-title">Start Your Journey</h1>
        <p class="detail-text">Lorem ipsum dolor sit amet consectetur adipisicing elit. Excepturi id eaque reprehenderit distinctio fugit exercitationem cum possimus, corporis earum libero quidem unde culpa quo fugiat sed eius cupiditate quisquam ab.</p>
      </div>
      <div class="card">
        <button class="card-button" @click="prev()">
          <img src="@/assets/icon/Arrow Left.svg" alt="Arrow Left">
        </button>
        <Card
          :data=selectedData
          @openModal=openModal
        />
        <button class="card-button" @click="next()">
          <img src="@/assets/icon/Arrow Right.svg" alt="Arrow Right">
        </button>
      </div>
    </div>

    <Modal
      :showModal="showModal"
      :data=selectedData
      @closeModal=closeModal
    />
    <div id="overlay" :class="showModal ? 'active' : ''" @click="closeModal()"></div>
  </div>
</template>

<script>
import Modal from '@/components/Modal.vue'
import Card from '@/components/Card.vue'

export default {
  name: 'Dashboard',
  components: { Modal, Card },
  data: () => ({
    showModal: false,
    dataDummy: [
      {
        id: 1,
        price: '326',
        credit: '2,6',
        bedRm: 2,
        bathRm: 2,
        building: 65,
        surface: 65,
        description: 'Rumah Minimalis dijual di Bandung Jawa Barat',
        details: 'Lorem ipsum dolor sit, amet consectetur adipisicing elit. Obcaecati aperiam maiores modi praesentium expedita error eius. Blanditiis saepe a quis quod aliquid nulla, suscipit perspiciatis repellendus debitis impedit numquam unde!',
        address: 'Jl Sukajadi No. 1 Bandung, Jawa Barat',
        picture: require('@/assets/image/rumah1.jpg')
      },
      {
        id: 2,
        price: '422',
        credit: '3,7',
        bedRm: 4,
        bathRm: 3,
        building: 90,
        surface: 90,
        description: 'Rumah Strategis di Bandung Jawa Barat',
        details: 'Lorem ipsum dolor sit, amet consectetur adipisicing elit. Obcaecati aperiam maiores modi praesentium expedita error eius. Blanditiis saepe a quis quod aliquid nulla, suscipit perspiciatis repellendus debitis impedit numquam unde!',
        address: 'Jl Marga Asri No. 21 Bandung, Jawa Barat',
        picture: require('@/assets/image/rumah2.jpg')
      },
      {
        id: 3,
        price: '590',
        credit: '4,9',
        bedRm: 4,
        bathRm: 4,
        building: 150,
        surface: 150,
        description: 'Rumah Bebas Banjir di Semarang Jawa Tengah',
        details: 'Lorem ipsum dolor sit, amet consectetur adipisicing elit. Obcaecati aperiam maiores modi praesentium expedita error eius. Blanditiis saepe a quis quod aliquid nulla, suscipit perspiciatis repellendus debitis impedit numquam unde!',
        address: 'Jl Soekarno Hatta No. 1 Semarang, Jawa Tengah',
        picture: require('@/assets/image/rumah3.jpg')
      }
    ],
    selectedData: {}
  }),
  created () {
    this.init()
  },
  methods: {
    // initialization data
    init () {
      this.selectedData = this.dataDummy[0]
    },

    // function open modal
    openModal () {
      this.showModal = true
    },

    // function close modal
    closeModal () {
      this.showModal = false
    },

    // set next data
    next () {
      const currentId = this.selectedData.id

      if (currentId === this.dataDummy.length) {
        this.selectedData = this.dataDummy[0]
      }
      this.dataDummy.filter((data) => {
        if (data.id === currentId + 1) {
          this.selectedData = data
        }
      })
    },

    // set previous data
    prev () {
      const currentId = this.selectedData.id

      if (currentId === 1) {
        this.selectedData = this.dataDummy[2]
      }
      this.dataDummy.filter((data) => {
        if (data.id === currentId - 1) {
          this.selectedData = data
        }
      })
    }
  }

}
</script>
