<template>
		<div class="container mx-auto mt-12">
			<div class="row">
				<div class="col-sm-8 offset-sm-2 text-gray-700 text-center ">
					<div class="relative mb-8">
						<h1 class="relative text-6xl md:text-9xl text-shadow font-sans font-bold">
							<span v-for="letter in title" :key="letter">{{ letter }}</span><br><span v-for="letter in subTitle" :key="letter">{{ letter }}</span>
						</h1>
					</div>
					<p class="my-8 text-2xl">site coming soon</p>
					<a class="bg-gray-800 px-5 py-3 text-sm shadow-sm font-medium tracking-wider text-gray-50 rounded-full hover:shadow-lg" href="https://discord.com/channels/830116083594952735/854164136932671502/870696629274038283"> Join Discord Community </a>
					<MeetSchedule :data="data"/>
					
				</div>
			</div>
		</div>
</template>


<script>
	export default {

		data(){
			return {
				title: 'NWA',
				subTitle: 'CODERS'
			}
		},

		async asyncData({ $axios }) {
			
			let data = {}

			try{
				
				const filterData = { 
					filter: { property: "Status", select: { equals: "Published" } },
					sorts: [ { property: "Day", direction: "ascending" }]
				}
				
				data = await $axios.$post('databases/d9f93215943f4d6ea9e73ab3af2f569c/query', filterData)

			}catch(err){
				
			}

			return { data }
		}

	}
</script>


<style>
	.text-shadow {
		text-shadow: -8px 0 0 #e3e3e3;
	}
</style>