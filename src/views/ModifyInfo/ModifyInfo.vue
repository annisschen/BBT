<template>
	<el-container>

		<el-header class="sub-header">
			<div>
				<h2>修改信息</h2>
			</div>
		</el-header>
		<el-main class="sub-main">
			<div class = 'inputElements'>
				<h4>修改部门 ： </h4><el-row class="demo-autocomplete">
				<el-col :span="12">
					<el-autocomplete
							class="inline-input"
							v-model="state1"
							:fetch-suggestions="querySearch"
							placeholder="请输入内容"
							@select="handleSelect"
					></el-autocomplete>
				</el-col>
			</el-row>
			</div >

			<div class = 'inputElements'>
				<h4>修改姓名 ： </h4>
				<el-input class="inputBox"
						  placeholder="请输入内容"
						  v-model="input1"
						  clearable>
				</el-input>
			</div>

			<div class = 'inputElements'>
				<h4>修改年级 ： </h4><div class="inputBox">
				<el-input
						placeholder="原姓名"
						v-model="input2"
						clearable>
				</el-input>
			</div>
			</div>

			<div class = 'inputElements'>
				<h4>修改性别 ： </h4>
				<div class="inputBox">
				<el-radio v-model="radio" label="1">男</el-radio>
				<el-radio v-model="radio" label="2">女</el-radio>
				</div>
			</div>
			<div class = 'inputElements'>
				<h4>修改寝室 ： </h4>
				<el-input class="inputBox"
						  placeholder="原寝室楼-号"
						  v-model="input3"
						  clearable>
				</el-input>
			</div>
			<div class = 'inputElements'>
				<h4>修改QQ号 ： </h4>
				<el-input class="inputBox"
						  placeholder="原QQ号"
						  v-model="input4"
						  clearable>
				</el-input>
			</div>
			<div class = 'inputElements'>
				<h4>修改职位 ： </h4>
				<el-input class="inputBox"
						  placeholder="原职位"
						  v-model="input5"
						  clearable>
				</el-input>
			</div>
			<el-row>
				<el-button type="warning" round id="submit-button" disabled="">提交</el-button>
				<el-button type="warning" round id="submit-button">提交</el-button>
			</el-row>
		</el-main>

	</el-container>
</template>

<script>
export default {
	name: "ModifyInfo",
	data() {
            return {
                restaurants: [],
                state1: '',
                input1: '',
                input2: '',
                input3: '',
                radio: '2',
				input4:'',
				input5:''
            };
        },
        methods: {
            querySearch(queryString, cb) {
                var restaurants = this.restaurants;
                var results = queryString ? restaurants.filter(this.createFilter(queryString)) : restaurants;
                // 调用 callback 返回建议列表的数据
                cb(results);
            },
            createFilter(queryString) {
                return (restaurant) => {
                    return (restaurant.value.toLowerCase().indexOf(queryString.toLowerCase()) === 0);
                };
            },
            loadAll() {
                return [
                    { "value": "秘书部" },
                    { "value": "文艺部" },
                    { "value": "宣传部" },
                    { "value": "体育部" },
                    { "value": "新媒体中心" },
                    { "value": "志愿者" },
                    { "value": "调研部" },
                    { "value": "生活部" },
                    { "value": "素拓部" },
                    { "value": "学术部" },
                    { "value": "组织部" }
                ];
            },
            handleSelect(item) {
                console.log(item);
            }
        },
        mounted() {
            this.restaurants = this.loadAll();
        }
}
</script>

<style scoped lang="scss">
	.sub-header{
		border: coral;
		border-bottom-style: solid;
		margin: 0 auto;
	}
	.sub-main{
		margin: 0 auto;
	}
	.inputBox{
		float: left;
		height: 50px;
		width: 400px;
	}
	.inputElements{
		float: bottom;
		line-height:50px;
	}

	.inputElements h4{
		float: left;
		height: 50px;
		width: 100px;
		display:inline-block
	}
	#submit-button{
		float: right;
	}
</style>