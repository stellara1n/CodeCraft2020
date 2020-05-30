# CodeCraft2020
* 队名：杰尼龟
* 成绩：江山赛区 初赛第二 复赛第一 决赛全国第七  
  
### 初赛
* 题目：有向图中找出所有长度为3~7的环。
* 方法：7+3 对每个起始点，先在反向图上，从起始点搜索三步得到其他点到起始点的可达性。正向七步搜索路径，后3步利用反向可达性剪枝。

### 复赛
* 题目：在初赛基础上增加对环相邻边金额的限制。最后一天改为，输入金额为不超两位小数的浮点数，环的长度为3~8。
* 方法：改为4+4。 对每个起始点s，反向DFS四步存下所有四步路径a->b->c->d->s，以链表形式存储，每个a单独形成一个链表。如果去掉起始点s以及用于“衔接”的a，反向其实只存储了bcd这3个有效点。正向4步，通过2+3、3、3+3、4+3、4、4+4的方式分别拼出长度为5、3、6、7、4、8的环。由于存储的反向路径不是字典序，而每次对所有反向路径一起排序开销太大且没有必要，因此改为“按需排序”，当到达某个衔接点时，对没有排序过的衔接点所对应的反向路径，从链表中取出放到连续数组中排序并标记。以后若重复用到，可以直接到这个连续数组中找。在循环中，判断的先后顺序非常重要，应当让强剪枝的判断优先。另外，对正向反向中重复节点的判断，直接进行不等判断 比 每个点判vis更好，因为访存的开销大于数值判断。

### 决赛

具体有空补完...
