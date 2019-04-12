<h2>页面渲染过程</h2>
<ol>
	<li>处理HTML来创建DOM tree</li>
	<li>处理CSS来创建CSSOM tree</li>
	<li>根据DOM tree和CSSOM tree合并render tree</li>
	<li>根据render tree来进行页面布局</li>
	<li>绘制render tree</li>
</ol>


<h2>CSS reflow & repaint</h2>
<h4>reflow: render tree的重新构建。包括以下几种情况：</h4>
<ul>
	<li>页面初始渲染</li>
	<li>DOM元素的增删</li>
	<li>DOM元素的位置、尺寸以及引起尺寸变化的内容改变</li>
	<li>resize事件</li>
</ul>
<h4>repaint: render tree中只影响外观而不影响布局的改变。</h4>