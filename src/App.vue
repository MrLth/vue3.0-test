<template>
	<router-view />
</template>

<script lang="ts">
import { defineComponent, onMounted, onBeforeUnmount } from 'vue'

const PartTime = defineComponent({
	setup(props) {
		//# region 修复100vh在移动端显示效果不符预期的BUG
		const windowResizeCb = () => {
			const vh = window.innerHeight * 0.01
			document.documentElement.style.setProperty('--vh', `${vh}px`)
		}
		onMounted(() => {
			windowResizeCb()
			window.addEventListener('resize', windowResizeCb)

			console.log('onMounted called')
		})
		onBeforeUnmount(() => {
			console.log('onMounted return called')
			window.removeEventListener('resize', windowResizeCb)
		})
		// # endregion
	}
})

export default PartTime
</script>


<style lang="scss">



</style>
