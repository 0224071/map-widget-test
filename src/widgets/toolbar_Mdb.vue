
<template>
  <!-- Footer -->
  <MDBNavbar
    dark
    bg="light"
    position="bottom"
    container
  >
    <div class="slider">
      <div class="slider--prev"><a href="#slide-1">＜</a></div>
      <div class="slider--next"><a href="#slide-5">＞</a></div>
      <div class="slider--slides">
        <div
          id="slide-1"
          @click="show = true"
        >1</div>
        <div
          id="slide-2"
          @click="show = true"
        >2</div>
        <div
          id="slide-3"
          @click="show = true"
        >3</div>
        <div
          id="slide-4"
          @click="show = true"
        >4</div>
        <div
          id="slide-5"
          @click="show = true"
        >5</div>
      </div>
    </div>
  </MDBNavbar>
  <!-- Footer -->
  <MDBModal
    id="exampleModal"
    tabindex="-1"
    labelledby="exampleModalLabel"
    v-model="show"
  >
    <MDBModalHeader>
      <MDBModalTitle id="exampleModalLabel"> Modal title </MDBModalTitle>
    </MDBModalHeader>
    <MDBModalBody>...</MDBModalBody>
    <MDBModalFooter>
      <MDBBtn
        color="secondary"
        @click="show = false"
      >Close</MDBBtn>
      <MDBBtn color="primary">Save changes</MDBBtn>
    </MDBModalFooter>
  </MDBModal>
</template>

<script>
import {
  MDBNavbar,
  MDBModal,
  MDBModalHeader,
  MDBModalTitle,
  MDBModalBody,
  MDBModalFooter,
  MDBBtn,
} from "mdb-vue-ui-kit";

export default {
  components: {
    MDBNavbar,
    MDBModal,
    MDBModalHeader,
    MDBModalTitle,
    MDBModalBody,
    MDBModalFooter,
    MDBBtn,
  },
  data() {
    return {
      show: false,
    };
  },
  created() {
    //  require("mdb-vue-ui-kit/css/mdb.min.css");
  },
  mounted() {
    this.show = false;
    var head = document.head;
    var link = document.createElement("link");
    link.type = "text/css";
    link.rel = "stylesheet";
    link.id = "mdb-stylesheet";
    link.href = "https://cdn.jsdelivr.net/npm/mdbvue/lib/css/mdb.min.css";
    head.appendChild(link);
    var link = document.createElement("link");
    link.type = "text/css";
    link.rel = "stylesheet";
    link.id = "bootstrap-stylesheet";
    link.href =
      "https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/css/bootstrap.min.css";

    head.appendChild(link);
  },
  beforeUnmount() {
    const mdb = document.querySelector(
      "link[rel=stylesheet][id='mdb-stylesheet']"
    );

    mdb.parentNode.removeChild(mdb);
    const bootstrap = document.querySelector(
      "link[rel=stylesheet][id='bootstrap-stylesheet']"
    );
    bootstrap.parentNode.removeChild(bootstrap);
  },
};
</script>


<style lang="scss" scoped>
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