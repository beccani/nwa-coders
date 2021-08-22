<template>
	<div class="container mx-auto grid grid-cols-2 py-4 px-4 md:px-0">
		<a href="/" class="p-4 sm:p-0"><span class="font-bold">NWA C</span>oders</a>
		<div class="cursor-pointer md:hidden justify-self-end hover:bg-black hover:text-white p-4" @click="toggle = !toggle">Menu</div>
		<div :class="{ 'hidden': toggle }" 
		class="col-span-2 md:col-span-1 justify-items-center md:justify-self-end md:block space-x-8">
			<a v-for="item in nav" :key="item.name" :href="item.path"> {{ item.name }}</a>
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