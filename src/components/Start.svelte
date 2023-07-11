<script lang="ts">
  import { appStarted } from "../stores";

  const handleClick = () => appStarted.set(true);
</script>

<div on:click={handleClick} class="flex h-screen w-full">
  <p style="font-family: 'Microsoft YaHei', sans-serif;" class="text-1xl md:text-2xl m-auto cursor-pointer">唤醒</p>
</div>
