<template>
  <el-form ref="postForm" :model="postForm">
    <sticky :class-name="'sub-navbar'">
      <el-button v-if="!isEdit" @click="showGuide">显示帮助</el-button>
      <el-button
        v-loading="loading"
        @click="submitForm"
        type="success"
        style="margin-left: 10px"
        >{{ isEdit ? "编辑电子书" : "新增电子书" }}</el-button
      >
    </sticky>
    <div class="detail-container">
      <el-row>
        <Warning />
        <el-col :span="24">
          <EbookUpload
            :file-list="fileList"
            :disabled="isEdit"
            @onSuccess="onUploadSuccess"
            @onRemove="onUploadRemove"
          >
          </EbookUpload>
        </el-col>
        <el-col :span="24"></el-col>
      </el-row>
    </div>
  </el-form>
</template>
<script>
import Sticky from "../../../components/Sticky";
import Warning from "./Warning";
import EbookUpload from "@/components/EbookUpload";

export default {
  components: { Sticky, Warning, EbookUpload },
  props: {
    isEdit: Boolean,
  },
  data() {
    return {
      loading: false,
      postForm: {},
      fileList: [],
    };
  },
  methods: {
    onUploadSuccess() {
      console.log("onUploadSuccess");
    },
    onUploadRemove() {
      console.log("onUploadRemove");
    },
    submitForm() {
      this.loading = true;
      setTimeout(() => {
        this.loading = false;
      }, 1000);
    },
    showGuide() {
      console.log("show guide...");
    },
  },
};
</script>

<style lang="scss" scoped>
.detail-container {
  padding: 40px 50px 20px;
}
</style>
