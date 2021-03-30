<template>
  <el-footer class="footer" height="70px">
    <div class="slider">
      <div class="slider--prev"><a href="#slide-1">＜</a></div>
      <div class="slider--next"><a href="#slide-5">＞</a></div>
      <div class="slider--slides">
        <div id="slide-1" @click="show = true">1</div>
        <div id="slide-2" @click="show = true">2</div>
        <div id="slide-3" @click="show = true">3</div>
        <div id="slide-4" @click="show = true">4</div>
        <div id="slide-5" @click="show = true">5</div>
      </div>
    </div>
  </el-footer>
  <el-dialog
    title="提示"
    v-model="show"
    width="30%"
    :before-close="handleClose"
  >
    <span>這是一段訊息</span>
    <template #footer>
      <span class="dialog-footer">
        <el-button @click="show = false">取 消</el-button>
        <el-button type="primary" @click="show = false">確 定</el-button>
      </span>
    </template>
  </el-dialog>
</template>

<script>
import "element-plus/lib/theme-chalk/index.css";
import { ElFooter, ElDialog, ElButton } from "element-plus";

export default {
  components: {
    ElFooter,
    ElDialog,
    ElButton,
  },
  data() {
    return { show: false };
  },
  methods: {
    handleClose(done) {
      // this.$confirm("確認關閉？")
      //   .then((_) => {
      //     done();
      //   })
      //   .catch((_) => {});
    },
  },
};
</script>

<style lang="scss" scoped>
.footer {
  position: fixed;
  bottom: 0;
  background: #fff;
  width: 100%;
  z-index: 999;
  display: flex;
  align-items: center;
}
.slider {
  width: 200px;
  text-align: center;

  margin: 0 auto;
  position: relative;
  &--prev,
  &--next {
    position: absolute;
    top: 50%;
    cursor: pointer;
  }
  &--prev {
    transform: translate(-50%, -50%);
    left: -20px;
  }
  &--next {
    transform: translate(50%, -50%);
    right: -20px;
  }
  &--slides {
    display: flex;
    overflow-x: auto;
    scroll-snap-type: x mandatory;
    scroll-behavior: smooth;
    -webkit-overflow-scrolling: touch;

    &:hover {
      .slider--slides::-webkit-scrollbar {
        visibility: true;
      }
    }
    &::-webkit-scrollbar {
      width: 10px;
      height: 3px;
      visibility: false;
    }
    &::-webkit-scrollbar-thumb {
      background: black;
      border-radius: 5px;
    }
    &::-webkit-scrollbar-track {
      background: transparent;
    }
    div {
      scroll-snap-align: start;
      flex-shrink: 0;
      width: 50px;
      height: 50px;
      margin-right: 10px;
      border-radius: 10px;
      background: #eee;
      transform-origin: center center;
      transform: scale(1);
      transition: transform 0.5s;
      position: relative;
      display: flex;
      justify-content: center;
      align-items: center;
      cursor: pointer;
    }
  }
}

.slides > div:target {
  /*   transform: scale(0.8); */
}
</style>