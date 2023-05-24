<script>
	import { onMount } from 'svelte';
	let uploader;

	onMount(() => {
		// list.set([...$list, { type: 'bootstrap', desc: 'upload your bootstrap documents' }]);
		uploader.addEventListener('change', async () => {
			const data = new FormData();
			for (const file of uploader.files) {
				data.append('files', file);
			}
			const res = await fetch('http://localhost:8000/bootstrap', {
				method: 'POST',
				body: data,
			});
			const j = await res.json();
			console.log(j);
		});
	});
</script>

<input
	id="fileInput"
	type="file"
	style="display:none;"
	multiple="multiple"
	bind:this={uploader}
	accept=".txt"
/>
<input
	type="button"
	value="选择文件"
	class="btn btn-sm"
	onclick="document.getElementById('fileInput').click();"
/>
