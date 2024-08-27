<script>
	import '../app.postcss';
	import { AppShell, AppBar } from '@skeletonlabs/skeleton';

	import { onMount } from 'svelte';
    let userInput = '';
    let result = null;
    let error = null;
    let loading = false;

    async function fetchSOAPData() {
        loading = true;
        result = null;
        error = null;

        try {
            const response = await fetch('/api/posts', {
                method: 'POST',
                headers: {
                    'Content-Type': 'application/json'
                },
                body: JSON.stringify({
                    cpf: userInput
                })
            });

            if (response.ok) {
                result = await response.json();
            } else {
                error = await response.json();
            }
        } catch (err) {
            error = { message: 'Network Error' };
        } finally {
            loading = false;
        }
    }

    function handleSubmit(event) {
        event.preventDefault();
        fetchSOAPData();
    }
</script>

<!-- App Shell -->
<AppShell>
	<svelte:fragment slot="header">
		<!-- App Bar -->
		<AppBar>
			<svelte:fragment slot="lead">
				<strong class="text-xl uppercase">Skeleton</strong>
			</svelte:fragment>
			<svelte:fragment slot="trail">
				<a
					class="btn btn-sm variant-ghost-surface"
					href="https://discord.gg/EXqV7W8MtY"
					target="_blank"
					rel="noreferrer"
				>
					Discord
				</a>
				<a
					class="btn btn-sm variant-ghost-surface"
					href="https://twitter.com/SkeletonUI"
					target="_blank"
					rel="noreferrer"
				>
					Twitter
				</a>
				<a
					class="btn btn-sm variant-ghost-surface"
					href="https://github.com/skeletonlabs/skeleton"
					target="_blank"
					rel="noreferrer"
				>
					GitHub
				</a>
			</svelte:fragment>
		</AppBar>
	</svelte:fragment>

	<form on:submit={handleSubmit}>
		<label class="m-auto label max-w-2xl flex">
			<input class="input bg-surface-700" title="Input (text)" type="text" placeholder="Digite seu CPF ou CNPJ" id="paramInput" bind:value={userInput} required />
			<button class="btn variant-filled-tertiary" type="submit">Enviar</button>
		</label>
	</form>

	{#if loading}
			<p>Carregando...</p>
	{:else if error}
			<p>Erro ao carregar os dados: {error.message}</p>
	{:else if result}
		<div class="max-w-2xl m-auto">
			<h1>Resultados da Requisição SOAP</h1>
			<p>{JSON.stringify(result)}</p>
		</div>
	{/if}
	<!-- Page Route Content -->
	<slot />
</AppShell>
