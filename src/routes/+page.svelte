<script lang="ts">
	import { sayings } from '../globals';

	let filter: string = '';

	$: filteredSayings = filter
		? sayings.filter((saying) => saying.base.toLowerCase().includes(filter.toLowerCase()))
		: sayings;
</script>

<section class="w-full bg-black inline-block text-white py-2 text-center px-10 lg:px-0">
	Queres adicionar algum? Manda uma DM a um destes bebados: <a
		class="underline mx-[0.125rem] text-blue-500"
		target="_blank"
		href="https://twitter.com/joaomendoncaaaa">joao</a
	>
	ou
	<a
		class="text-blue-500 underline mx-[0.125rem]"
		target="_blank"
		href="https://twitter.com/paidoviegas">ruben</a
	>
</section>
<header
	class="flex flex-col items-center justify-between container mx-auto py-4 px-8 gap-4 sm:flex-row sm:px-0"
>
	<h1>nome/logo</h1>
	<div>
		<input
			bind:value={filter}
			class="border border-gray-500 rounded-md p-2"
			placeholder="Pesquisa provérbios"
		/>
		<span>{filteredSayings.length} encontrados</span>
	</div>
	<a href="https://www.google.com">link util</a>
</header>
<div class="container mx-auto my-4 flex gap-8 flex-col px-8 sm:px-0">
	{#each filteredSayings as saying}
		<div class="flex flex-col items-center">
			<span class="line-through text-gray-400">{saying.base}</span>
			<span class="text-xl">{saying.alt}</span>
		</div>
	{/each}
</div>
