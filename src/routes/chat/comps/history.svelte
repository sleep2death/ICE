<script>
	import { onMount } from 'svelte';
	import { writable } from 'svelte/store';
	import Uploader from './uploader.svelte';
	let list = writable([]);
</script>

<div class="w-full h-full bg-yellow-100 relative">
	<div class="flex flex-col w-full p-2">
		{#if $list.length > 0}
			{#each $list as item}
				<button class="btn w-fit btn-sm">上传启动文档</button>
			{/each}
		{:else}
			<div class="w-full h-full absolute flex flex-col justify-center items-center space-y-4">
				<div class="text text-sm">新对话，请上传启动文档</div>
        <Uploader/>
			</div>
		{/if}
	</div>
</div>
