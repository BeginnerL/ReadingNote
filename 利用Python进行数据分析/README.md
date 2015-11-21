# 利用Python进行数据分析

列表推导逐行处理文件：

    record = [json.loads(line) for line in open(‘xxx’)]-
	xx = [rec[‘key’] for rec in records if ‘key’ in rec]
字典判断:

	if key in dict:
		pass

	if k,v in dict.items():
	pass

默认字典：

	from collections import defaultdict
	dict = defaultdict(int)

`collections.Counter`查找出现频率最高的数据：

	from collections import Counter
	counts = Counter(xxx)
	counts.most_common(10)

pandas：

	from pandas import DataFrame,Series
	import pandas as pd
	import numpy as np

	frame = DataFrame(record)
	# frame[‘tz’]返回Series对象
	# 频次最高的10个item
	print frame[‘tz’].value_counts()[:10] 
	# 清除未知数据：
	clean_tz = frame[‘tz’].fillna(‘Missing’)
	clean_tz[clean_tz==‘’] = “Unknown”
