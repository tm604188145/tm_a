<template>
	<div>
		<h3>App组件</h3>
		<p>{{msg.name}}</p>
		<Child :message="msg"/>
	</div>
</template>

<script>
	import Child from './components/Child';
	export default {
		name:"App",
		components:{Child},
		data(){
			return {
				msg:{name:"赵四"}
			}
		}
	}
</script>

<style lang="scss" scoped>

</style>