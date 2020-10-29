<template>
	<div class="content">
		<Header />
		<Popup />
		<ContentList :list="partTimeList" />
	</div>
</template>

<script lang="ts">
import { defineComponent, reactive } from 'vue'
import Header from './Header.vue'
import Popup from './Popup.vue'
import ContentList from './ContentList.vue'

export interface PartTimeInfo {
	jobs: string
	salary: string
	isSelfEmployed: boolean
	isDayKnot: boolean
	isFreeFood: boolean
	company: string
	area: string
}

const PartTime = defineComponent({
	components: {
		Header,
		Popup,
		ContentList
	},
	setup() {
		const partTimeList = reactive<PartTimeInfo[]>(
			Array(5).fill({
				jobs: '酒店服务员',
				salary: '10元/小时',
				isDayKnot: true,
				isFreeFood: true,
				isSelfEmployed: true,
				company: '重庆公司公司公司公司',
				area: '江北区'
			})
		)
		return {
			partTimeList
		}
	}
})

export default PartTime
</script>

<style scoped lang="scss">
@import '@/common.scss';

.content {
	@extend %vh100;
	display: flex;
	flex-direction: column;
	.contentList {
		flex: 1;
	}
}
</style>
