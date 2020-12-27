<template>
	<!-- template下只能有一个根节点-->
	<div>
    <pre>
      * v-text 是元素的innerText只能在双标签使用
      * v-html 是innerHTML，不能包含{{}}
      * v-if   元素是否移除或插入
      * v-show 元素是否显示或隐藏
      * v-model 双向数据绑定，v-bind是单向数据绑定（内存js改变影响页面）
	    <hr/>
    </pre>
		v-text =
		<span v-text="text"></span>
		<hr/>
		<input type="text" name="" v-text="text"/>
		<hr/>
		v-html =
		<span v-html="html"></span>
		<hr/>
		v-if =
		<div v-if="isShow" style="height: 6rem; background-color: red;"></div>
		<hr/>
		v-show =
		<div v-show="isShow" style="height: 6rem; background-color:blue;"></div>
		<hr/>
		v-model =
		<input type="text" name="" v-model="mText"/><br/>
		{{mText}}<br/>
		<!-- 给下面的input的value赋值用v-bind：value = 'mTest'-->
		v-bind =
		<input type="text" name="" v-bind:value="mText"/><br/>
		<hr/>
		<div v-bind:class="isRed ? 'red' : 'cyan'">单个class</div>
		<hr/>
		<div :class="{'red': true, 'size': true}">多个class</div>
		<hr/>
		<ul>
			<li v-for="student in students" :class="{'A' :'red', 'B' : 'cyan'}[student.score]">
				{{student.name}}
			</li>
		</ul>
		<hr/>
		<button @click="change">点我大变化</button>
		<hr/>
		<ul>
			<li v-for="(student, index) in students" v-bind:key="index">
			    student = {{student}}-->index:{{index}}
			</li>
		</ul>
		<ul>
			<li v-for="(value, key, index) in person" v-bind:key="index">
				value-->{{value}}
				key-->{{key}}
				index-->{{index}}
			</li>
		</ul>
		
		
		<!--<div id="login" v-on:mousedown.left="createLoves($event)" v-on:mouseup="removeSmallHert">
			<background ref="background"></background>
		</div>-->
	</div>
</template>

<script>
    // import background from './views/background.vue'

    export default {
        // components: {background},
        data() {
            return {
                text: "我是t-text玩的东西",
                // language=HTML
                html: `
					<ul>
						<li>哈哈手动蝶阀</li>
						<li>老师发的可感受到</li>
					</ul>
				`,
                isShow: false,
                mText: "拉十多个",
                isRed: true,
                students: [{name: 'jack', score: 'A'}, {name: 'rose', score: 'B'}],
	            person: {name: 'mack', alias: '麦克'}
            }
        },
        // 声明函数，属于组件对象的
        methods: {
            /*createLoves() {
                this.$refs.background.createLoves(event)
            },
            removeSmallHert() {
                this.$refs.background.removeSmallHert()
            },*/
            // 包含多个函数名做key，函数体做value
            change() {
                // 在script中能使用的对象，基本template中也能使用，但是，
                // 在script中要加this，  template一般不加this
                this.isRed = !this.isRed;
                this.students.push({
                    name: '张三', score: 'B',
                })
            }
        }
    }
</script>

<style>
	.red {
		background-color: red;
	}
	
	.cyan {
		background-color: cyan;
	}
	
	.size {
		font-size: 5rem;
	}
	
	#login {
		position: absolute;
		top: 0;
		left: 0;
		width: 100%;
		height: 100%;
	}
</style>