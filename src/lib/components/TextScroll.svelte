<script lang="ts">

  let {height, progress}: {height: number, progress: number} = $props()
</script>

<div style="height: {height * 100}vh;">
  <p>This is a demo that is exactly {height} screens</p>
  <p>Progress: {progress}</p>
</div>


