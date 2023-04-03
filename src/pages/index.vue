<script setup lang="ts">
defineOptions({
  name: 'IndexPage',
})

const poem = $ref('欲买桂花同载酒，终不似，少年游')
const reference = $ref('《唐多令 · 芦叶满汀洲》')

let isCopyDone = $ref(false)

function onClick() {
  navigator.clipboard.writeText(poem)

  if (!isCopyDone) {
    isCopyDone = true
    setTimeout(() => {
      isCopyDone = false
    }, 1800)
  }
}
</script>

<template>
  <div h-full flex items-center justify-center>
    <div>
      <div
        w-auto px-4 py-0.5 cursor-pointer rounded-md
        lg:text-14 md:text-10 sm:text-8
        transition transition-all duration-300
        class="hover:bg-coolGray/20"
        @click="onClick"
      >
        <Transition name="fit" mode="out-in">
          <div v-if="!isCopyDone">
            <TheSentence>
              <span
                text-shadow font-bold
                class="sentence"
              >
                {{ poem }}
              </span>
            </TheSentence>
          </div>
          <template v-else>
            <div i-carbon-ai-status-complete class="w-10 h-10 inline-block" />
          </template>
        </Transition>
      </div>

      <div my-2 />

      <div lg:text-6 text-4 class="text-amber/70">
        <TheSentence>
          <span tracking-widest class="sentence">{{ reference }}</span>
        </TheSentence>
      </div>
    </div>
  </div>
</template>

<style scoped>
.sentence {
  --at-apply: antialiased text-center;
}

.fit-enter-active,
.fit-leave-active {
  transition: all 0.3s ease;
}

.fit-enter-from,
.fit-leave-to {
  opacity: 0;
  transform: scale(0.7);
}
</style>
