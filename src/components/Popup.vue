<!--
 * @Author: mrlthf11
 * @LastEditors: mrlthf11
 * @Date: 2020-10-29 19:55:58
 * @LastEditTime: 2020-10-29 21:53:27
 * @Description: file content
-->
<template>
	<div class="popup">
		<div class="col1" v-if="status === 1"></div>
		<ul class="col2" v-if="status === 2">
			<li
				v-for="(v, i) in partTimeCategroy.list"
				:key="i"
				:class="partTimeCategroy.current === i ? 'selected' : ''"
				@click="changeCurrent(i)"
			>
				{{ v }}
			</li>
		</ul>
		<div class="col3" v-if="status === 3">
			<ul class="list" v-if="status === 3">
				<ul v-for="v in jobsCategroy" :key="v.title">
					<li class="title">{{ v.title }}</li>
					<li class="tile" v-for="vv in v.list" :key="vv">{{ vv }}</li>
				</ul>
			</ul>
			<div class="btn-group">
				<div>重置</div>
				<div>完成</div>
			</div>
		</div>
	</div>
	<div class="mask"></div>
</template>

<script lang="ts">
import { defineComponent, PropType } from 'vue'
import { JobsClassification, PartTimeCategroy } from './index.vue'

const Popup = defineComponent({
	props: {
		status: Number, // 2:全部兼职， 3：全部岗位,
		partTimeCategroy: Object as PropType<PartTimeCategroy>,
		changeCurrent: Function,
		jobsCategroy: Array as PropType<JobsClassification[]>
	}
})

export default Popup
</script>

<style lang="scss" scoped>
@import '@/common.scss';

.popup {
	z-index: 999;
	width: 100%;
	position: absolute;
	top: rem(112);
	background-color: #fff;

	.col2 {
		li {
			text-align: center;
			vertical-align: middle;
			line-height: rem(42);
			color: #9c9c9c;
			font-size: rem(14);
			border-bottom: 1px solid #f1f1f3;
		}

		.selected {
			color: #00bdfd;
		}
	}

	.col3 {
		.list {
			height: rem(300);
			overflow: auto;

			.title {
				font-size: rem(16);
				font-weight: bold;
				margin: rem(4) 0 rem(12) rem(14);
			}

			.tile {
				font-size: rem(14);
				color: #73797d;
				padding: 0 rem(14);
				height: rem(28);
				line-height: rem(28);
				border-radius: rem(14);
				background-color: #f4f5f7;
				display: inline-block;
				margin: 0 0 rem(10) rem(10);
			}
		}

		.btn-group {
			display: flex;
			height: rem(42);
			line-height: rem(42);
			font-size: rem(14);
			border-top: 1px solid #f1f1f3;

			div {
				color: #97989c;
				flex: 1;
				text-align: center;
				&:last-child {
					color: #fff;
					background: linear-gradient(to right, #82c9f5, #66a8f2);
				}
			}
		}
	}
}
.mask {
	position: absolute;
	top: rem(112);
	left: 0;
	right: 0;
	bottom: 0;
	background-color: rgba($color: #000000, $alpha: 0.05);
}
</style>
