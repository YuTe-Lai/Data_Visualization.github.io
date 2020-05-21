# Plotly
參考資料：(https://kknews.cc/zh-tw/code/vr2jmeq.html)

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
![Image of plotly1]
(https://github.com/YuTe-Lai/plotly.github.io/blob/master/plotly1.png)
```

















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
