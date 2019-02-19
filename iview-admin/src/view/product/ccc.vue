<template>
	<div style="margin:0 auto;">
		<Table :loading="loading" border :columns="columns7" :data="lastdata"></Table>
		<br>
		<div align="center">
		<template>
			<Page :total="total" :current="current" :page-size="pageNum" :page-size-opts="arrPageSize"
			  @on-change="changePage" show-total />
		</template>
		</div>
	</div>
</template>
<script>
	export default {
		data() {
			return {
				loading: false,
				current: 1,
				total: 9,
				pageNum: 8,
				arrPageSize: [5],
				lastdata: [
					{
						id: 5,
						name: 'John Brown',
						price: 18,
						number: 'New York No. 1 Lake Park'
					}, {
						id: 848,
						name: 'iPhoneX 全网通 64G',
						price: 5299.00,
						number: 8
					},
					{
						id: 788,
						name: 'iPhone7 Plus 全网通 128G',
						price: 4199.00,
						number: 3
					},
					{
						id: 898,
						name: 'iPhone7 Plus 全网通 32G',
						price: 3699.00,
						number: 13
					},
					{
						id: 879,
						name: 'iPhone8 全网通 256G',
						price: 4699.00,
						number: 9
					},
					{
						id: 388,
						name: 'iPhone7 Plus 全网通 32G',
						price: 3699.00,
						number: 13
					},
					{
						id: 688,
						name: 'iPhone7 Plus 全网通 32G',
						price: 3699.00,
						number: 13
					},
					{
						id: 188,
						name: 'iPhone7 全网通 32G',
						price: 2799.00,
						number: 8
					}
				],
				columns7: [
					{
						title: '编号',
						key: 'id',
						width: 100,
						fixed: 'left',
						render: (h, params) => {
							return h('div', [
								h('Icon', {
									props: {
										type: 'person'
									}
								}),
								h('strong', params.row.id)
							]);
						}
					},
					{
						title: '商品名称',
						key: 'name'
					},
					{
						title: '产品最低售价',
						key: 'price'
					},
					{
						title: '库存',
						key: 'number'
					},
					{
						title: 'Action',
						key: 'action',
						width: 150,
						align: 'center',
						render: (h, params) => {
							return h('div', [
								h('Button', {
									props: {
										type: 'primary',
										size: 'small'
									},
									style: {
										marginRight: '5px'
									},
									on: {
										click: () => {
											this.show(params.index)
										}
									}
								}, 'View'),
								h('Button', {
									props: {
										type: 'error',
										size: 'small'
									},
									on: {
										click: () => {
											this.remove(params.index)
										}
									}
								}, 'Delete')
							]);
						}
					}
				],
				data6: [
					{
						id: 5,
						name: 'John Brown',
						price: 18,
						number: 'New York No. 1 Lake Park'
					}, {
						id: 848,
						name: 'iPhoneX 全网通 64G',
						price: 5299.00,
						number: 8
					},
					{
						id: 788,
						name: 'iPhone7 Plus 全网通 128G',
						price: 4199.00,
						number: 3
					},
					{
						id: 898,
						name: 'iPhone7 Plus 全网通 32G',
						price: 3699.00,
						number: 13
					},
					{
						id: 879,
						name: 'iPhone8 全网通 256G',
						price: 4699.00,
						number: 9
					},
					{
						id: 388,
						name: 'iPhone7 Plus 全网通 32G',
						price: 3699.00,
						number: 13
					},
					{
						id: 688,
						name: 'iPhone7 Plus 全网通 32G',
						price: 3699.00,
						number: 13
					},
					{
						id: 188,
						name: 'iPhone7 全网通 32G',
						price: 2799.00,
						number: 8
					},
					{
						id: 88,
						name: 'iPhone8 Plus 全网通 64G',
						price: 4699.00,
						number: 1
					}
				]
			}
		},
		methods: {
			changePage(value) {
				console.log(this.data6.length);
				 this.current = value;
				var _start = ( value - 1 ) * this.pageNum;
				var _end = value * this.pageNum;
				this.lastdata = this.data6 .slice(_start,_end);
			},
			show(index) {
				this.$Modal.info({
					title: '产品详情',
					content: `编号：${this.data6[index].id}<br>名称：${this.data6[index].name}<br>price：${this.data6[index].price}<br>库存：${this.data6[index].number}`
				})
			},
			propage() {
				this.loading = true;
			},
			remove(index) {
				this.data6.splice(index, 1);
			}
		}
	}
</script>
<style>
	.pro-page{
		position: fixed;
		height: 500px;
	}
</style>