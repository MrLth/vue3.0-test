<template>
	<div class="header">
		<div class="navigater">
			<div class="position icon-arrowDown">重庆市</div>
			<div class="title">全部兼职</div>
		</div>
		<div class="action">
			<div>全部地区 </div>
			<div>全部兼职 </div>
			<div>全部岗位 </div>
		</div>
	</div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'

const Header = defineComponent({})

export default Header
</script>

<style scoped lang="scss">
@import '@/common.scss';

.navigater {
	position: relative;
	height: rem(64);
	line-height: rem(64);
	.position {
		position: absolute;
		padding-left: rem(16);
		color: #9d9d9d;
		font-size: rem(13);
		&:after {
			@include iconfont('\e61a', rem(14));
		}
	}
	.title {
		font-size: rem(18);
		font-weight: bold;
		text-align: center;
	}
}

.action {
    display: flex;
    height: rem(48);
    line-height: rem(48);
    color: #9C9C9C;
	& > div {
        text-align: center;
        flex: 1;
        font-size: rem(14);
        &:after {
			@include iconfont('\e62f', rem(15));
		}
	}
}
</style>
