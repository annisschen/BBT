<template>
	<el-container>

		<el-header class="sub-header">
			<div>
				<h2>海报申请表</h2>
			</div>
		</el-header>

		<el-main class="sub-main">
			<div class = 'inputElements'>
				<h4>申请部门 ： </h4><el-row>
				<el-col :span="12">
					<el-autocomplete
							class="inputBox"
							v-model="state1"
							:fetch-suggestions="querySearch1"
							placeholder="请选择部门"
							@select="handleSelect"
					></el-autocomplete>
				</el-col>
			</el-row>
			</div >

			<div class = 'inputElements'>
				<h4>申请人 ： </h4><el-input class="inputBox"
						  placeholder="请输入内容"
						  v-model="input1"
						  clearable>
				</el-input>
			</div>

			<div class = 'inputElements'>
				<h4>活动时间 ： </h4>
				<el-date-picker class="inputBox"
						v-model="value1"
						type="datetime"
						placeholder="选择日期时间">
				</el-date-picker>
			</div>

			<div class = 'inputElements'>
				<h4>活动地点 ： </h4><el-input class="inputBox"
										  placeholder="请输入内容，若无地点则输入无"
										  v-model="input2"
										  clearable>
			</el-input>
			</div>
			<div class = 'inputElements'>
				<h4>海报要求： </h4>
				<el-input class ="textarea"
						  type="textarea"
						  rows="2"
						  placeholder="A0/A2/横幅/A4邀请函（彩色/黑白）……"
						  v-model="textarea1"
						  resize="none">
				</el-input>
			</div>

			<div class="inputElements">
				<h4>文字要求： </h4>
				<el-input class ="textarea"
						  type="textarea"
						  rows="2"
						  placeholder="请输入文字要求"
						  v-model="textarea2"
						  resize="none">
				</el-input>
			</div>

			<div class = 'inputElements'>
				<h4>截止时间 ： </h4>
				<el-date-picker class="inputBox"
								v-model="value2"
								type="datetime"
								placeholder="选择日期时间">
				</el-date-picker>
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
        name:'PostApply',
        data() {
            return {
                restaurants: [],
                state1: '',
                input1: '',
                value1: '',
                input2: '',
                textarea1: '',
				textarea2: '',
				value2: ''
            };
        },
        methods: {
            querySearch1(queryString, cb) {
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
            loadAll1() {
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
            this.restaurants = this.loadAll1();
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
	.textarea{
		margin-top: 10px;
		height: 60px;
		width: 400px;
	}
	.inputBox{
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