<template>
	<div class="container mx-auto">

		<div class="h-96 bg-gray-800">
			<p class="text-center text-white py-12"></p>
		</div>
		
		<h1 class="text-center text-4xl my-12 uppercase">Guest Speaker: {{ page.properties.Name.title[0].plain_text }}</h1>
		<div class="block">
			<div class="border-b border-gray-200">
				<nav class="-mb-px flex space-x-8" aria-label="Tabs">
					<a v-for="(tab, index) in tabs" :key="tab.name" @click='selectTab(index)' :href="tab.href" :class="[tab.current ? 'border-indigo-500 text-indigo-600' : 'border-transparent text-gray-500 hover:text-gray-700 hover:border-gray-300', 'whitespace-nowrap py-4 px-1 border-b-2 font-medium text-sm']" :aria-current="tab.current ? 'page' : undefined">{{ tab.name }}
					</a>
				</nav>
			</div>
		</div>
		<div class="my-4" v-if="tabs[0].current">
			<template v-for="item in content"  class="leading-relaxed">
				
				<p :key="item.id" v-if="item.type == 'paragraph' && item.paragraph.text.length == 1"
				:class="{ 'font-bold': item.paragraph.text[0].annotations.bold }"
				class="leading-relaxed">

					{{ item.paragraph.text[0].plain_text }}
				</p>

				<br v-else-if="item.type == 'paragraph' && item.paragraph.text.length == 0" :key="item.id" />
					

				<li :key="item.id" v-if="item.type == 'bulleted_list_item'"
				class="pl-4 leading-relaxed">
					{{ item.bulleted_list_item.text[0].plain_text }}
				</li>

			</template>	
		</div>
		
		<div class="my-4" v-if="tabs[1].current">
			Lorem, ipsum dolor sit amet consectetur, adipisicing elit. Facilis totam nobis fugiat delectus officiis harum illo, consequuntur et, qui laboriosam molestias voluptates odit iure soluta exercitationem corporis ipsam repellat consectetur?

			Lorem ipsum dolor sit amet consectetur adipisicing elit. Ullam fugiat aut debitis, autem vero temporibus minus delectus voluptas veritatis? Ea possimus voluptates totam culpa perspiciatis? Laudantium beatae culpa provident nulla!
		</div>
	</div>
</template>

<script>
	export default {

		data(){
			return {
				tabs: [
					  { name: 'Notes', href: '#', current: true },
					  { name: 'Resources', href: '#', current: false },
					]
			}
		},

		methods: {
			selectTab (i) {
				this.tabs.forEach((tab, index) => {
				tab.current = (index === i)
				})
			}
		},

		async asyncData({ $axios, params }) {
			
			let content = {}
			let page = {}

			const filterData = { 
				filter: { "and":  [ 
						{ property: "Slug", text: { equals: params.slug } }, 
						{ property: "Status", select: { equals: "Published" } }
					]
				}

			}
			
			page = await $axios.$post('databases/815035805b6d4a53ab7a74c81ee7fa0b/query', filterData)

			content = await $axios.$get(`blocks/${page.results[0].id}/children`)
		
			return { page: page.results[0], content: content.results }
		}
	}
</script>
