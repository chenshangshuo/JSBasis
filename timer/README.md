
### 定时器
最近在牛客上刷题时，遇到些有关定时器的问题，习惯了一直是`setTimeout`及`setInterval`来弄些轮播，却未曾深入思考，今天正好总结下。
如何停止定时器？
```
setTimeout和setInterval函数，都返回一个表示计数器编号的整数值，将该整数传入clearTimeout和clearInterval函数，就可以取消对应的定时器。
```
**使用场景：在控制台每隔1000毫秒打印出1~10，超过10之后终止**
```
function count(a,b){
	let timer = setInterval(function(){
		if (a<b) {
		        a++
			console.log(a)
		}else{
			clearInterval(timer)
			console.log('time out')
		}
	},1000)
}
count(1,10) //1、2、3....9
```
有效地利用`clearTimeout`和`clearInterval`可以实现节流函数。切换到下一个使用场景。在操作页面时，监听的事件过于频繁，如
- 歌曲搜索时，实时展示搜索结果
- 监听屏幕尺寸变化
- 鼠标滚轮的滚动

举例歌曲搜索，每次监听输入框中的`input`事件，获取`value`，像后台发生Ajax请求，每次用户的输入都会被监听，结果会频繁地发送Ajax请求，大大降低性能。
#### 通过上面的示例我们可以利用`setTimeou`，延迟AJAX的发送时间，并如果用户在这段时间内重复操作，利用`clearTimeout`清除定时器，阻止发送AJAX.
