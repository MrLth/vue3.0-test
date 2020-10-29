<!--
 * @Author: mrlthf11
 * @LastEditors: mrlthf11
 * @Date: 2020-10-29 19:55:58
 * @LastEditTime: 2020-10-29 21:52:38
 * @Description: file content
-->
<template>
	<div class="content">
		<Header :status="popupStatus" :changeStatus="changeStatus" />
		<Popup
			v-if="popupStatus !== 0"
			:status="popupStatus"
			:partTimeCategroy="partTimeCategroy"
			:changeCurrent="changeCurrent"
			:jobsCategroy="jobsCategroy"
		/>
		<ContentList :list="partTimeList" />
	</div>
</template>

<script lang="ts">
import { defineComponent, reactive, ref } from 'vue'
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

export interface PartTimeCategroy {
	current: number
	list: string[]
}

export interface JobsClassification {
	title: string
	list: string[]
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
		const popupStatus = ref(0)
		const partTimeCategroy = reactive<PartTimeCategroy>({
			current: 0,
			list: ['全部兼职', '优质兼职', '附件兼职', '周末兼职', '最新兼职']
		})
		const jobsCategroy = reactive<JobsClassification[]>([
			{
				title: '简单易做',
				list: [
					'问卷调查',
					'地摊拉访',
					'促销导购',
					'服务员',
					'送餐员',
					'打包分拣',
					'安保',
					'充场',
					'展会协助',
					'临时工',
					'其他'
				]
			},
			{
				title: '宅家兼职',
				list: ['优惠卷分享', '产品代理', '上推广', 'APP试玩', '其他线上任务']
			},
			{
				title: '才艺技能',
				list: [
					'问卷调查',
					'地摊拉访',
					'促销导购',
					'服务员',
					'送餐员',
					'打包分拣',
					'安保',
					'充场',
					'展会协助',
					'临时工',
					'其他'
				]
			}
		])

		return {
			partTimeList,
			popupStatus,
			changeStatus(status: number) {
				console.log('status changed')
				popupStatus.value = status === popupStatus.value ? 0 : status
			},
			partTimeCategroy,
			changeCurrent(index: number) {
				console.log('changeCurrent', index)

				partTimeCategroy.current = index
			},
			jobsCategroy
		}
	}
})

export default PartTime
</script>

<style lang="scss" scoped>
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
