<template>
  <el-form :model="ruleForm"
           ref="ruleForm">
    <el-form-item label="上传文件">
      <el-upload ref="uploada"
                 :action="mixinUploadUrl"
                 :file-list="fileList">
        <el-button size="small"
                   type="primary">点击上传
        </el-button>
      </el-upload>
    </el-form-item>
    <el-form-item>
      <el-button type="primary"
                 @click="submitForm('ruleForm')">导出
      </el-button>
    </el-form-item>
  </el-form>
</template>
<script>
  export default {
    data() {
      return {
        fileList: []
      }
    },
    methods: {
      submitForm(formName) {
        // 包含上传的文件信息和服务端返回的所有信息都在这个对象里
        this.$refs.uploada.uploadFiles
      }
    }
  }
</script>
