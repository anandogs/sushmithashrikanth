<script lang="ts">
  export let heading:string
  export let content:boolean = true
</script>

<div class="grid">
  <div class="flex">
    <div
      class="top-0 border-black border-2 bg-white w-72 grid py-4 gap-y-4 px-2"
    >
      <h3 class="pl-2">{heading}</h3>
      {#if content}
      <div class="border-black border-2 bg-[#F6F5F2] mx-4 px-2 py-3">
        <slot></slot>
      </div>
      {/if}
    </div>
    <div class="w-1 bg-black mt-1" />

  </div>
  <div class="h-1 bg-black ml-1" />
</div>
