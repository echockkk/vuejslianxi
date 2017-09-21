<template>
	<div class="footer fixed">
		<ul>
			<li><router-link to="/">首页</router-link></li>
			<li><router-link to="/manage">人员管理</router-link></li>
		</ul>
	</div>
</template>
<script>

</script>
<style scoped>
	.footer {
		width: 100%;
		height: 50px;
		position: fixed;
		left: 0;
		bottom: 0;
	}
	ul {
		display: flex;
		height: 100%;
		line-height: 50px;
	}
	ul li {
		flex: 1;
		background: #f1f1f1;
	}
	li a {
		display: inline-block;
		width: 100%;
		height: 100%;
		text-align: center;
		line-height: 50px;
		color: #000;
		font-size: 14px;
	}
	.isIndex li:first-child,.isManage li:last-child {
		background: #d3d3d3;
	}
	.isIndex li:first-child a,.isManage li:last-child a {
		color: #41b883;
	}

</style>