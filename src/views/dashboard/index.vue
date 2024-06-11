<template>
	<div class="dashboard-container">
		<qus-editor :qusList="list"></qus-editor>
		{{list[9]}}
		<button @click="addList">Add</button>
	</div>
</template>

<script>
	import {
		mapGetters
	} from 'vuex'
	import QusEditor from '@/components/QusEditor'

	export default {
		name: 'Dashboard',
		components: {
			QusEditor
		},
		computed: {
			...mapGetters([
				'name'
			])
		},
		data() {
			return {
        list2:[{
					id: '1',
					title: `<p><strong>单项选择</strong></p>`,
					type: 'radio',
					setting: [
						{key:'11',label:'男',value:'男',defaultChecked:false},
						{key:'12',label:'女',value:'女',defaultChecked:false},
						{key:'13',label:'保密',value:'保密',defaultChecked:true}
					],
					answer: []
				}],
				list: [{
					id: '1',
					title: `<p><strong>单项选择</strong></p>`,
					type: 'radio',
					setting: [
						{key:'11',label:'男',value:'男',defaultChecked:false},
						{key:'12',label:'女',value:'女',defaultChecked:false},
						{key:'13',label:'保密',value:'保密',defaultChecked:true}
					],
					answer: []
				}, {
					id: '2',
					title: `<p><strong>多项选择</strong></p>`,
					type: 'checkbox',
					setting: [
						{key:'21',label:'男',value:'男',defaultChecked:false},
						{key:'22',label:'女',value:'女',defaultChecked:false},
						{key:'23',label:'保密',value:'保密',defaultChecked:true}
					],
					answer: []
				}, {
					id: '3',
					title: `<p><strong>下拉框选择</strong></p>`,
					type: 'selector',
					setting: [
						{key:'31',label:'男',value:'男',defaultChecked:false},
						{key:'32',label:'女',value:'女',defaultChecked:false},
						{key:'33',label:'保密',value:'保密',defaultChecked:true}
					],
					answer: []
				}, {
					id: '4',
					title: `<p><strong>量表题</strong></p>`,
					type: 'rate',
					setting: [
						{key:'41',label:'极差',value:'极差',num:'1',notScored:false},
						{key:'42',label:'失望',value:'失望',num:'2',notScored:false},
						{key:'43',label:'一般',value:'一般',num:'3',notScored:false},
            {key:'44',label:'满意',value:'满意',num:'4',notScored:false},
            {key:'45',label:'惊喜',value:'惊喜',num:'5',notScored:false}
					],
					answer: []
				}, {
					id: '5',
					title: `<p><strong>评分单选</strong></p>`,
					type: 'singleRate',
					setting: [
						{key:'51',label:'极差',value:'极差',num:'1',notScored:false},
						{key:'52',label:'失望',value:'失望',num:'2',notScored:false},
						{key:'53',label:'一般',value:'一般',num:'3',notScored:false},
            {key:'54',label:'满意',value:'满意',num:'4',notScored:false},
            {key:'55',label:'惊喜',value:'惊喜',num:'5',notScored:false}
					],
					answer: []
				}, {
					id: '6',
					title: `<p><strong>评分多选</strong></p>`,
					type: 'multipleRate',
					setting: [
						{key:'61',label:'极差',value:'极差',num:'1',notScored:false},
						{key:'62',label:'失望',value:'失望',num:'2',notScored:false},
						{key:'63',label:'一般',value:'一般',num:'3',notScored:false},
            {key:'64',label:'满意',value:'满意',num:'4',notScored:false},
            {key:'65',label:'惊喜',value:'惊喜',num:'5',notScored:false}
					],
					answer: []
				}, {
					id: '7',
					title: `<p><strong>矩阵量表</strong></p>`,
					type: 'matrixRate',
					Xsetting: [
						{key:'x71',label:'极差',value:'极差',num:'1',notScored:false},
						{key:'x72',label:'失望',value:'失望',num:'2',notScored:false},
						{key:'x73',label:'一般',value:'一般',num:'3',notScored:false},
            {key:'x74',label:'满意',value:'满意',num:'4',notScored:false},
            {key:'x75',label:'惊喜',value:'惊喜',num:'5',notScored:false}
					],
          Ysetting: [
          	{key:'y71',label:'内容1',value:'内容1',num:'',notScored:false},
          	{key:'y72',label:'内容2',value:'内容2',num:'',notScored:false},
          	{key:'y73',label:'内容3',value:'内容3',num:'',notScored:false},
            {key:'y74',label:'内容4',value:'内容4',num:'',notScored:false},
            {key:'y75',label:'内容5',value:'内容5',num:'',notScored:false}
          ],
					answer: []
				}, {
					id: '8',
					title: `<p><strong>NPS量表</strong></p>`,
					type: 'npsRate',
					setting: [
						{key:'81',label:'极差',value:'极差',num:'1',notScored:false},
						{key:'82',label:'极差',value:'极差',num:'2',notScored:false},
						{key:'83',label:'失望',value:'失望',num:'3',notScored:false},
            {key:'84',label:'失望',value:'失望',num:'4',notScored:false},
            {key:'85',label:'一般',value:'一般',num:'5',notScored:false},
            {key:'86',label:'一般',value:'一般',num:'6',notScored:false},
            {key:'87',label:'满意',value:'满意',num:'7',notScored:false},
            {key:'88',label:'满意',value:'满意',num:'8',notScored:false},
            {key:'89',label:'惊喜',value:'惊喜',num:'9',notScored:false},
            {key:'810',label:'惊喜',value:'惊喜',num:'10',notScored:false}
					],
					answer: []
				}, {
					id: '9',
					title: `<p><strong>单项填空</strong></p>`,
					type: 'singleInput',
					setting: [
            {key:'91',label:'单项填空',value:'单项填空',num:'1',notScored:false},
            ],
					answer: []
				}, {
					id: '10',
					title: `<p><strong>多项填空</strong></p>`,
					type: 'multipleInput',
					setting: [
            {key:'101',label:'多项填空1',value:'多项填空1',num:'',notScored:false},
            {key:'102',label:'多项填空2',value:'多项填空2',num:'',notScored:false},
            ],
					answer: []
				}]
			}
		},
		methods: {
			addList() {
				this.list.push({
					id: new Date().getTime() + '',
					title: '标题' + new Date().getTime(),
					type: 'select-xed'
				})
			}
		}
	}
</script>

<style lang="scss" scoped>
	.dashboard {
		&-container {
			margin: 30px;
		}

		&-text {
			font-size: 30px;
			line-height: 46px;
		}
	}
</style>
