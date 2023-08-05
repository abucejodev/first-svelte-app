<script>
	import '../globals.css';
</script>

<div>
	<img
		src="https://images.unsplash.com/photo-1501420264597-23296a7e6a46?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D&auto=format&fit=crop&w=1176&q=80"
		alt="Background"
		class="object-cover w-full h-full absolute inset-0 brightness-[0.5]"
	/>
	<div class="fixed inset-0 bg-black/40 backdrop-blur-sm" />
	<main class="relative h-screen z-10 grid items-center mx-auto max-w-4xl">
		<slot />
	</main>
</div>
