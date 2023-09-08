<script setup lang="ts">
  useHead({
    title: 'Beshiefy Me | Bakit 🤸‍♂️ malungkot 🤸‍♂️ ang 🤸‍♂️ beshie 🤸‍♂️ ko?',
    link: [{ rel: 'icon', href: './cartwheel.svg' }],
  })

  const userInput = ref('')
  const emojis = ref(['🤸‍♂️', '🤸', '❤', '🛒', '👌', '😀', '⭐', '😍', '⚡', '👍', '🙌', '✌', '🤣'])
  const selectedEmoji = ref('🤸‍♂️')
  const beshified = computed(() => {
    return userInput.value.replaceAll(' ', ` ${selectedEmoji.value} `)
  })

  const copyToClipboard = () => {
    navigator.clipboard.writeText(beshified.value)
  }
</script>

<template>
  <section class="container mx-auto flex justify-center h-screen">
    <div class="my-auto max-w-min">
      <div class="flex flex-col flex-wrap gap-2">
        <div class="flex flex-col gap-2">
          <div class="text-purple-800 font-medium mx-auto">
            ✨ Beshiefy Me ✨
          </div>

          <div class="flex flex-row gap-0">
            <input type="text"
              class="w-auto placeholder:text-gray-200 text-sm border-r-0 rounded-md rounded-r-none border-gray-200 transition focus:border-purple-200 focus:ring focus:ring-purple-200 focus:ring-opacity-50"
              spellcheck="false" placeholder="Bakit malungkot ang beshie ko?" v-model="userInput">

            <select
              class="border-l-0 rounded-md rounded-l-none border-gray-200 transition focus:border-purple-200 focus:ring focus:ring-purple-200 focus:ring-opacity-50"
              v-model="selectedEmoji">
              <option v-for="emoji in emojis" :value="emoji">
                {{ emoji }}
              </option>
            </select>
          </div>
        </div>

        <Transition>
          <div class="w-full bg-indigo-50 p-2 rounded-md" v-if="beshified">
            <p class="text-xs">
              {{ beshified }}
            </p>
          </div>
        </Transition>

        <Transition>
          <div class="mx-auto" v-if="beshified">
            <button class="bg-purple-50 p-2 rounded-md transition active:scale-95" @click="copyToClipboard">
              <IconCopy />
            </button>
          </div>
        </Transition>

      </div>
    </div>
  </section>
  <footer class="container mx-auto flex justify-center">
    <div class="flex flex-col ">
      <p class="text-sm">
        Bryan Olandres
      </p>
      <a class="text-xs mx-auto hover:underline" href="https://github.com/veib6247/beshiefy-me" target="_blank">
        Github
      </a>
    </div>
  </footer>
</template>

<style>
.v-enter-active,
.v-leave-active {
  transition: opacity 0.3s ease;
}

.v-enter-from,
.v-leave-to {
  opacity: 0;
}
</style>
