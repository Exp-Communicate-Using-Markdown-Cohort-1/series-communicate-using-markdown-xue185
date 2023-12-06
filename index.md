# 因果学习
## 数理统计 因果推断
### 医疗治疗、政策、干预


因果学习的数学推理
因果学习的可解释性

相关性  ρ 线性相关系数  不等于因果

因果性和相关性的差异

![images](https://github.com/Exp-Communicate-Using-Markdown-Cohort-1/series-communicate-using-markdown-xue185/assets/59075323/d6692305-006b-4cf5-a1af-73e3d87eb89c)


![images](https://github.com/Exp-Communicate-Using-Markdown-Cohort-1/series-communicate-using-markdown-xue185/assets/59075323/9969b039-ecb6-406c-b0ea-bba0ff9247f6)
相关性映射为关联性

````
from causalml.inference.meta import LRSRegressor
from causalml.dataset import synthetic_data

y, X, treatment, _, _, _ = synthetic_data(mode=1, n=1000, p=5, sigma=1.0)

# X是一个数组，X的每个元素是一个向量。
# X举例：用户特征

# treatment是一个数组，treatment的每个元素是0或1。
# treatment举例：对该用户是否发优惠券

# y是一个数组，y是训练目标，y的每个元素可能为0或1，也可为float。
# y举例：该用户是否下单/该用户下单量

lr = LRSRegressor()
treatment_effect, lower_bound, upper_bound = lr.estimate_ate(X, treatment, y)
print('Average Treatment Effect by Linear Regression S-learner: {:.2f} ({:.2f}, {:.2f})'.format(treatment_effect[0], lower_bound[0], upper_bound[0]))

# treatment_effect 是一个float值
# lower_bound 是 treatment_effect 的下置信范围
# upper_bound 是 treatment_effect 的上置信范围
````
