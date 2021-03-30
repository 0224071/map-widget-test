<style scoped lang="scss">
.footer {
  z-index: 999;
}
.modal {
  z-index: 1000;
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
<template>
  <footer
    class="footer bg-white w-full fixed bottom-0 left-0 pt-1 border-b-2 border-blue-700"
  >
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
  </footer>
  <!-- This example requires Tailwind CSS v2.0+ -->
  <div
    class="modal fixed z-10 inset-0 overflow-y-auto"
    aria-labelledby="modal-title"
    role="dialog"
    aria-modal="true"
    v-show="show"
  >
    <div
      class="flex items-end justify-center min-h-screen pt-4 px-4 pb-20 text-center sm:block sm:p-0"
    >
      <!--
      Background overlay, show/hide based on modal state.

      Entering: "ease-out duration-300"
        From: "opacity-0"
        To: "opacity-100"
      Leaving: "ease-in duration-200"
        From: "opacity-100"
        To: "opacity-0"
    -->
      <div
        class="fixed inset-0 bg-gray-500 bg-opacity-75 transition-opacity"
        aria-hidden="true"
      ></div>

      <!-- This element is to trick the browser into centering the modal contents. -->
      <span
        class="hidden sm:inline-block sm:align-middle sm:h-screen"
        aria-hidden="true"
        >&#8203;</span
      >

      <!--
      Modal panel, show/hide based on modal state.

      Entering: "ease-out duration-300"
        From: "opacity-0 translate-y-4 sm:translate-y-0 sm:scale-95"
        To: "opacity-100 translate-y-0 sm:scale-100"
      Leaving: "ease-in duration-200"
        From: "opacity-100 translate-y-0 sm:scale-100"
        To: "opacity-0 translate-y-4 sm:translate-y-0 sm:scale-95"
    -->
      <div
        class="inline-block align-bottom bg-white rounded-lg text-left overflow-hidden shadow-xl transform transition-all sm:my-8 sm:align-middle sm:max-w-lg sm:w-full"
      >
        <div class="bg-white px-4 pt-5 pb-4 sm:p-6 sm:pb-4">
          <div class="sm:flex sm:items-start">
            <div
              class="mx-auto flex-shrink-0 flex items-center justify-center h-12 w-12 rounded-full bg-red-100 sm:mx-0 sm:h-10 sm:w-10"
            >
              <!-- Heroicon name: outline/exclamation -->
              <svg
                class="h-6 w-6 text-red-600"
                xmlns="http://www.w3.org/2000/svg"
                fill="none"
                viewBox="0 0 24 24"
                stroke="currentColor"
                aria-hidden="true"
              >
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  stroke-width="2"
                  d="M12 9v2m0 4h.01m-6.938 4h13.856c1.54 0 2.502-1.667 1.732-3L13.732 4c-.77-1.333-2.694-1.333-3.464 0L3.34 16c-.77 1.333.192 3 1.732 3z"
                />
              </svg>
            </div>
            <div class="mt-3 text-center sm:mt-0 sm:ml-4 sm:text-left">
              <h3
                class="text-lg leading-6 font-medium text-gray-900"
                id="modal-title"
              >
                Deactivate account
              </h3>
              <div class="mt-2">
                <p class="text-sm text-gray-500">
                  Are you sure you want to deactivate your account? All of your
                  data will be permanently removed. This action cannot be
                  undone.
                </p>
              </div>
            </div>
          </div>
        </div>
        <div class="bg-gray-50 px-4 py-3 sm:px-6 sm:flex sm:flex-row-reverse">
          <button
            type="button"
            class="w-full inline-flex justify-center rounded-md border border-transparent shadow-sm px-4 py-2 bg-red-600 text-base font-medium text-white hover:bg-red-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-red-500 sm:ml-3 sm:w-auto sm:text-sm"
          >
            Deactivate
          </button>
          <button
            type="button"
            class="mt-3 w-full inline-flex justify-center rounded-md border border-gray-300 shadow-sm px-4 py-2 bg-white text-base font-medium text-gray-700 hover:bg-gray-50 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500 sm:mt-0 sm:ml-3 sm:w-auto sm:text-sm"
            @click="show = false"
          >
            Cancel
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      show: false,
    };
  },
};
</script>
