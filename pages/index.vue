<template>
  <div
    class="
      relative
      flex
      items-top
      justify-center
      min-h-screen
      bg-gray-100
      sm:items-center sm:pt-0
    "
  >
    <div class="max-w-4xl mx-auto sm:px-6 lg:px-8 mb-8">
      <h1
        class="
          text-center
          mt-10
          text-3xl
          leading-9
          font-extrabold
          text-gray-900
        "
      >
        Manage image animations in Nuxt.js
      </h1>
      <div class="mt-8 bg-white overflow-hidden shadow sm:rounded-lg p-6">
        <h2 class="text-lg leading-6 font-medium text-gray-900">
          Class-based Animations
        </h2>
        <div :class="{ shake }">
          <button
            @click="activateShakeAnimation"
            class="
              bg-transparent
              hover:bg-blue-500 hover:text-white
              py-2
              px-4
              border border-blue-500
              hover:border-transparent
              rounded-full
              mt-3
            "
          >
            Click me, I will shake!
          </button>
          <span v-if="shake">This is a shake animation feature!</span>
        </div>
      </div>
      <div class="mt-8 bg-white overflow-hidden shadow sm:rounded-lg p-6">
        <h2 class="text-lg leading-6 font-medium text-gray-900">
          State-driven Animations
        </h2>
        <div
          @mousemove="onMousemove"
          :style="{ backgroundColor: `hsl(${state}, 40%, 50%)` }"
          class="
            movearea
            w-full
            h-full
            flex
            justify-center
            items-center
            mt-3
            py-6
            px-4
            border border-gray-500
          "
        >
          <p class="text-center text-white text-l">
            Move the mouse to change the color!
          </p>
        </div>
      </div>
      <div class="mt-8 bg-white overflow-hidden shadow sm:rounded-lg p-6">
        <h2 class="text-lg leading-6 font-medium text-gray-900">
          Built-in Transition (Toggle & Fade)
        </h2>
        <button
          @click="tFade = !tFade"
          class="
            bg-transparent
            hover:bg-blue-500 hover:text-white
            py-2
            px-4
            border border-blue-500
            hover:border-transparent
            rounded-full
            mt-3
          "
        >
          Click me, I will toggle + Fade!
        </button>
        <Transition>
          <p v-if="tFade" class="text-dark text-l mt-3">
            This is a built-in transition feature!
          </p>
        </Transition>
      </div>
      <div class="mt-8 bg-white overflow-hidden shadow sm:rounded-lg p-6">
        <h2 class="text-lg leading-6 font-medium text-gray-900">
          CSS Transitions (Slide & Fade)
        </h2>
        <button
          @click="sFade = !sFade"
          class="
            bg-transparent
            hover:bg-blue-500 hover:text-white
            py-2
            px-4
            border border-blue-500
            hover:border-transparent
            rounded-full
            mt-3
          "
        >
          Click me to toggle Slide + Fade!
        </button>
        <Transition name="slide-fade">
          <p v-if="sFade" class="text-dark text-l mt-3">
            This is a CSS transition feature!
          </p>
        </Transition>
      </div>
      <div class="mt-8 bg-white overflow-hidden shadow sm:rounded-lg p-6">
        <h2 class="text-lg leading-6 font-medium text-gray-900">
          CSS Animations (Bounce)
        </h2>
        <button
          @click="bounce = !bounce"
          class="
            bg-transparent
            hover:bg-blue-500 hover:text-white
            py-2
            px-4
            border border-blue-500
            hover:border-transparent
            rounded-full
            mt-3
          "
        >
          Click me to toggle Bounce!
        </button>
        <Transition name="bounce">
          <p v-if="bounce" class="text-dark text-l mt-3">
            This is a CSS animation feature!
          </p>
        </Transition>
      </div>
      <div class="mt-8 bg-white overflow-hidden shadow sm:rounded-lg p-6">
        <h2 class="text-lg leading-6 font-medium text-gray-900">
          Custom Transition Classes
        </h2>
        <button
          @click="show = !show"
          class="
            bg-transparent
            hover:bg-blue-500 hover:text-white
            py-2
            px-4
            border border-blue-500
            hover:border-transparent
            rounded-full
            mt-3
          "
        >
          Click me to toggle!
        </button>
        <Transition
          name="custom-classes"
          enter-active-class="animate__animated animate__tada"
          leave-active-class="animate__animated animate__bounceOutRight"
        >
          <p v-if="show" class="text-dark text-l mt-3">
            This is a custom transition feature!
          </p>
        </Transition>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "IndexPage",

  data() {
    return {
      shake: false,
      state: 0,
      tFade: false,
      sFade: false,
      bounce: false,
      show: false,
    };
  },

  methods: {
    activateShakeAnimation() {
      this.shake = true;
      setTimeout(() => {
        this.shake = false;
      }, 1500);
    },

    onMousemove(e) {
      this.state = e.clientX;
    },
  },
};
</script>

<style scoped>
/* Custom Transition Classes starts here */
@import "https://cdnjs.cloudflare.com/ajax/libs/animate.css/4.1.1/animate.min.css";
/* Custom Transition Classes end here */

/* Shake animation starts here */
.shake {
  animation: shake 0.82s cubic-bezier(0.36, 0.07, 0.19, 0.97) both;
  transform: translate3d(0, 0, 0);
}

@keyframes shake {
  10%,
  90% {
    transform: translate3d(-1px, 0, 0);
  }

  20%,
  80% {
    transform: translate3d(2px, 0, 0);
  }

  30%,
  50%,
  70% {
    transform: translate3d(-4px, 0, 0);
  }

  40%,
  60% {
    transform: translate3d(4px, 0, 0);
  }
}
/* Shake animation end here */

/* ////////////////////////////////////////////////////////////////////////////////////////////// */

/* State-driven Animations starts here */
.movearea {
  transition: 0.3s background-color ease;
}
/* State-driven Animations end here */

/* ////////////////////////////////////////////////////////////////////////////////////////////// */

/* Built-in Transition (Toggle) starts here */
.v-enter-active,
.v-leave-active {
  transition: opacity 0.7s ease;
}

.v-enter-from,
.v-leave-to {
  opacity: 0;
}
/* Built-in Transition (Toggle) end here */

/* ////////////////////////////////////////////////////////////////////////////////////////////// */

/* CSS Transitions (Slide & Fade) starts here */
.slide-fade-enter-active {
  transition: all 0.4s ease-out;
}

.slide-fade-leave-active {
  transition: all 0.9s cubic-bezier(1, 0.5, 0.8, 1);
}

.slide-fade-enter-from,
.slide-fade-leave-to {
  transform: translateX(20px);
  opacity: 0;
}

/* CSS Transitions (Slide & Fade) end here */

/* ////////////////////////////////////////////////////////////////////////////////////////////// */

/* CSS Animations (Bounce) starts here */

.bounce-enter-active {
  animation: bounce-in 0.5s;
}
.bounce-leave-active {
  animation: bounce-in 0.5s reverse;
}
@keyframes bounce-in {
  0% {
    transform: scale(0);
  }
  50% {
    transform: scale(1.25);
  }
  100% {
    transform: scale(1);
  }
}

/* CSS Animations (Bounce) end here */

/* ////////////////////////////////////////////////////////////////////////////////////////////// */
</style>
