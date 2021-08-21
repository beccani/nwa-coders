<template>
	<div class="container mx-auto">

		<h1 class="text-center text-4xl my-12 uppercase">Guest Speaker: {{ page.properties.Name.title[0].plain_text }}</h1>
		<div v-for="item in content" :key="item.id" class="leading-relaxed">
			
			<p v-if="item.type == 'paragraph' && item.paragraph.text.length == 1"
			class="leading-normal">
				{{ item.paragraph.text[0].plain_text }}
			</p>

			<p v-if="item.type == 'bulleted_list_item'"
			class="pl-4 leading-relaxed">
				* {{ item.bulleted_list_item.text[0].plain_text }}
			</p>

		</div>
	</div>
</template>

<script>
	export default {
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
