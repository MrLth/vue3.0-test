<!--
 * @Author: mrlthf11
 * @LastEditors: mrlthf11
 * @Date: 2020-10-29 19:55:58
 * @LastEditTime: 2020-10-29 21:29:32
 * @Description: file content
-->
<template>
	<div class="contentList">
		<li v-for="(v, i) in list" :key="i">
			<div class="row1">
				<div>{{ v.jobs }}</div>
				<div>{{ v.salary }}</div>
			</div>
			<div class="row2">
				<div v-if="v.isSelfEmployed" class="selfEmployed">自营</div>
				<div v-if="v.isDayKnot" class="dayKnot">日结</div>
				<div v-if="v.isFreeFood" class="freeFood">包吃</div>
			</div>
			<div class="row3">
				<div>{{ v.company }}</div>
				<div>{{ v.area }}</div>
			</div>
		</li>
	</div>
</template>

<script lang="ts">
import { defineComponent, PropType } from 'vue'
import { PartTimeInfo } from './index.vue'
import { setup } from 'vue-class-component'

const ContentList = defineComponent({
	props: {
		list: Array as PropType<PartTimeInfo[]>
	},
	setup(props) {
		// console.log(props.list.map(v=>console.log(v)))
	}
})

export default ContentList
</script>

<style scoped lang="scss">
@import '@/common.scss';

.contentList {
	background-color: #f4f4f6;
	padding: rem(16) rem(16) 0;
	overflow: auto;
	li {
		display: block;
		width: 100%;
		padding: rem(12);
		margin-bottom: rem(16);
		background-color: #fff;
		border-radius: rem(8);

		.row1 {
			display: flex;
			font-size: rem(18);
			font-weight: bold;
			margin-bottom: rem(6);
			justify-content: space-between;
			div:last-child {
				color: #ff6d48;
			}
		}

		.row2 {
			display: flex;
			margin-bottom: rem(6);

			div {
				font-size: rem(12);
				border-radius: rem(3);
				vertical-align: middle;
				padding: rem(1) rem(5);
				margin-right: rem(4);
			}
			.selfEmployed {
				color: #fff;
				background: linear-gradient(to right, #f3c68c, #ea8f46);
			}
			.dayKnot,
			.freeFood {
				color: #ea8f46;
				background-color: #fff6f1;
			}
		}

		.row3 {
			display: flex;
			justify-content: space-between;
			div {
				font-size: rem(12);
				color: #9d9d9d;
			}
		}
	}
}
</style>
