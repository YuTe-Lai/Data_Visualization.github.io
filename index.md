# Plotly
參考資料：<br>
[https://kknews.cc/zh-tw/code/vr2jmeq.html](https://kknews.cc/zh-tw/code/vr2jmeq.html)<br>
[https://kknews.cc/zh-tw/news/mnyeakg.html](https://kknews.cc/zh-tw/news/mnyeakg.html)<br>
[https://www.luoow.com/dc_tw/200924837](https://www.luoow.com/dc_tw/200924837)<br>
[markers](https://guides.github.com/features/mastering-markdown/)<br>

## 離線繪圖方式
  Plotly中繪製圖像有在線和離線兩種方式，在線繪圖需要註冊帳號獲取API key。而離線繪圖分成兩種`plotly.offline.plot()`和`plotly.offline.iplot()`兩種，前者會在當前工作目錄下生成一個html格式的圖，而後者為jupyter notebook中專用的方法，直接將圖嵌在ipynb文件中。<br>
（注意，在jupyter notebook中使用`plotly.offline.iplot()`時，需要在之前運行`plotly.offline.init_notebook_mode()`以完成繪圖代碼的初始化，否則會報錯）。<br>簡單舉例：

```python
import plotly
import plotly.graph_objs as go

plotly.offline.init_notebook_mode()    #初始化jupyter notebook中的繪圖模式

plotly.offline.plot([{'x':[1,2,3], 'y':[4,8,1]}],
image_height=600,
image_width=1600)                      #繪製基本折線圖，尺寸為1600*600
```
![Image of plotly1](plotly1.png)

  在plotly中的圖層元素(數據)與圖的背景、座標軸等是獨立分開的。前者使用Graph_objs定義好參數後便能將數據圖形化。但如果想要在背景圖層上有更多自定義化的內容，就需要定義Layout()。

## Graph_objs
  先根據繪圖需求從graph_objs中導入相應的obj，接下來需要做的事情是基於待展示的數據，為指定的obj配置相關參數，這在plotly中稱為構造traces
### 建造Traces
  二維散點圖
```python
#創建1000筆二維正分佈數據
n = 1000
random_x = np.random.randn(n)
random_y = np.random.randn(n)

#建造Trace
trace = go.Scatter(
x = random_x,
y = random_y,
mode = 'markers')

#將Trace儲存於列表
data = [trace]

#初始化繪圖模式
plotly.offline.init_notebook_mode()

#開始繪圖
plotly.offline.iplot(data, filename='basic-scatter')
```
![Image of plotly2](plotly2.png)
<br>


一張圖中可以疊加多個trace
```python
n = 100
random_x = np.linspace(0,10,n)
random_y0 = np.random.randn(n)+5
random_y1 = np.random.randn(n)
random_y2 = np.random.randn(n)-5 
#+5、-5是為了方便辨識三種圖

trace0 = go.Scatter(
x = random_x,
y = random_y0,
mode = 'markers',
name = 'markers'
)

trace1 = go.Scatter(
x = random_x,
y = random_y1,
mode = 'lines+markers',
name = 'lines+markers'
)

trace2 = go.Scatter(
x = random_x,
y = random_y2,
mode = 'lines',
name = 'lines')

data = [trace0,trace1,trace2]
plotly.offline.init_notebook_mode()
plotly.offline.iplot(data, filename='basic-scatter')
```
![Image of plotly3](plotly3.png)








### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/YuTe-Lai/ploty.github.io/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://help.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.
