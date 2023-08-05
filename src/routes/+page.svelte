<script lang="ts">
	import { onMount } from 'svelte';
	interface ReleaseDateComponents {
		year: number;
		month: number;
		day: number;
	}

	interface Artist {
		_type: string;
		api_path: string;
		header_image_url: string;
		id: number;
		image_url: string;
		index_character: string;
		is_meme_verified: boolean;
		is_verified: boolean;
		name: string;
		slug: string;
		url: string;
	}

	interface Album {
		_type: string;
		api_path: string;
		cover_art_thumbnail_url: string;
		cover_art_url: string;
		full_title: string;
		id: number;
		name: string;
		name_with_artist: string;
		release_date_components: ReleaseDateComponents;
		release_date_for_display: string;
		url: string;
		artist: Artist;
	}

	let album: Album;

	onMount(async () => {
		const url = 'https://genius-song-lyrics1.p.rapidapi.com/song/details/?id=3333153';
		const options = {
			method: 'GET',
			headers: {
				'X-RapidAPI-Key': '45d0e06a12msh287e4e7cd76739cp112175jsn5d674de1d8e4',
				'X-RapidAPI-Host': 'genius-song-lyrics1.p.rapidapi.com'
			}
		};

		try {
			const response = await fetch(url, options);
			const result = await response.json();

			album = result.song.album;
			console.log({ album });
		} catch (error) {
			console.log(error);
		}
	});
</script>

{#if album}
	<section class="grid grid-cols-[5fr,10fr] gap-8 overflow-hidden h-[454px]">
		<div class="aspect-video bg-white/60 rounded-lg p-4 pb-8 backdrop-blur-lg space-y-8">
			<div class="grid grid-cols-[5fr,3fr]">
				<div class="aspect-square">
					<img
						src={album.cover_art_url}
						alt="Cover"
						class="object-cover h-full w-full rounded-lg shadow-2xl"
					/>
				</div>
				<div class="-ml-16 relative -z-10">
					<img
						src="https://i.imgur.com/JVR5sY2.png"
						alt="Disc"
						class="object-contain h-full w-full"
					/>
				</div>
			</div>
			<!--  -->
			<div class="space-y-2">
				<h3 class="text-2xl text-center font-semibold">{album.name}</h3>
				<h4 class="text-center">{album.artist.name}</h4>
			</div>
			<!--  -->
			<input type="range" class="w-full" />

			<div class="flex gap-4 justify-evenly">
				<button class="active:scale-95">
					<svg
						xmlns="http://www.w3.org/2000/svg"
						viewBox="0 0 24 24"
						fill="currentColor"
						class="w-10 aspect-square rotate-180"
					>
						<path
							d="M15 6.75a.75.75 0 00-.75.75V18a.75.75 0 00.75.75h.75a.75.75 0 00.75-.75V7.5a.75.75 0 00-.75-.75H15zM20.25 6.75a.75.75 0 00-.75.75V18c0 .414.336.75.75.75H21a.75.75 0 00.75-.75V7.5a.75.75 0 00-.75-.75h-.75zM5.055 7.06C3.805 6.347 2.25 7.25 2.25 8.69v8.122c0 1.44 1.555 2.343 2.805 1.628l7.108-4.061c1.26-.72 1.26-2.536 0-3.256L5.055 7.061z"
						/>
					</svg>
				</button>
				<!--  -->
				<button class="active:scale-95">
					<svg
						xmlns="http://www.w3.org/2000/svg"
						viewBox="0 0 24 24"
						fill="currentColor"
						class="w-16 aspect-square"
					>
						<path
							fill-rule="evenodd"
							d="M2.25 12c0-5.385 4.365-9.75 9.75-9.75s9.75 4.365 9.75 9.75-4.365 9.75-9.75 9.75S2.25 17.385 2.25 12zm14.024-.983a1.125 1.125 0 010 1.966l-5.603 3.113A1.125 1.125 0 019 15.113V8.887c0-.857.921-1.4 1.671-.983l5.603 3.113z"
							clip-rule="evenodd"
						/>
					</svg>
				</button>
				<!--  -->
				<button class="active:scale-95">
					<svg
						xmlns="http://www.w3.org/2000/svg"
						viewBox="0 0 24 24"
						fill="currentColor"
						class="w-10 aspect-square"
					>
						<path
							d="M15 6.75a.75.75 0 00-.75.75V18a.75.75 0 00.75.75h.75a.75.75 0 00.75-.75V7.5a.75.75 0 00-.75-.75H15zM20.25 6.75a.75.75 0 00-.75.75V18c0 .414.336.75.75.75H21a.75.75 0 00.75-.75V7.5a.75.75 0 00-.75-.75h-.75zM5.055 7.06C3.805 6.347 2.25 7.25 2.25 8.69v8.122c0 1.44 1.555 2.343 2.805 1.628l7.108-4.061c1.26-.72 1.26-2.536 0-3.256L5.055 7.061z"
						/>
					</svg>
				</button>
			</div>
		</div>
		<div class="text-white w-full space-y-8">
			<h1 class="text-3xl font-bold">Explore</h1>

			<ul class="flex w-full gap-16">
				<li class="text-lg font-medium">Lyrics</li>
				<li class="text-lg font-medium">Other Albums</li>
				<li class="text-lg font-medium">Related Artist</li>
			</ul>

			<div class="relative">
				<div class="overflow-y-auto h-80 scrollbar-hide">
					Lorem ipsum dolor sit, amet consectetur adipisicing elit. Consequatur cumque doloribus,
					laborum repellendus itaque nam tenetur quam unde aperiam possimus ipsa alias perferendis
					assumenda accusantium cum accusamus voluptates earum necessitatibus. Distinctio tempore
					dolorem ad doloribus odit illum cumque! Itaque nostrum cumque deserunt obcaecati vel
					architecto harum quidem esse illo, dolorem, magnam ut deleniti, recusandae aperiam ab.
					Consectetur repudiandae alias ab. Voluptate libero repudiandae quod porro necessitatibus,
					eius corporis dolores hic, ad tempore animi quam sed architecto assumenda aspernatur
					laboriosam doloremque reiciendis pariatur blanditiis eum in at! Totam similique autem
					aliquam. Excepturi impedit omnis qui nobis suscipit officia neque libero. Ea laboriosam
					dignissimos consequatur deleniti cumque libero impedit a magni? Praesentium quam quis
					possimus laudantium iste ea expedita voluptatem harum assumenda! Impedit, adipisci
					nesciunt? Ab laborum autem modi explicabo nemo maiores fugiat unde eaque optio ullam
					voluptate natus quibusdam blanditiis ex culpa dolores deleniti, neque veritatis deserunt
					ducimus eligendi aliquid quod. Nihil dolores velit explicabo exercitationem eveniet, ipsum
					molestias ipsam, corrupti praesentium in alias autem veritatis libero? Est fugiat, a
					veritatis odio temporibus minus commodi, vel debitis dolorem totam deleniti sequi. Harum
					eligendi ea error molestias minus! Autem accusamus quasi doloribus excepturi perferendis
					maiores provident! In ad architecto accusamus iste ipsa eaque sunt consequuntur tempora
					nam eius, recusandae earum ipsum voluptatum! Consequuntur quod consectetur laborum,
					tempora perferendis nemo aliquam, neque enim delectus velit ex incidunt? Temporibus
					assumenda commodi culpa voluptatum dolorem magni esse, quae at, dolores, aspernatur odio
					aperiam expedita deleniti. Minus veritatis expedita quisquam libero non suscipit commodi
					eos aperiam possimus, deleniti maiores nulla nobis dolor aspernatur soluta cum pariatur
					rem numquam est quod blanditiis accusantium consequatur id. Obcaecati, delectus. Fuga
					laborum iure nobis rerum at delectus facere, aut quasi, nam reprehenderit sunt non quidem
					hic assumenda necessitatibus, odio sequi dignissimos distinctio. Nemo at ipsam quis
					adipisci? Laudantium, similique ullam?
				</div>
			</div>
		</div>
	</section>
{/if}
