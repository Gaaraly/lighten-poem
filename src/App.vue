<template>
  <main h-screen font-serif bg-black flex="~ col" text="center gray-200">
    <div h-10 w-full class="line" style="--i:-1" />
    <RouterView />
    <div h-10 w-full class="line" style="--i:1" />
  </main>
</template>

<style>
.line {
  background: linear-gradient(45deg, #27272A 10%, transparent 10%,
    transparent 50%, #27272A 50%, #27272A 60%, transparent 60%, transparent 100%);
  background-size: 40px 40px;
  animation: scroll 0.5s linear infinite;
}

@keyframes scroll {
  0% {
    background-position: 0;
  }
  100% {
    background-position: calc(var(--i) * 40px);
  }
}
</style>
