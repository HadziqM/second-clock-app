<script lang="ts">

  import { onMount } from 'svelte';

  function parse(i:number) {
    if (i<10){
      return "0"+String(i)
    }
    return String(i)
  }

  let time = new Date();
  $: hours = parse(time.getHours())
  $: minute = parse(time.getMinutes())
  $: second = parse(time.getSeconds())
  onMount(() => {
		const interval = setInterval(() => {
			time = new Date();
		}, 1000);

		return () => {
			clearInterval(interval);
		};
	});
</script>

<div data-tauri-drag-region class="con">
  <div class="ho"><p>{hours}</p></div>
  <div class="sep">:</div>
  <div class="min"><p>{minute}</p></div>
  <div class="sec"><p>{second}</p></div>
</div>
<style>
  .con{
    position:relative;
    display: block;
    top: 0;
    left: 0;
    width: 100vw;
    height: 100vh;
    user-select:none;
    cursor:pointer;
  }
  .con div{
    position: absolute;
    display: flex;
    padding: 0;
    margin: 0;
    justify-content: center;
    align-items: center;
    width: 5rem;
    height: fit-content;
    z-index: 1000;
    top: 25vh;
    font-size: 2.3rem;
    color: white;
    transform: scale(0.6,1);
  }
  .con p{
    padding: 0;
    margin: 0;
  }
  .ho{
    right: 57vw !important;
  }
  .sep{
    left: 35.5vw !important;
    top:24vw !important;
    width: 0.5rem !important;
  }
  .min{
    left:31vw !important;
  }
  .sec{
    left:44vw !important;
    top:30vh !important;
    font-size: 1.7rem !important;
  }
</style>

