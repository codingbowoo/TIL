# Matplotlib.pyplot

## Contents

- [bar chart != histogram](#bar-chart)
- [plt.savefig() 했는데 아무것도 나오지 않는다구?](#reset)
- [smooth한 그래프를 그리고 싶습니다](#smooth-interpolate)
- [x축이 날짜입니다](#date-tick-labels)
- [매번 plot 그릴 때마다 너무 헤매서 적어두는 (나름) template](#template)
- [매번 찾는 color code](#color-code)
- [축](#axis)



* * *
### bar chart <a id="bar-chart"></a>
내가 그려야 하는 건 bar plot이었는데, histogram을 붙잡고 씨름하고 있었다. 
- bar chart는 각각의 columns이 categorical variable
- histogram의 각 column은 하나의 연속한 변수의 range를 나눈 것이다.


bar chart는 대략 아래와 같이 그린다.
```python3
import matplotlib.pyplot as plt

fig, ax = plt.subplots()

ax.bar(bar의 중심 위치, plot할 data, bar width, bar label)
# histogram의 경우 ax.hist()를 찾아보자

ax.set_ylabel()
ax.set_title()
ax.set_xticks()
ax.set_xticklabels()
ax.legend()

plt.show()
```
- [Grouped bar chart with labels](https://matplotlib.org/3.2.1/gallery/lines_bars_and_markers/barchart.html#sphx-glr-gallery-lines-bars-and-markers-barchart-py)

* * *
### 축 <a id="axis"></a>
y축의 예시를 들자.
```python3
import matplotlib.pyplot as plt

fig, ax = plt.subplots()

# 뭔가 plot을 하고 나서...

ax.set_ylim(limit) # y축의 전체 range, 곧 limit을 정한다. 
ax.set_yticks(y_tick) #  y축에 그리는 눈금을 정한다.
```

* * *
### x축이 날짜입니다 <a id="date-tick-labels"></a>
- [Date tick labels](https://matplotlib.org/gallery/text_labels_and_annotations/date.html#date-tick-labels)


* * *
### 매번 찾는 color code <a id="color-code"></a>

[Default style: colors in default property cycle](https://matplotlib.org/3.1.3/users/dflt_style_changes.html#colors-color-cycles-and-color-maps)
<br>
아래는 dataframe의 each column(y)을 plot할 때 종종 사용하는 코드다.
```python3
def plot_with_style(df, kind='line', y=None, figsize=None, color=None, linewidth=3, linestyle=None,fontsize=16, ax=None):
    return df.plot(kind=kind, 
                    y=y,
                    #figsize=figsize,
                    color=color,
                    linestyle=linestyle,
                    linewidth=linewidth,
                    fontsize=fontsize,
                    ax=ax, 
                   )
```

* * *
### plt.savefig <a id="reset"></a>

문제의 코드는 이렇게 생겼다. 어떤 format으로 savefig를 해도 그림에 아무것도 나오지 않는 것이다!
```python3
plt.show()
plt.savefig(f, format="png")
plt.savefig(f, format="eps", dpi=1000)
```
그리고 ```plt.show()```를 지우니 해결! 아마도 interactive 환경에서 ```plt.show()```가 내용을 보여주고 초기화해버리는 것 같다. (근거 찾아야 함)


* * *
### smooth한 그래프 - scipy의 interpolate.spline <a id="smooth-interpolate"></a>

신에게는 x와 y의 list가 있는데... 점들을 부드럽게 잇고 싶어진 것이다! scipy의 interpolate의 힘을 빌려보자.
```python3
from scipy.interpolate import make_interp_spline

x, y = map(list, zip(*DATA))
l0, = ax.plot(x, y)

xs = np.linspace(min(x), max(x), 1000)
spl = make_interp_spline(x, y)
ys = spl(xs)
l1, = ax.plot(xs, ys)
```
이렇게 하면 구물구불한 그래프가 나온다. 만약 다항식 형태의 그래프를 원한다면 numpy의 polyfit을 써보자.
- https://docs.scipy.org/doc/scipy/reference/interpolate.html#module-scipy.interpolate


* * *
### Template
```python3
fig, ax = plt.subplots()

l1, = ax.plot(df)
l2, = ax.plot(x, y)

ax.set_xticks(x)
ax.grid(True, linestyle='-.')
ax.tick_params()
ax.legend((l1, l2),
          (name1, name2),
          loc="upper right"
         )
ax.set_xlabel('xlabelname')
ax.set_ylabel('ylabelname')
ax.set_title('titlename')

plt.savefig(f, format='png')
plt.savefig(f, format='eps', dpi=1000)
```
항상 기본이 되는 
- [matplotlib rcParams](https://matplotlib.org/tutorials/introductory/customizing.html#matplotlib-rcparams)
- [matplotlib.axes](https://matplotlib.org/api/axes_api.html#matplotlib.axes.Axes)
- [matplotlib.axes.Axes.plot](https://matplotlib.org/api/_as_gen/matplotlib.axes.Axes.plot.html#matplotlib-axes-axes-plot)
- [Anatomy of a figure](https://matplotlib.org/3.1.1/gallery/showcase/anatomy.html)
