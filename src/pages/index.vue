<template>

	<br>
	<div id="introduce" style="margin: 50px;margin-top: 100px;">
		<h1 class="text" style="line-height: 90px;">
			{{ saying1 }}
		</h1>
		<br><br><br>
		<h2 class="text2">
			{{saying2}}
		</h2>
	</div>
	<br><br><br>


	<el-drawer
	size="50%"
    v-model="drawer"
    title="关于软件"
  >
	<h1>对角工具巷(原工具栈)</h1><br>
	<a class="thanks" href="https://toolstack.rth5.com/">https://toolstack.rth5.com/  (复制打开)</a>
	<p>这是一个用 Vue + Element UI 构建的时间工具，以简洁的设计为您高效工作提供帮助</p><br><br>
	<h2>功能</h2><br>
	<p>翻页时钟√</p>
	<p>表盘时钟√</p>
	<p>番茄时钟√</p>
	<p>正计时器√</p>
	<p>倒计时器√</p>
	<p>智能助手√</p>
	<p>TTS朗读√</p>
	<p>天气查询√</p>
	<p>二维码制作√</p>
	<p>IP查询√</p>
	<p>成语查询√</p>
	<p>MBTI√</p>
	<p>拖拽分屏时钟√</p>
	<p>懒加载√</p>
	<p>时钟精度到达毫秒⚪</p>
	<p>增加抽签工具板块⚪</p>
	<p>增加网页工具板块⚪</p>	
	<br><br>
	<h2>开发</h2><br>
	<p>本项目仍然处于开发阶段，我们期待您给我们一些建议与支持！</p><br><br>
    <h2>作者</h2>
	<p><br>
		卡尔斯厄<br>
		个人网站：<a class="thanks" href="https://kaersie.github.io">kaersie.github.io</a><br>
		B站：<a class="thanks" href="https://space.bilibili.com/1026296481">bilibili@卡尔斯厄</a><br>
		Github：<a class="thanks" href="https://github.com/kaersie">Kaersie</a><br>
	</p><br><br>
	<h2>致谢</h2><br>
		<p>以下是本项目使用到的第三方库和框架：</p>
		<br><a class="thanks" href="https://cn.vuejs.org/">Vue.js</a>
		<br><a class="thanks" href="https://element-plus.org/">Element Plus</a>
		<br><a class="thanks" href="https://vitejs.cn/">Vite.js</a>
		<br><a class="thanks" href="https://router.vuejs.org/">Vue Router</a>
		<br><a class="thanks" href="https://github.com/rongang/vue-drag-split">VueDragSplit</a>
		<br><a class="thanks" href="https://github.com/Yuezi32/flipClock">flipClock</a>
		<br><a class="thanks" href="https://blog.csdn.net/qq_39708228/article/details/114921340">Vue3Cookie</a>
		<br><a class="thanks" href="https://github.com/bestvist/vue-clock2/">Vue-Clock2</a>
		<br><a class="thanks" href="https://github.com/sindresorhus/screenfull">ScreenFull</a>
		<br><a class="thanks" href="https://github.com/unplugin/unplugin-vue-components">unplugin-vue-components</a>
		<br><a class="thanks" href="https://github.com/unplugin/unplugin-auto-import">unplugin-auto-import</a>
		<br><a class="thanks" href="https://api.vore.top/">OoyonghongoO</a><br><br>
		<br><a class="thanks" href="https://platform.moonshot.cn/">MoonShot</a><br><br>
		<br><a class="thanks" href="https://api.ipify.org">Ipify</a><br><br>

		<h3>本软件基于 GPL-3.0 开源协议</h3>
  </el-drawer>

	<el-row :gutter="21" style="margin-left: 10px;margin-right: 10px;">
		<el-col v-for="(item, index) in items" :xs="20" :sm="10" :md="8" :lg="7" :xl="5" @click="jump(item.link)"
			style="margin: auto;margin-bottom: 40px;display: block;">
			<el-card style="max-width: 480px" shadow="hover" :key="index">
				<template #header>
					<div class="card-header">
						<div v-html="item.icon" style="margin-bottom:15px"></div>
						<p style="text-align: center;">{{ item.name }}</p>
					</div>
				</template>
				<p style="text-align: center;" v-html="item.other"></p>
			</el-card>
		</el-col>
		
	</el-row>
	<div>
  <h3 style="text-align: center;">网站浏览次数</h3><br>
  <div style="text-align: center; width:100%;height:100%; display: table;">
   <span style="display: table-cell; vertical-align: middle; ">
    <img style="margin:0 auto" src="https://api.vore.top/api/ACGcount?code=toolstack">
   </span>
</div>
 </div>
</template>
<style>
.card {
	margin: auto;
	display: block;
	text-align: center;
}

.thanks{
	color:#409EFF
}
* {
	margin: 0;
	padding: 0;
	box-sizing: border-box;
}

.text {
	display: inline-block;
	position: relative;
	height: 20px;
	line-height: 20px;
	color: rgb(245, 245, 245);
	margin-bottom: 10px;
}

.text2 {
	height: 40px;
	line-height: 45px;
	color: rgb(245, 245, 245);
}

.text::after {
	content: '';
	position: absolute;
	height: 70px;
	width: 3px;
	background-color: #fff;
	animation: san 0.5s steps(1) infinite;
}

@keyframes san {

	0%,
	100% {
		background-color: #fff;
	}

	50% {
		background-color: transparent;
	}

}
</style>
<script setup>
import { useRouter } from 'vue-router'
import { reactive,ref } from 'vue'
const drawer = ref(false)
const router = useRouter()
function jump(link) {
	if(link=="about"){
		drawer.value=true
	} else if(link=="down"){
		location.href="https://grasp.lanzout.com/b00659rdjg"
	}
	else{
	router.push(link)
	}
}
const saying1=ref("Hello,World!")
const saying2=ref("")

fetch(`https://api.vore.top/api/hitokoto?type=json`).then((res) => res.json()).then((data) => {
	const{data:{text,from}}=data;
	saying1.value=text;

	saying2.value="来源于 "+from
})

const items = reactive([
	{
		name: 'AI 优化助手', icon: `<svg xmlns="http://www.w3.org/2000/svg" width="100" height="100" fill="currentColor"  class="el-icon card k" viewBox="0 0 16 16">
			<path d="M4.968 9.75a.5.5 0 1 0-.866.5A4.498 4.498 0 0 0 8 12.5a4.5 4.5 0 0 0 3.898-2.25.5.5 0 1 0-.866-.5A3.498 3.498 0 0 1 8 11.5a3.498 3.498 0 0 1-3.032-1.75zM7 5.116V5a1 1 0 0 0-1-1H3.28a1 1 0 0 0-.97 1.243l.311 1.242A2 2 0 0 0 4.561 8H5a2 2 0 0 0 1.994-1.839A2.99 2.99 0 0 1 8 6c.393 0 .74.064 1.006.161A2 2 0 0 0 11 8h.438a2 2 0 0 0 1.94-1.515l.311-1.242A1 1 0 0 0 12.72 4H10a1 1 0 0 0-1 1v.116A4.22 4.22 0 0 0 8 5c-.35 0-.69.04-1 .116z"/>
  <path d="M16 8A8 8 0 1 1 0 8a8 8 0 0 1 16 0zm-1 0A7 7 0 1 0 1 8a7 7 0 0 0 14 0z"/>
				</svg>`,
		other: '用 AI 优化每一件事情<br>支持各类问题<br>适用于“没思路”或“不了解”等情况', link: '/ai'
	},
	{
		name: '分屏时钟', icon: `<svg xmlns="http://www.w3.org/2000/svg" width="100" height="100" fill="currentColor"  class="el-icon card k" viewBox="0 0 16 16">
			<path d="M8.235 1.559a.5.5 0 0 0-.47 0l-7.5 4a.5.5 0 0 0 0 .882L3.188 8 .264 9.559a.5.5 0 0 0 0 .882l7.5 4a.5.5 0 0 0 .47 0l7.5-4a.5.5 0 0 0 0-.882L12.813 8l2.922-1.559a.5.5 0 0 0 0-.882l-7.5-4zm3.515 7.008L14.438 10 8 13.433 1.562 10 4.25 8.567l3.515 1.874a.5.5 0 0 0 .47 0l3.515-1.874zM8 9.433 1.562 6 8 2.567 14.438 6 8 9.433z"/>
	</svg>`,
		other: '实现同一页面多开时间工具<br>支持所有工具<br>适用于辩论、比赛等场景', link: '/splitclock'
	},
	{
		name: 'MBTI测试', icon: `<svg xmlns="http://www.w3.org/2000/svg" width="100" height="100" fill="currentColor"  class="el-icon card k" viewBox="0 0 16 16">
			<path d="M8 8a3 3 0 1 0 0-6 3 3 0 0 0 0 6zm2-3a2 2 0 1 1-4 0 2 2 0 0 1 4 0zm4 8c0 1-1 1-1 1H3s-1 0-1-1 1-4 6-4 6 3 6 4zm-1-.004c-.001-.246-.154-.986-.832-1.664C11.516 10.68 10.289 10 8 10c-2.29 0-3.516.68-4.168 1.332-.678.678-.83 1.418-.832 1.664h10z"/>	</svg>`,
		other: '快速的MBTI测试工具<br>简易版，主打效率<br>适用于想要免费快速了解自己的人群', link: '/mbtitest'
	},
	{
		name: '数字时钟', icon: `<svg xmlns="http://www.w3.org/2000/svg" width="100" height="100" fill="currentColor"  class="el-icon card k" viewBox="0 0 16 16">
			<path d="M0 3.5A1.5 1.5 0 0 1 1.5 2h13A1.5 1.5 0 0 1 16 3.5v9a1.5 1.5 0 0 1-1.5 1.5h-13A1.5 1.5 0 0 1 0 12.5v-9zM1.5 3a.5.5 0 0 0-.5.5v9a.5.5 0 0 0 .5.5h13a.5.5 0 0 0 .5-.5v-9a.5.5 0 0 0-.5-.5h-13z"/>
  <path d="M2 4.5a.5.5 0 0 1 .5-.5h3a.5.5 0 0 1 0 1H3v2.5a.5.5 0 0 1-1 0v-3zm12 7a.5.5 0 0 1-.5.5h-3a.5.5 0 0 1 0-1H13V8.5a.5.5 0 0 1 1 0v3z"/></svg>`,
		other: '极简的翻页数字时间<br>支持背景色、全屏等参数设置<br>适用于考试或自习等场景', link: '/numberclock'
	},
	{
		name: '模拟时钟', icon: `<svg xmlns="http://www.w3.org/2000/svg" width="100" height="100" fill="currentColor"  class="el-icon card k" viewBox="0 0 16 16">
			<path d="M8 3.5a.5.5 0 0 0-1 0V9a.5.5 0 0 0 .252.434l3.5 2a.5.5 0 0 0 .496-.868L8 8.71V3.5z"/>
  <path d="M8 16A8 8 0 1 0 8 0a8 8 0 0 0 0 16zm7-8A7 7 0 1 1 1 8a7 7 0 0 1 14 0z"/></svg>`,
		other: '类似于真实时钟的在线时间<br>支持背景色、全屏、等参数设置<br>适用于自习、工作、会议等场景', link: '/muticlock'
	},
	{
		name: '番茄时钟', icon: `<svg xmlns="http://www.w3.org/2000/svg" width="100" height="100" fill="currentColor"  class="el-icon card k" viewBox="0 0 16 16">
			<path d="M8.5 5.5a.5.5 0 0 0-1 0v3.362l-1.429 2.38a.5.5 0 1 0 .858.515l1.5-2.5A.5.5 0 0 0 8.5 9V5.5z"/>
  <path d="M6.5 0a.5.5 0 0 0 0 1H7v1.07a7.001 7.001 0 0 0-3.273 12.474l-.602.602a.5.5 0 0 0 .707.708l.746-.746A6.97 6.97 0 0 0 8 16a6.97 6.97 0 0 0 3.422-.892l.746.746a.5.5 0 0 0 .707-.708l-.601-.602A7.001 7.001 0 0 0 9 2.07V1h.5a.5.5 0 0 0 0-1h-3zm1.038 3.018a6.093 6.093 0 0 1 .924 0 6 6 0 1 1-.924 0zM0 3.5c0 .753.333 1.429.86 1.887A8.035 8.035 0 0 1 4.387 1.86 2.5 2.5 0 0 0 0 3.5zM13.5 1c-.753 0-1.429.333-1.887.86a8.035 8.035 0 0 1 3.527 3.527A2.5 2.5 0 0 0 13.5 1z"/></svg>`,
		other: '以番茄工作法为基础的计时器<br>支持背景、任务等参数设置<br>让自己于专注工作与学习', link: '/tomatoclock'
	},
	{
		name: '正计时器', icon: `<svg xmlns="http://www.w3.org/2000/svg" width="100" height="100" fill="currentColor"  class="el-icon card k" viewBox="0 0 16 16">
			<path d="M9 5a.5.5 0 0 0-1 0v3H6a.5.5 0 0 0 0 1h2.5a.5.5 0 0 0 .5-.5V5z"/>
  <path d="M4 1.667v.383A2.5 2.5 0 0 0 2 4.5v7a2.5 2.5 0 0 0 2 2.45v.383C4 15.253 4.746 16 5.667 16h4.666c.92 0 1.667-.746 1.667-1.667v-.383a2.5 2.5 0 0 0 2-2.45V8h.5a.5.5 0 0 0 .5-.5v-2a.5.5 0 0 0-.5-.5H14v-.5a2.5 2.5 0 0 0-2-2.45v-.383C12 .747 11.254 0 10.333 0H5.667C4.747 0 4 .746 4 1.667zM4.5 3h7A1.5 1.5 0 0 1 13 4.5v7a1.5 1.5 0 0 1-1.5 1.5h-7A1.5 1.5 0 0 1 3 11.5v-7A1.5 1.5 0 0 1 4.5 3z"/>	</svg>`,
		other: '秒表计时工具<br>支持暂停、计次等功能<br>适用于考试、自习、比赛等场景', link: '/floatclock'
	},
	{
		name: '倒计时器', icon: `<svg xmlns="http://www.w3.org/2000/svg" width="100" height="100" fill="currentColor"  class="el-icon card k" viewBox="0 0 16 16">
			<path d="M8.5 5.6a.5.5 0 1 0-1 0v2.9h-3a.5.5 0 0 0 0 1H8a.5.5 0 0 0 .5-.5V5.6z"/>
  <path d="M6.5 1A.5.5 0 0 1 7 .5h2a.5.5 0 0 1 0 1v.57c1.36.196 2.594.78 3.584 1.64a.715.715 0 0 1 .012-.013l.354-.354-.354-.353a.5.5 0 0 1 .707-.708l1.414 1.415a.5.5 0 1 1-.707.707l-.353-.354-.354.354a.512.512 0 0 1-.013.012A7 7 0 1 1 7 2.071V1.5a.5.5 0 0 1-.5-.5zM8 3a6 6 0 1 0 .001 12A6 6 0 0 0 8 3z"/>
			</svg>`,
		other: '倒计时工具<br>支持播放提示音、暂停、重置、刷新等操作<br>适用于考试、自习、比赛等场景', link: '/unfloatclock'
	},
	{
		name: 'TTS 文本朗读', icon: `<svg xmlns="http://www.w3.org/2000/svg" width="100" height="100" fill="currentColor"  class="el-icon card k" viewBox="0 0 16 16">
			<path d="M13 2.5a1.5 1.5 0 0 1 3 0v11a1.5 1.5 0 0 1-3 0v-.214c-2.162-1.241-4.49-1.843-6.912-2.083l.405 2.712A1 1 0 0 1 5.51 15.1h-.548a1 1 0 0 1-.916-.599l-1.85-3.49a68.14 68.14 0 0 0-.202-.003A2.014 2.014 0 0 1 0 9V7a2.02 2.02 0 0 1 1.992-2.013 74.663 74.663 0 0 0 2.483-.075c3.043-.154 6.148-.849 8.525-2.199V2.5zm1 0v11a.5.5 0 0 0 1 0v-11a.5.5 0 0 0-1 0zm-1 1.35c-2.344 1.205-5.209 1.842-8 2.033v4.233c.18.01.359.022.537.036 2.568.189 5.093.744 7.463 1.993V3.85zm-9 6.215v-4.13a95.09 95.09 0 0 1-1.992.052A1.02 1.02 0 0 0 1 7v2c0 .55.448 1.002 1.006 1.009A60.49 60.49 0 0 1 4 10.065zm-.657.975 1.609 3.037.01.024h.548l-.002-.014-.443-2.966a68.019 68.019 0 0 0-1.722-.082z"/>			</svg>`,
		other: '快速文本转语音<br>基于 TTS 技术<br>适用于全平台', link: '/tts'
	},
	{
		name: 'IP 查询', icon: `<svg xmlns="http://www.w3.org/2000/svg" width="100" height="100" fill="currentColor"  class="el-icon card k" viewBox="0 0 16 16">
			<path d="M8 0a8 8 0 1 0 0 16A8 8 0 0 0 8 0ZM2.04 4.326c.325 1.329 2.532 2.54 3.717 3.19.48.263.793.434.743.484-.08.08-.162.158-.242.234-.416.396-.787.749-.758 1.266.035.634.618.824 1.214 1.017.577.188 1.168.38 1.286.983.082.417-.075.988-.22 1.52-.215.782-.406 1.48.22 1.48 1.5-.5 3.798-3.186 4-5 .138-1.243-2-2-3.5-2.5-.478-.16-.755.081-.99.284-.172.15-.322.279-.51.216-.445-.148-2.5-2-1.5-2.5.78-.39.952-.171 1.227.182.078.099.163.208.273.318.609.304.662-.132.723-.633.039-.322.081-.671.277-.867.434-.434 1.265-.791 2.028-1.12.712-.306 1.365-.587 1.579-.88A7 7 0 1 1 2.04 4.327Z"/>
  </svg>`,
		other: '获取本机公网IP<br>支持查看归属地、邮编、运营商<br>适用于全平台', link: '/ip'
	},
	{
		name: '二维码生成', icon: `<svg xmlns="http://www.w3.org/2000/svg" width="100" height="100" fill="currentColor"  class="el-icon card k" viewBox="0 0 16 16">
			<path d="M0 .5A.5.5 0 0 1 .5 0h3a.5.5 0 0 1 0 1H1v2.5a.5.5 0 0 1-1 0v-3Zm12 0a.5.5 0 0 1 .5-.5h3a.5.5 0 0 1 .5.5v3a.5.5 0 0 1-1 0V1h-2.5a.5.5 0 0 1-.5-.5ZM.5 12a.5.5 0 0 1 .5.5V15h2.5a.5.5 0 0 1 0 1h-3a.5.5 0 0 1-.5-.5v-3a.5.5 0 0 1 .5-.5Zm15 0a.5.5 0 0 1 .5.5v3a.5.5 0 0 1-.5.5h-3a.5.5 0 0 1 0-1H15v-2.5a.5.5 0 0 1 .5-.5ZM4 4h1v1H4V4Z"/>
  <path d="M7 2H2v5h5V2ZM3 3h3v3H3V3Zm2 8H4v1h1v-1Z"/>
  <path d="M7 9H2v5h5V9Zm-4 1h3v3H3v-3Zm8-6h1v1h-1V4Z"/>
  <path d="M9 2h5v5H9V2Zm1 1v3h3V3h-3ZM8 8v2h1v1H8v1h2v-2h1v2h1v-1h2v-1h-3V8H8Zm2 2H9V9h1v1Zm4 2h-1v1h-2v1h3v-2Zm-4 2v-1H8v1h2Z"/>
  <path d="M12 9h2V8h-2v1Z"/>
	</svg>`,
		other: '生成高清二维码<br>支持快速生成<br>适用于全平台', link: '/qrcode'
	},
	{
		name: '成语字典', icon: `<svg xmlns="http://www.w3.org/2000/svg" width="100" height="100" fill="currentColor"  class="el-icon card k" viewBox="0 0 16 16">
			<path d="M14 3a1 1 0 0 1 1 1v8a1 1 0 0 1-1 1H2a1 1 0 0 1-1-1V4a1 1 0 0 1 1-1h12zM2 2a2 2 0 0 0-2 2v8a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2V4a2 2 0 0 0-2-2H2z"/>
  <path d="M2 5.5a.5.5 0 0 1 .5-.5h2a.5.5 0 0 1 .5.5v1a.5.5 0 0 1-.5.5h-2a.5.5 0 0 1-.5-.5v-1zm0 3a.5.5 0 0 1 .5-.5h5a.5.5 0 0 1 0 1h-5a.5.5 0 0 1-.5-.5zm0 2a.5.5 0 0 1 .5-.5h1a.5.5 0 0 1 0 1h-1a.5.5 0 0 1-.5-.5zm3 0a.5.5 0 0 1 .5-.5h1a.5.5 0 0 1 0 1h-1a.5.5 0 0 1-.5-.5zm3 0a.5.5 0 0 1 .5-.5h1a.5.5 0 0 1 0 1h-1a.5.5 0 0 1-.5-.5zm3 0a.5.5 0 0 1 .5-.5h1a.5.5 0 0 1 0 1h-1a.5.5 0 0 1-.5-.5z"/>		</svg>`,		other: '在线快速查词<br>支持拼音、释义、例句、出处等<br>适用于全平台', link: '/text'
	},{
		name: '天气查询', icon: `<svg xmlns="http://www.w3.org/2000/svg" width="100" height="100" fill="currentColor"  class="el-icon card k" viewBox="0 0 16 16">
			<path d="M8.5 3a4.002 4.002 0 0 0-3.8 2.745.5.5 0 1 1-.949-.313 5.002 5.002 0 0 1 9.654.595A3 3 0 0 1 13 12H4.5a.5.5 0 0 1 0-1H13a2 2 0 0 0 .001-4h-.026a.5.5 0 0 1-.5-.445A4 4 0 0 0 8.5 3zM0 7.5A.5.5 0 0 1 .5 7h5a.5.5 0 0 1 0 1h-5a.5.5 0 0 1-.5-.5zm2 2a.5.5 0 0 1 .5-.5h9a.5.5 0 0 1 0 1h-9a.5.5 0 0 1-.5-.5zm-2 4a.5.5 0 0 1 .5-.5h9a.5.5 0 0 1 0 1h-9a.5.5 0 0 1-.5-.5z"/></svg>`,
			other: '在线快速查天气<br>根据IP属地获取天气<br>支持风力、风向、湿度等数据', link: '/weather'
	},
	
	{
		name: '关于网站', icon: `<svg xmlns="http://www.w3.org/2000/svg" width="100" height="100" fill="currentColor"  class="el-icon card k" viewBox="0 0 16 16">
			<path d="M6 1H1v14h5V1zm9 0h-5v5h5V1zm0 9v5h-5v-5h5zM0 1a1 1 0 0 1 1-1h5a1 1 0 0 1 1 1v14a1 1 0 0 1-1 1H1a1 1 0 0 1-1-1V1zm9 0a1 1 0 0 1 1-1h5a1 1 0 0 1 1 1v5a1 1 0 0 1-1 1h-5a1 1 0 0 1-1-1V1zm1 8a1 1 0 0 0-1 1v5a1 1 0 0 0 1 1h5a1 1 0 0 0 1-1v-5a1 1 0 0 0-1-1h-5z"/></svg>`,
			other: '版本: 0.2.1 Build<br>作者: 卡尔斯厄 ( bilibili@卡尔斯厄 )<br>点此查看更多', link: 'about'
	},{
		name: '客户端下载', icon: `<svg xmlns="http://www.w3.org/2000/svg" width="100" height="100" fill="currentColor"  class="el-icon card k" viewBox="0 0 16 16">
			<path d="M4.406 1.342A5.53 5.53 0 0 1 8 0c2.69 0 4.923 2 5.166 4.579C14.758 4.804 16 6.137 16 7.773 16 9.569 14.502 11 12.687 11H10a.5.5 0 0 1 0-1h2.688C13.979 10 15 8.988 15 7.773c0-1.216-1.02-2.228-2.313-2.228h-.5v-.5C12.188 2.825 10.328 1 8 1a4.53 4.53 0 0 0-2.941 1.1c-.757.652-1.153 1.438-1.153 2.055v.448l-.445.049C2.064 4.805 1 5.952 1 7.318 1 8.785 2.23 10 3.781 10H6a.5.5 0 0 1 0 1H3.781C1.708 11 0 9.366 0 7.318c0-1.763 1.266-3.223 2.942-3.593.143-.863.698-1.723 1.464-2.383z"/>
  <path d="M7.646 15.854a.5.5 0 0 0 .708 0l3-3a.5.5 0 0 0-.708-.708L8.5 14.293V5.5a.5.5 0 0 0-1 0v8.793l-2.146-2.147a.5.5 0 0 0-.708.708l3 3z"/></svg>`,
		other: '版本: 0.2.1 Build<br>支持安卓、Windows 平台<br>其他平台可使用vue编译单文件直接运行', link: 'down'
	}
])
console.log(items)

</script>
<style>
.k{
	height: 40px;
	width: 40px;
}
</style>