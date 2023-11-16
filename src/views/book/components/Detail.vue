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
          <!-- 表单控件的具体样式 -->
        </el-col>
        <el-col :span="24"></el-col>
      </el-row>
    </div>
  </el-form>
</template>
<script>
import Sticky from "../../../components/Sticky/index.vue";
import Warning from "./Warning.vue";

export default {
  components: { Sticky, Warning },
  props: {
    isEdit: Boolean,
  },
  data() {
    return {
      loading: false,
      postForm: {},
    };
  },
  methods: {
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
