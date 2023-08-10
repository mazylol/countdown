<script lang="ts">
  let countDownDate = new Date("August 12, 2023 10:30:00").getTime();

  let done = false;

  let days: number;
  let hours: number;
  let minutes: number;
  let seconds: number;

  let x = setInterval(function() {
    let now = new Date().getTime();

    let distance = countDownDate - now;

    days = Math.floor(distance / (1000 * 60 * 60 * 24));
    hours = Math.floor((distance %  (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
    minutes = Math.floor((distance % (1000 * 60 * 60)) / (1000 * 60));
    seconds = Math.floor((distance % (1000 * 60)) / 1000);

    if (distance < 0) {
      clearInterval(x);
      done = true;
    }
  });

  let hue = 0;

  setInterval(() => {
    hue++;
  }, 25);
</script>

<div style="--hue: {hue}" class="text-center min-h-screen" class:rainbow={done}>
  <div class="pt-[40vh]">
    {#if !done}
    <p class="text-8xl font-bold">{days}d {hours}h {minutes}m {seconds}s</p>
  {:else}
    <p class="text-7xl font-extrabold">GREAT DANE TIME GOGOGOGOGOGOGO</p>
  {/if}
  </div>
</div>

<style>
  .rainbow {
    background-color: hsl(var(--hue), 100%, 50%);
  }
</style>