### todo

- [x] match信息需要按当前时间查询
- [x] 需要再给一个广告信息
- [x] 单个比赛文字说明
- [x] 我的战绩页面
- [x] 单个玩家参加比赛   
- [x] 单个玩家今日战绩      都是针对单个游戏的
- [x] 单个玩家昨日战绩
- [x] 单个玩家战绩
- [ ] 文章 评论(数) | 点赞(数) | 分享(数)  | 谁点赞的 | 热门 | 评论审核 

---

### 小目标

- [x] 所有查询页面

- [x] 运气最佳(钱 open_id  name)    今日最早(open_id name 时间)     坚持最久(open_id name last)

- [x] 支付 ->  报名 

- [x] 打卡

- [x] 定时任务1 调试  

- [x] 定时任务2

- [x] 测试

---

### 比赛

- [ ] 列表信息完善

- [ ] 得分排名分钱
1. 报名
- 新增day_goal_record

- 新增day_goal_count 并 `update`(总报名人数+1,  状态未开始1

- user_goal_count  `update`投入金额+=报名费
2. 打卡
- day_goal_record `update` 
  
  ```
  check_time 
  status 打卡 2
  ```

- user_goal_count `crear or update`
  
  ```
  first_time
  last_time
  pass_count
  best_time
  worst_time
  last_day
  ```

- day_goal_count `update`
  
  ```
  pass_count
  status   ing 2
  ```
1. 数据来源  `scrapy` + `beautifulsoap`

2. 存储   `mysql`

3. 前端  `web+app`

4. `sendMsg`            type 3

5. `validationCode`

6. `forgetPassword`



流程图 工具:

- draw.io
- 在线 [zenflow](https://www.zenflowchart.com/documents) 
- [code2flow](https://code2flow.com/)



> **`redis`使用**



done

- `game_rule  hash key by game_id`
- `game_ads hash key by id`
- `banner hash key by id`
- 生成`game_match`的时候, 全部缓存到`redis`
- 比赛存redis



`todo`

- 优化之前的redis写入读取过程
- 其他需要加入redis的加入redis
- 将redis定时同步到mysql, 并删掉无用redis



- 
- `user_game_record` 已完结`(status>1)`的时候
- 订单相关
- 战绩昨天的放redis
- 小红点信息 
- 小目标
  - 今日活动完成情况



### time management for system administrators (时间管理)

- 把所有时间管理的东西放一起
- 大脑只用于现在重要的事情, 其他使用外部存储
  - 在床边放纸和笔。当一些事让你睡不着时,  把他写下来再睡
  - 多用手机记录临时的想法
- 每天早上花时间计划一天
- 定期发生的事情开发例行公事
  - 让每台服务器都以相同的状态运行 (包括更改配置和更新)
    - `SaltStack` `Ansible` `Puppet` `chef` 等配置同步
    - `docker` 等容器技术
  - 编辑配置文件之前总是备份 (按日期)
- 常用命令alias
  - `alias book='cd ~/projects/books/time/chapters'`
  - `alias inva='cd ~/projects/inventory/groupa ; export INVSTYLE=A'`
  - `alias rank='cd /home/rank/data && date >>.log'`



### git flow

- fork
- checkout a new branch
- code & test
- commit & push
- issue  merge request
- code review => approve  by code viewer
- merge & deploy



**`gitlab`**

自动部署, 代码测试, 自动发邮件或消息qq等

`docker`

分布式测试

测试包括:

- 单元测试
- 冒烟测试 (全部流程最基本功能, CI 里自动化)
- 回归测试 (相对新功能的原有系统的正确性)
- 大数据测试

`CI/CD`  *eg: gitlab*

-  持续集成 / 交付 / 部署
- staging / production 环境
- 容器 

### work flow

#### scrum:

- sprint
- daily scrum
- plan meeting

#### jira 管理项目

做产品决策时尽量使用数据支持

产品ab测试:

​	多个版本, 分别进行测试.

> 最极端的例子是 Google 的即时通信解决方案。Android 上一度曾出现过 4 款不同的产品：Google Talk、Google+ Messenger、Messaging （Android 的短信应用）以及 Google Voice。Google Hangouts 最终胜出，把其他的都合并进了一个平台。



### TCP/UDP

- 实时音视频用udp
- nat穿透用udp



### 优化的本质

1. 物理上, 内存, cpu, 磁盘, 网络io, 文件io, 之间权衡
2. 逻辑上, 避免不必要的计算开销, 找最优解



### TCP多进程

- ~~TCP并发服务器, 每个客户一个子进程, 错误的~~
- TCP预先派生子进程, accept 无锁保护
  - 优点: 无需引入父进程执行fork
  - 缺点: 必须在启动阶段猜测需要预创建多少子进程
  - 可以监控闲置子进程数, 动态增减子进程数
  - 由于子进程阻塞在accept上, 但是当一个连接到达时只会有一个子进程获得连接. 但是所有的子进程都被唤醒了, 这就叫惊群, 影响性能.
  - 客户端不多的时候, 比如10个, 使用这个比较方便
- TCP预先派生子进程, 使用文件上锁保护accept
- TCP预先派生子进程, 使用线程互斥锁上锁保护accept
- TCP预先派生子进程, 内存上锁, 传递描述符, 主进程accept



- 预先创建线程服务器，使用互斥锁上锁保护accept
- 预先创建线程服务器，由主线程调用accept
- select在一个进程中同时服务多个TCP服务器



程序优化:

- 降低数据精度
- 减少函数调用
- 空间换时间
- 少用乘法除法取余, 多用位移替代
- 尽量减少条件分支
- 将最可能的分支放到if
- 少用全局变量
- 一次性多取数据, 而不是分批次取
- 数据对齐访问
- 将浮点数定点化