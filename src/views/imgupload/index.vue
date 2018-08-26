<template>
  <div class="imgupload-container">
    <div><h1>Submit a photo </h1></div>
    <div>
      <img-inputer
        v-model="file"
        theme="material"
        size="normal"
        max-size="5120"
      >
      </img-inputer>
    </div>
  </div>
</template>

<script>
  import { getList } from '@/api/table'
  import ImgInputer from 'vue-img-inputer'
  import 'vue-img-inputer/dist/index.css'

  export default {
    components: {
      ImgInputer
    },
    data() {
      return {
        list: null,
        listLoading: true
      }
    },
    filters: {
      statusFilter(status) {
        const statusMap = {
          published: 'success',
          draft: 'gray',
          deleted: 'danger'
        }
        return statusMap[status]
      }
    },
    created() {
      this.fetchData()
    },
    methods: {
      fetchData() {
        this.listLoading = true
        getList(this.listQuery).then(response => {
          this.list = response.data.items
          this.listLoading = false
        })
      },
      onRead(file) {
        console.log(file)
      }
    }
  }
</script>

<style lang="stylus" scoped>
  .imgupload-container
    padding-left: 50px
</style>
