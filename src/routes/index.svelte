<script>
	import SearchFilter from '$lib/SearchFilter.svelte';
	import Field from '$lib/Field.svelte';
	import Modal from '$lib/Modal.svelte';
	import Markdown from '$lib/Markdown.svelte';
	import Portal from '$lib/Portal.svelte';
	import Toast from '$lib/toast/Toast.svelte';
	import { toast } from '$lib/toast/toast';
	import Toggle from '$lib/Toggle.svelte';
	import Accordion from '$lib/Accordion.svelte';

	let isToggled = false;
	let isModalOpen = false;

	let text = '# hi';

	let search = '';
	let items = ['scott', 'noam', 'daniel', 'adva', 'loren', 'aviv'];
</script>

<h1>Svelte UI Components {search}</h1>

<!-- Markdown Component -->
<Markdown bind:text />

<!-- Modal & Field Components -->
<Modal bind:isModalOpen background={true}>
	<div style="background: white; box-shadow: 1px 1px 4px rgba(0, 0, 0, 0.3);">
		<Field bind:value={search} label="Search" instructions="Type to search" placholder="Joe" />
		<Field value={0} label="Number" type="number" />
	</div>
</Modal>

<button
	on:click={() => {
		isModalOpen = true;
	}}>Open Modal Form</button
>

<!-- Toast Component -->
<Toast duration={4000} />
<button on:click={() => toast.send(' New Message ' + Math.random())}>New Toast</button>

<!-- Search Filter Component -->
<h1>Search Filter</h1>
<SearchFilter {items} bind:search />

<!-- Accordio Component -->
<h1>Accordion</h1>
<Accordion isOpen={false} buttonText="Open Accordion">
	<div>
		<p>
			Lorem ipsum dolor sit, amet consectetur adipisicing elit. Magni ab similique, ratione non
			magnam facere deserunt temporibus quas cum dolorem ipsa officia quod culpa minima. Animi nisi
			nemo sint asperiores.
		</p>
	</div>
</Accordion>

<!-- Toggle Component -->
<h1>Toggle</h1>
<Toggle bind:isToggled label="Beta" />
<Toggle bind:isToggled label="Beta" style="--toggleBackgroundColor: red;" />

{#if isToggled}
	<h1>I'm Toggled!</h1>
{/if}
