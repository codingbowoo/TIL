# Matplotlib.pyplot

## Contents
- [plt.savefig() 했는데 아무것도 나오지 않는다구?](#reset)
- [매번 plot 그릴 때마다 너무 헤매서 적어두는 (나름) template](#template)

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
