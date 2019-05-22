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

