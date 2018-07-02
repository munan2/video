# video
关于video标签的学习
## video 常见属性  
1. controls 显示控件，例如播放暂停按钮  
2. width/height 设置宽高  
3. loop 设置播放关闭之后再次播放  
4. autoplay 设置自动播放，兼容性问题：在谷歌浏览器中，需要在src前加上muted,在可以使用。  
```
<video muted src="./video.mp4" autoplay="autoplay" ></video>
```  
5. poster 用户点击播放按钮前视频区域展示的图片
```
<video poster="http://img0.ph.126.net/I10JqUUJDmlEtE_XYl4hOg==/6608842237655242020.jpg" src="./video.mp4" ></video>
```  
6. duration 视频的长度
7. currentTime 当前播放时间(以秒计)  
8. volume 视频音量
## video 事件
当音频/视频处于加载过程中时，会依次发生以下事件：  
loadstart 加载开始时，浏览器开始搜索视频/音频  
durationchange 提示视频的时长已改变，当加载时，时长从NaN变为实际时长  
loadedmetadata 提示音频的元数据已加载，元数据有：时长、尺寸、文本轨道
loadeddata 当前帧的数据已经加载，但是没有足够的数据展示下一帧  
progress  浏览器正在下载视频/音频
canplay  下载完毕，可以播放
canplaythrough 浏览器预计在可以在不停下来进行缓冲的情况下进行视频播放   
## video获取时长
事件loadedmetadata
```dash
	myVideo.addEventListener('loadedmetadata', () => {
		console.log(myVideo.duration);
	});
```

## 播放、暂停
play() 播放
pause() 暂停

## timeupdate 视频播放位置发生改变时，触发
```dash
	myVideo.addEventListener('timeupdate', () => {
		var currentTime = myVideo.currentTime;
		if (currentTime < 10) {
			myVideo.play();
		} else {
			myVideo.pause();
		}
	})
```

