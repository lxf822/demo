<template>
    <div class="index-message">
   		<div class="index-message__title clearfix">
   			<div class="block--float-left">消息</div>
   			<div 
   				class="block--float-right"
   				@click="goNext('/message/query')"
   			></div>
   		</div>
	    <dx-ul>
		  	<li 
		  		v-for="(message, index) in messages"
		  		:key="index"
		  		class="index-message-teacher clearfix"
		  	>
				<div class="index-message-teacher--icon block--float-left"></div>
				<div class="index-message-teacher__detail">
					<div>
						<span class="index-message-teacher__detail--name">
							{{message.title}}
						</span>
						<span v-if="!message.system">
							<span class="index-message-teacher__detail--male"></span>
							<span class="index-message-teacher__detail--role"></span>
						</span>
						<span class="block--float-right">{{message.time}}</span>
					</div>
					<div class="index-message-teacher__detail--desc">
						<router-link :to="message.path">{{message.content}}</router-link>
					</div>
				</div>
			</li>
		</dx-ul> 
		<dx-footer :selectTab="2"></dx-footer>
		<transition 
			name="router"  
			mode='out-in'
		>
			<router-view class="full-screen"/>
		</transition>
    </div>
   
</template>
<script>
	import DxFooter from '../common/FooterPage.vue'
	import mixin from 'utils/mixin.js'
	export default {
		mixins: [mixin],
		components: {
			DxFooter
		},
		data() {
			return {
				messages: [
					{
						title: '系统消息',
						time: '3天前',
						content: '请对课程进行评价',
						path: '/message/system',
						system: true
					},
					{
						title: '杨帆',
						time: '5分钟',
						content: '英语协会副会长，多次获得国际英语口语竞赛金奖英语协会副会长，多次获得国际英语口语竞赛金奖',
						path: '/message/chat'
					},
					{
						title: '张逸勇',
						time: '5分钟',
						content: '英语协会副会长，多次获得国际英语口语竞赛金奖英语协会副会长，多次获得国际英语口语竞赛金奖',
						path: '/message/chat'
					}
				]
			}
		}
	}
</script>
<style  lang="scss">
	@include b(index-message) {
		padding-top: 0.32rem;
		@include e(title) {
			font-size: 0.48rem;
			line-height: 0.88rem;
			>div:nth-child(2) {
				width: 0.88rem;
				height: 0.88rem;
				background: $--message-search-background;
			}
		}
		/* 明星老师介绍 */
		@include b(index-message-teacher) {
			width: 100%;
			margin-top: 0.48rem;
			margin-bottom: 0.42rem;
			@include m(icon) {
				width: 1.09rem;
				height: 1.09rem;
				margin-right: 0.28rem;
				border-radius: 50%;
				background-color: #444;
			}
			@include e(detail) {
				overflow: hidden;
				vertical-align: middle;
				font-size: 0.34rem;
				color: #7E7E7E;
				word-wrap: break-word;
				@include m(name) {
					color: #333;
				}
				@include m(male) {
					display: inline-block;
					margin-left: 0.1rem;
					width: 0.28rem;
					height: 0.28rem;
					background: $--index-home-teacher-male-background;
				}
				@include m(role) {
					display: inline-block;
					margin-left: 0.1rem;
					width: 0.66rem;
					height: 0.32rem;
					background: $--index-home-teacher-role-background;
				}
				@include m(desc) {
				width: 100%;
					margin-top: 0.2rem; 
				}
			}
		}
	}	
</style>