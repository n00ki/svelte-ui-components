<script>
	import { fly, fade } from 'svelte/transition';
	import { flip } from 'svelte/animate';
	import Portal from '../Portal.svelte';
	import ToastMessage from './ToastMessage.svelte';
	import { toast } from './toast';

	export let duration;
</script>

<Portal>
	<div class="toast-wrapper">
		{#each $toast as message (message)}
			<div
				on:click={toast.remove}
				in:fly={{ opacity: 0, x: 100 }}
				out:fade
				animate:flip
				class="toast"
			>
				<ToastMessage {message} {duration} />
			</div>
		{/each}
	</div>
</Portal>

<style>
	.toast-wrapper {
		position: fixed;
		bottom: 0;
		right: 20px;
	}
	.toast {
		background: white;
		margin-bottom: 1rem;
		padding: 20px;
		border-radius: 15px;
		box-shadow: 1px 1px 4px rgba(0, 0, 0, 0.3);
	}
</style>
