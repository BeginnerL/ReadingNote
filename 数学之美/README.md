## 统计假设
$\begin{eqnarray*}P(S) & = &P(w_1,w_2,w_3…w_n) \\& = & P(w_1)\cdot P(w_2|w_1)\cdot  P(w_3|w_1,w_2)…\cdot P(w_n|w_1,w_2,…,w_{n-1})\end{eqnarray*}$

马尔科夫假设：只与前面k个值有关

二元模型：$$k=1 $$
$$\downarrow$$
$$\begin{eqnarray*}P(S) & = &P(w_1,w_2,w_3…w_n) \\& = & P(w_1)\cdot P(w_2|w_1)\cdot  P(w_3|w_2)…\cdot P(w_n|w_{n-1})\end{eqnarray*}$$

其中：
$P(w_i|w_{i-1})=\dfrac{P(w_i,w_{i-1})}{P(w_{i-1})}$

N-1阶马尔科夫假设：
$$P(w_i|w_1,w_2,…w_{i-1})=P(w_i|w_{i-N+1},w_{i-N+2},…,w_{i-1})$$

N取值一般小于4：
	- 空间复杂度:$O(|V|^N)$,|V|是词汇量
	- 时间复杂度：$O(|V|^{N-1})$

## 零概率问题，平滑方法
- 古德-图灵估计：
	- 赋予小比例给没有发生的事件
	- 将已发生的事件概率调小
		- 越不可行（频数越小），折扣越多

出现$r$次的单词有$N_r$个，未出现的词数目为$N_0$,语料库大小为$N$:
$$N=\sum\limits_{r=1}^{\infty}rN_r$$

当$r$较小时，估计不可靠，可以使用一个更小的次数$d_r$来替换：
$$d_r=(r+1)\cdot \dfrac{N_{r+1}}{N_r}$$

显然：
$$\sum_rd_r\cdot N_r=N$$

> 依据：
> Zipf’s Law：出现越少次数的词的数目比出现次数多的词的数目多，所以$N_r>N_{r+1}$

解决的问题：
- 没出现的词也有概率
- 出现次数越少的概率折扣越大

### 二元组平滑处理
#### 卡茨退避法：
$(w_{i-1},w_i)$出现次数少也应该平滑处理，应该按古德图灵方法打折，使:
$$\sum\limits_{w_{i-1},w_i seen}P(w_i|w_{i-1})<1$$

估计模型：
$$P(w_i|w_{i-1})=\begin{cases}f(w_i|w_{i-1}) & if~~\#(w_{i-1},w_i) \ge T \\ f_{gt}(w_i|w_{i-1}) & if~~0<\#(w_{i-1},w_i) < T \\Q(w_{i-1})\cdot f(w_i) & otherwise\end{cases}$$

其中：#表示出现频次，T一般取8~10，$f_{gt}$表示经过古德图灵估计后的频度。

$Q(w_i)=\dfrac{1-\sum\limits_{w_i seen}P(w_i|w_{i-1})}{\sum\limits_{w_i unseen}f(w_i)}$
