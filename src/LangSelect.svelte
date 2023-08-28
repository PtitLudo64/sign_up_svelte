<script>
	import {texts} from './Texts.svelte';
    import {createEventDispatcher} from 'svelte';

    const dispatch = createEventDispatcher();
	const Logo = "../assets/img/C_logo.svg";

    
	let id = 0;
	let globalTexts = texts[id].h1;

	const changeTexts = () => {
		globalTexts = texts[id];
        dispatch('chgTexts', {globalTexts});
	}

</script>


	<select name="lang" id="lang-select" bind:value={id} on:change={changeTexts}>
		{#each texts as t}
			<option value={t.id}>
				{t.lang}
			</option>
		{/each}
	</select>



<style>
	#lang-select {
		/* position: absolute;
        right: 20px; */
        border: none;
        outline: none;
        background-color: var(--clr-neutral);
        color: var(--clr-accent_400);
	}
</style>