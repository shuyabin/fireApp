<script>
	import common from 'common/common.js';
	export default {
		onLaunch: function() {

			plus.screen.lockOrientation('portrait-primary'); //锁定

			//plus.storage.removeItem("pushmsg");

			setInterval(function() {

				common.getPush();

				var pushlist = common.pushlistapp;

				if (pushlist == null || pushlist == "") {
					return;
				}

				console.log(JSON.stringify(pushlist));

				plus.push.createMessage(pushlist.pushcontent);

				let user = uni.getStorageSync("USERS_KEY");
				user = JSON.parse(user);
				let uuid = plus.device.uuid;
				uni.request({
					url: common.hosturl + "push/insertlist.html",
					method: "POST",
					data: {
						uuid: uuid,
						pushid: pushlist.pushid,
						token:user.token
					},
					header: {
						'content-type': 'application/x-www-form-urlencoded'
					},
					success: function(res) {

						//console.log(JSON.stringify(res.data))
						if (res.data.code == 0) {



						} else {
							return;
						}
					},
					fail: function() {
						return;
					}
				})



			}, 5000);




		},
		onShow: function() {

			// 监听点击消息事件
			plus.push.addEventListener("click", function(msg) {
				/*
       根据需要填写
           */
				uni.navigateTo({
					url: "/pages/train/msglist"
				})


			}, false);



		},
		onHide: function() {
			console.log('App Hide')
		}
	}
</script>

<style>
	/* 按钮 */
	.btn {
		width: 490px;
		height: 88px;
		border-radius: 12px;
		line-height: 88px;
		text-align: center;
		font-size: 36px;
		margin: 0 auto;
		background-color: #d0021b;
		color: #ffffff;
	}

	.mbtn {
		border-radius: 12px;
		display: flex;
		justify-content: center;
		align-items: center;
		font-size: 28px;
		color: #FFFFFF;
		/* 需要参数：宽高，背景颜色大小 */
	}

	/* icon图标 */
	@font-face {
		font-family: iconfont;
		font-weight: normal;
		font-style: normal;
		src: url('https://at.alicdn.com/t/font_874003_zu85pbcigxa.ttf') format('truetype');
	}

	.icon {
		font-size: 50px;
		color: #fff;
		font-family: iconfont;
	}

	.gIcon {
		font-size: 52px;
		color: #6c6c6c;
		font-family: iconfont;
	}

	/*每个页面公共css */
	/* @import './common/common.css'; */

	page {
		font-size: 32px;
		background-color: #f7f7f7;
		display: flex;
		flex-direction: column;
		width: 100%;
		min-height: 100vh;
	}

	.mgr20 {
		margin-right: 20px;
	}

	.mgl20 {
		margin-left: 20px;
	}

	.mgr30 {
		margin-right: 30px;
	}

	.mgl30 {
		margin-left: 30px;
	}

	.mgt20 {
		margin-top: 20px;
	}

	.mgt40 {
		margin-top: 40px;
	}

	.btn-danger {
		background-color: #d0021b;
	}

	.btn-primary {
		background-color: #409eff;
	}

	.btn-info {
		background-color: #67ba61;
	}

	/*页面头部样式*/
	.header {
		height: 128px;
		width: 100%;
		display: flex;
		padding-top: 40px;
		box-sizing: border-box;
		padding-top: 40px;
		align-items: center;
		background-color: #d0021b;
		/* box-shadow: 0px 4px 8px 0px #e6e6e6; */
	}

	.header-left,
	.header-right {
		width: 88px;
		height: 88px;
		display: flex;
		align-items: center;
		justify-content: center;
	}

	.header-content {
		flex: 1;
		font-size: 36px;
		text-align: center;
		font-size: 36px;
		color: #ffffff;
	}
</style>
