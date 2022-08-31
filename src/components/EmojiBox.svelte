<script lang="ts">
    export let emoji: string;
</script>
<div class="bg-[#F6F5F2] w-72 grid py-4 gap-y-4 px-2 justify-items-center">
    <div class="text-3xl">{emoji}</div>
    <p class="text-center">
<slot></slot>
    </p>
</div>