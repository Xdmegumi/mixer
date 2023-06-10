<script lang="ts">
  import Start from "./Start.svelte";
  import Player from "./Player.svelte";

  import { appStarted, currentSong } from "../stores";
  import { downloadTracks } from "../tracks";
  import { capitalise } from "../utils";
  import Loading from "./Loading.svelte";
  import Footer from "./Footer/Footer.svelte";
  import Modal from "./SongList/Modal.svelte";
</script>

<svelte:head>
  <title>{capitalise($currentSong.song)}</title>
</svelte:head>

<main class="bg-black h-fit min-h-screen relative">
  <div class="fixed flex w-full justify-between">
    <div class="m-2 md:m-6">
      <a
        class="w-5"
        href=""
        target="_blank"
        rel="noreferrer"
        ><img
          src="https://s2.loli.net/2023/06/10/JknT5QRC7uAfNZI.png"
          alt="Happy Bithday!"
          class="w-28 md:h-[32px] md:w-[32px]"
        /></a
      >
    </div>

    <Modal />
  </div>

  {#await downloadTracks($currentSong)}
    <Loading />
  {:then tracks}
    {#if $appStarted}
      <Player {tracks} />
    {:else}
      <Start />
    {/if}
  {/await}

  <Footer />
</main>
