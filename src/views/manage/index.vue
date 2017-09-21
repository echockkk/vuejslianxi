<template>
	<div class="manage tc">
		<button v-on:click="add">新增</button>
		<div class="input-area" v-show="showAdd">
			<input type="text" placeholder="请输入名称" v-model="nameValue"/>
			<button v-on:click="addName">确定</button>
		</div>
		<table>
			<tr>
				<th>姓名</th>
				<th>操作</th>
			</tr>
			<tr v-for="(item,index) in peoples">
				<td>{{item.name}}</td>
				<td v-bind:id="index"><span v-on:click="edit">编辑</span><span v-on:click="del">删除</span></td>
			</tr>
		</table>
		<div class="wrap" v-show="showEdit">
			<div class="content">
				<input type="text" placeholder="请输入名字" v-model="newValue">
				<button v-on:click="editName">确定</button>
				<button v-on:click="cancel">取消</button>
			</div>
		</div>
		<footer-nav v-bind:class="{'isManage':isNowPage}"></footer-nav>
	</div>
</template>
<script>
	import FooterNav from '../../components/footer.vue'
	export default {
		components: {
			FooterNav
		},
		data(){
			return {
				isNowPage: true,
				peoples:[
					{'name':'Jack'},
					{'name':'Joe'}
				],
				nameValue: '',
				showAdd: false,
				showEdit: false,
				newValue: '',
				editId: 0
			}
		},
		methods: {
			add(){
				this.showAdd = true
			},
			addName(){
				var v = this.nameValue
				if(v.trim() == ""){
					alert('请输入姓名');
				}else{
					var data = {};
					data.name = v;
					this.peoples.push(data);
				}
			},
			del(e){
				var id = e.target.offsetParent.id;
				this.peoples.splice(id,1)
			},
			edit(e){
				var id = e.target.offsetParent.id
				this.showEdit = true
				this.editId = id
				this.newValue = this.peoples[id].name
			},
			cancel(){
				this.showEdit = false
			},
			editName(){
				var v = this.newValue
				if(v.trim() == ''){
					alert('请输入名字');
				}else{
					this.peoples[this.editId].name = this.newValue;
					this.showEdit = false;
				}
			}
		}
	}
</script>
<style type="text/css">
	button {
		width: 60%;
		height: 40px;
		background: #41b883;
		line-height: 40px;
		font-size: 14px;
		text-align: center;
		color: #fff;
		border: 1px solid #41b883;
		border-radius: 10px;
	}
	.input-area {
		margin-top: 10px;
	}
	.input-area input {
		width: 50%;
		height: 40px;
		border: 1px solid #666;
		border-radius: 5px;
		vertical-align: middle;
	}
	.input-area button {
		width: 80px;
		height: 42px;
		line-height: 42px;
		text-align: center;
		vertical-align: middle;
	}
	table {
		margin-top: 20px;
		width: 100%;
	}
	table tr {
		width: 100%;
		display: flex;
	}
	table tr td,table tr th {
		width: 50%;
		height: 30px;
		line-height: 30px;
		text-align: center;
		font-size: 14px;
	}
	.wrap {
		width: 100%;
		height: 100%;
		background: rgba(0,0,0,0.5);
		position: absolute;
		top: 0;
		left: 0;
	}
	.wrap .content input {
		display: block;
		width: 60%;
		height: 40px;
		line-height: 40px;
		border: 1px solid #666;
		margin: 0 auto;
		margin-top: 200px;
		margin-bottom: 20px;
	}
	.wrap .content button {
		width: 80px;
		height: 40px;
	}
</style>