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
              <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5"
                stroke="currentColor" class="w-6 h-6 stroke-1">
                <path stroke-linecap="round" stroke-linejoin="round"
                  d="M15.75 17.25v3.375c0 .621-.504 1.125-1.125 1.125h-9.75a1.125 1.125 0 01-1.125-1.125V7.875c0-.621.504-1.125 1.125-1.125H6.75a9.06 9.06 0 011.5.124m7.5 10.376h3.375c.621 0 1.125-.504 1.125-1.125V11.25c0-4.46-3.243-8.161-7.5-8.876a9.06 9.06 0 00-1.5-.124H9.375c-.621 0-1.125.504-1.125 1.125v3.5m7.5 10.375H9.375a1.125 1.125 0 01-1.125-1.125v-9.25m12 6.625v-1.875a3.375 3.375 0 00-3.375-3.375h-1.5a1.125 1.125 0 01-1.125-1.125v-1.5a3.375 3.375 0 00-3.375-3.375H9.75" />
              </svg>
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
