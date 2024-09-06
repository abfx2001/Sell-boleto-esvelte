<!-- YOU CAN DELETE EVERYTHING IN THIS PAGE -->

<div class="container h-full mx-auto flex justify-center items-center">
	<div class="space-y-10 text-center flex flex-col items-center">
		<h2 class="h2">Boas Vindas ao meu Site de Testes</h2>
		<!-- Animated Logo -->
		<figure>
			<section class="img-bg" />
			<img class="rounded-full" src="https://avatars.githubusercontent.com/u/71567139?s=400&u=44de47f44e9831dd0acf1d42b360835fe7649742&v=4" alt="teste">
		</figure>
		<!-- / -->
		<div class="flex justify-center space-x-2">
			<a
				class="btn variant-filled-tertiary"
				href="https://github.com/abfx2001"
				target="_blank"
				rel="noreferrer"
			>
				Conheça Meu Perfil
			</a>
		</div>
	</div>
</div>




<style lang="postcss">
	figure {
		@apply flex relative flex-col;
	}
	figure svg,
	.img-bg {
		@apply w-64 h-64 md:w-80 md:h-80;
	}
	.img-bg {
		@apply absolute z-[-1] rounded-full blur-[50px] transition-all;
		animation: pulse 5s cubic-bezier(0, 0, 0, 0.5) infinite,
			glow 5s linear infinite;
	}
	@keyframes glow {
		0% {
			@apply bg-primary-400/50;
		}
		33% {
			@apply bg-secondary-400/50;
		}
		66% {
			@apply bg-tertiary-400/50;
		}
		100% {
			@apply bg-primary-400/50;
		}
	}
	@keyframes pulse {
		50% {
			transform: scale(1.5);
		}
	}
</style>
