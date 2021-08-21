<template>
	<div class="grid grid-cols-2 py-4 px-2">
		<a href="/"><span class="font-bold">NWA C</span>oders</a>
		<div class="cursor-pointer md:hidden justify-self-end" @click="toggle = !toggle">Menu</div>
		<div :class="{ 'hidden': toggle }" 
		class="col-span-2 md:col-span-1 justify-items-center md:justify-self-end md:block ">
			<a v-for="item in nav" :key="item.name" :href="item.path" class="mr-8"> {{ item.name }}</a>
		</div>
	</div>
</template>

<script>
	export default {
		data(){
			return{
				nav: [
					{ name: "Sponsor", path: "/sponsor" },
					{ name: "Events", path: "/events" },
					{ name: "Contact", path: "/contact" },
					{ name: "About", path: "/about" },
				],
				toggle: true
			}
		},
	}
</script>