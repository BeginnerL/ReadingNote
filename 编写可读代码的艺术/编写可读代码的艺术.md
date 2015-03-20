> **可读性基本原理**：别人理解它所需时间最小化
> 一般而言，越短越好

## 表面层次改进
#### 信息→名字
 * 使用专业词汇
	 * `get`→`Fetch`,`Download`
	 * `size`→`Heigth`,`NumNodes`,`MemoryBytes`
	 * `Stop`→`Kill`(无法恢复),`Pause`(存在`resum`)
	 * `send`→`deliver`,`dispatch`,`announce`,`distribute`,`route`
	 * `find`→`search`,`extract`,`locate`,`recover`
	 * `start`→`launch`,`create`,`begin`,`open`
	 * `make`→`create`,`set up`,`build`,`generate`,`compose`,`add`,`new`
 * 避免泛泛的名字
 	 * `temp`→`temp_file`
	 * `retval`→`sum_squares`
	 * `foo`
	 * `i`,`j`,`k`→`clubs[ci].students[sj].menbers[mk]`
	 * `it`
 * 具体名字代替抽象
	 * `ServerCanStart`→`CanListenOnPort`
 * 使用前后缀
	 * 增加描述
		 * `id`→`hex_id`
	 * 单位
		 * `start`→`start_ms`
		 * `size`→`size_mb`
		 * `limit`→`max_kbps`
		 * `angle`→`degrees_cw`
	 * 附带重要信息：【只】在别人要使用的地方
		 * `password`→`plaintext_password`
		 * `html`→`html_utf8`
		 * `data`→`data_urlenc`
 * 名字长度
	 * 小作用域使用短名
	 * 常用替换
		 * `evaluation`→`eval`
		 * `document`→`doc`
		 * `string`→`str`
	 * 去掉无用单词
		 * `ConvertToString`→`ToString`
		 * `DoServerLoop`→`ServerLoop`
 * 利用格式来表达含义
	 * 宏→大写
	 * 常量→`kConstName`
	 * 类成员以`_`结尾，如`offset_`

#### 不会被误解
* `filter`：无法区分是滤除还是滤出
* `clip(text,len)`→`Truncate(text,len)`
* `max_length`:没有说明是字节单位
* 不要用`CART_LIMIT`等无法判断是`＞`还是`≥`的名字，用`MAX`,`MIN`
* 不要用`start`/`stop`来表示范围，因为不知道是否包含，用`last`/`first`
* 用`begin`/`end`来表示包含/排除范围【e.g.描述时间范围】
* 布尔类型前面加上`is`,`has`,`can`,`should`
	* 不要用反义：`bool disable_ssl = false`→`bool use_ssl = true`
* `read`这类词禁用，无法判断读了还是需要读
* 与使用者希望匹配：
	* `getMean`如果希望做大量迭代计算，与使用者希望不符
	* `list::size()`：同上

#### 审美
* 函数参数通过换行来保持一致
## 简化循环和逻辑

## 重新组织代码