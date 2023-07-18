<script setup>
import * as math from 'mathjs';

import HelloWorld from "./components/HelloWorld.vue";
import TheWelcome from "./components/TheWelcome.vue";


</script>

<template>
  <div class="mx-auto overflow-hidden mt-10 shadow-lg mb-2 bg-purple-900 border rounded-lg lg:w-2/6 md:w-3/6 sm:w-4/6">
    <div class="">
      <div class="p-5 text-white text-center text-3xl bg-purple-900">
        <span class="text-orange-500">Calcu</span>lator
      </div>
      <div class="pt-16 p-5 pb-0 text-white text-right text-3xl bg-purple-800" @paste="handlePaste"
        @keydown.enter.prevent="calculate" contenteditable="true">
        <span class="text-orange-500">{{ screenDisplay }}</span>
      </div>


      <div class="flex items-stretch bg-purple-900 h-24">
        <div class="flex-1 px-2 py-2 justify-center flex items-center text-white text-2xl font-semibold">
          <button @click="updateScreen('%')"
            class="rounded-full cursor-default h-20 w-20 flex items-center bg-purple-800 justify-center shadow-lg border-2 border-purple-700 hover:border-2 hover:border-gray-500 focus:outline-none">
            %
          </button>
        </div>

        <div class="flex-1 px-2 py-2 justify-center flex items-center text-white text-2xl font-semibold">
          <button @click="updateScreen('(')"
            class="rounded-full cursor-default h-20 w-20 flex items-center bg-purple-800 justify-center shadow-lg border-2 border-purple-700 hover:border-2 hover:border-gray-500 focus:outline-none">
            (
          </button>
        </div>

        <div class="flex-1 px-2 py-2 justify-center flex items-center text-white text-2xl font-semibold">
          <button @click="updateScreen(')')"
            class="rounded-full h-20 w-20 flex cursor-default items-center bg-purple-800 justify-center shadow-lg border-2 border-purple-700 hover:border-2 hover:border-gray-500 focus:outline-none">
            )
          </button>
        </div>

        <div class="flex-1 px-2 py-2 justify-center flex items-center text-white text-2xl font-semibold">
          <button @click="updateScreen('÷')"
            class="rounded-full h-20 w-20 flex items-center cursor-default bg-purple-800 justify-center shadow-lg border-2 border-purple-700 hover:border-2 hover:border-gray-500 focus:outline-none">
            ÷
          </button>
        </div>
      </div>

      <div class="flex items-stretch bg-purple-900 h-24">
        <div class="flex-1 px-2 py-2 justify-center flex items-center  text-white text-2xl font-semibold">
          <button @click="updateScreen('7')"
            class=" rounded-full h-20 w-20 flex items-center cursor-default bg-purple-800 justify-center shadow-lg border-2 border-purple-700 hover:border-2 hover:border-gray-500 focus:outline-none">
            7
          </button>
        </div>

        <div class="flex-1 px-2 py-2 justify-center flex items-center text-white text-2xl font-semibold">
          <button @click="updateScreen('8')"
            class="rounded-full h-20 w-20 flex items-center bg-purple-800 cursor-default justify-center shadow-lg border-2 border-purple-700 hover:border-2 hover:border-gray-500 focus:outline-none">
            8
          </button>
        </div>

        <div class="flex-1 px-2 py-2 justify-center flex items-center text-white text-2xl font-semibold">
          <button @click="updateScreen('9')"
            class="rounded-full h-20 w-20 flex items-center bg-purple-800 justify-center cursor-default shadow-lg border-2 border-purple-700 hover:border-2 hover:border-gray-500 focus:outline-none">
            9
          </button>
        </div>

        <div class="flex-1 px-2 py-2 justify-center flex items-center text-white text-2xl font-semibold">
          <button @click="updateScreen('×')"
            class="rounded-full h-20 w-20 flex items-center bg-purple-800 justify-center shadow-lg border-2 cursor-default border-purple-700 hover:border-2 hover:border-gray-500 focus:outline-none">
            ×
          </button>
        </div>
      </div>

      <div class="flex items-stretch bg-purple-900 h-24">
        <div class="flex-1 px-2 py-2 justify-center flex items-center text-white text-2xl font-semibold">
          <button @click="updateScreen('4')"
            class="rounded-full h-20 w-20 flex items-center bg-purple-800 justify-center shadow-lg cursor-default border-2 border-purple-700 hover:border-2 hover:border-gray-500 focus:outline-none">
            4
          </button>
        </div>

        <div class="flex-1 px-2 py-2 justify-center flex items-center text-white text-2xl font-semibold">
          <button @click="updateScreen('5')"
            class="rounded-full h-20 w-20 flex items-center bg-purple-800 justify-center shadow-lg border-2 cursor-default border-purple-700 hover:border-2 hover:border-gray-500 focus:outline-none">
            5
          </button>
        </div>

        <div class="flex-1 px-2 py-2 justify-center flex items-center text-white text-2xl font-semibold">
          <button @click="updateScreen('6')"
            class="rounded-full h-20 w-20 flex items-center bg-purple-800 justify-center shadow-lg border-2 cursor-default border-purple-700 hover:border-2 hover:border-gray-500 focus:outline-none">
            6
          </button>
        </div>

        <div class="flex-1 px-2 py-2 justify-center flex items-center text-white text-2xl font-semibold">
          <button @click="updateScreen('-')"
            class="rounded-full h-20 w-20 flex items-center bg-purple-800 justify-center shadow-lg border-2 cursor-default border-purple-700 hover:border-2 hover:border-gray-500 focus:outline-none">
            -
          </button>
        </div>
      </div>

      <div class="flex items-stretch bg-purple-900 h-24">
        <div class="flex-1 px-2 py-2 justify-center flex items-center text-white text-2xl font-semibold">
          <button @click="updateScreen('1')"
            class="rounded-full h-20 w-20 flex items-center bg-purple-800 justify-center cursor-default shadow-lg border-2 border-purple-700 hover:border-2 hover:border-gray-500 focus:outline-none">
            1
          </button>
        </div>

        <div class="flex-1 px-2 py-2 justify-center flex items-center text-white text-2xl font-semibold">
          <button @click="updateScreen('2')"
            class="rounded-full h-20 w-20 flex items-center bg-purple-800 justify-center shadow-lg border-2 cursor-default border-purple-700 hover:border-2 hover:border-gray-500 focus:outline-none">
            2
          </button>
        </div>

        <div class="flex-1 px-2 py-2 justify-center flex items-center text-white text-2xl font-semibold">
          <button @click="updateScreen('3')"
            class="rounded-full h-20 w-20 flex items-center cursor-default bg-purple-800 justify-center shadow-lg border-2 border-purple-700 hover:border-2 hover:border-gray-500 focus:outline-none">
            3
          </button>
        </div>

        <div class="flex-1 px-2 py-2 justify-center flex items-center text-white text-2xl font-semibold">
          <button @click="updateScreen('+')"
            class="rounded-full h-20 w-20 flex items-center bg-purple-800 cursor-default justify-center shadow-lg border-2 border-purple-700 hover:border-2 hover:border-gray-500 focus:outline-none">
            +
          </button>
        </div>
      </div>

      <div class="flex items-stretch bg-purple-900 h-24 mb-4">
        <div class="flex-1 px-2 py-2 justify-center flex items-center text-white text-2xl font-semibold">
          <!-- AC button -->
          <button @click="clearAll"
            class="rounded-full h-12 w-12 flex items-center bg-red-500 justify-center shadow-lg border-2 border-red-700 hover:border-2 hover:border-gray-500 focus:outline-none">
            AC
          </button>
        </div>

        <div class="flex-1 px-2 py-2 justify-center flex items-center text-white text-2xl font-semibold">
          <!-- C button -->
          <button @click="clearScreen"
            class="rounded-full h-12 w-12 flex items-center bg-red-500 justify-center shadow-lg border-2 border-red-700 hover:border-2 hover:border-gray-500 focus:outline-none">
            C
          </button>
        </div>

        <div class="flex-1 px-2 py-2 justify-center flex items-center text-white text-2xl font-semibold">
          <button @click="updateScreen('0')"
            class="rounded-full h-20 w-20 flex items-center bg-purple-800 justify-center shadow-lg cursor-default border-2 border-purple-700 hover:border-2 hover:border-gray-500 focus:outline-none">
            0
          </button>
        </div>

        <div class="flex-1 px-2 py-2 justify-center flex items-center text-white text-2xl font-semibold">
          <button
            class="rounded-full h-20 w-20 flex items-center bg-purple-800 justify-center shadow-lg border-2 cursor-default border-purple-700 hover:border-2 hover:border-gray-500 focus:outline-none">
            .
          </button>
        </div>

        <div class="flex-1 px-2 py-2 justify-center flex items-center text-white text-2xl font-semibold">
          <button @click="calculate"
            class="rounded-full h-20 w-20 flex items-center bg-orange-500 justify-center shadow-lg border-2 cursor-default border-purple-700 hover:border-2 hover:border-gray-500 focus:outline-none">
            =
          </button>
        </div>
      </div>
    </div>
  </div>
  <!-- <header>
    <img alt="Vue logo" class="logo" src="./assets/logo.svg" width="125" height="125" />

    <div class="wrapper">
      <HelloWorld msg="You did it!" />
    </div>
  </header>

  <main>
    <TheWelcome />
  </main> -->
</template>

<script>
export default {
  data() {
    return {
      screenDisplay: '0', // Initial screen display value
      hasResult: false // Flag to indicate if the calculation has been performed
    };
  },
  methods: {
    updateScreen(value) {
      if (this.hasResult) {
        if (value === 'AC') {
          // Clear the screen and reset the calculator
          this.screenDisplay = '0';
          this.hasResult = false;
        } else {
          // Start a new calculation with the previous result
          this.screenDisplay = this.screenDisplay + value;
          this.hasResult = false;
        }
      } else if (this.screenDisplay === '0') {
        // If the screen is cleared, replace '0' with the new value
        this.screenDisplay = value;
      } else {
        // Append the new value to the existing screen display
        this.screenDisplay += value;
      }
    },

    clearScreen() {
      if (this.screenDisplay.length > 1) {
        this.screenDisplay = this.screenDisplay.slice(0, -1);
      } else {
        this.screenDisplay = '0';
        this.hasResult = false;
      }
    },
    clearAll() {
      this.screenDisplay = '0';
      this.hasResult = false;
    },
    calculate() {
      try {
        let expression = this.screenDisplay.replace(/×/g, '*').replace(/÷/g, '/');
        const result = math.evaluate(expression);
        this.screenDisplay = String(result);
        this.hasResult = true;
      } catch (error) {
        this.screenDisplay = 'Error';
        this.hasResult = true;
      }
    },
    handlePaste(event) {
      event.preventDefault();
      const pastedText = event.clipboardData.getData('text/plain');
      const numbersOnly = pastedText.replace(/[^0-9]/g, '');
      this.screenDisplay = numbersOnly;
    },
    focusInput() {
      this.$refs.screen.focus();
    }
  }
};
</script>
<style scoped>
/* header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
} */
</style>
