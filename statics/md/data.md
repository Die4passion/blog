## 备注:

1. 所有奖金都是减掉平台提成之后算

2. 每一级提取的奖金是减掉前10之后再算

3. 参赛人数少于多少人的时候,只有前3有奖

4. 游戏    game_rule

          开始    每天进行多少场   每次时长(分钟)   参赛金额    平台提成      最少参赛人数(>3)           参赛人数临界值 (>10)      

   name desc stime     count               size             pay         draw              min_person           more_person             

            H:i         7                60        默认10              10             20    

5. 我的战绩 user_game_score

id open_id game_id score 参赛时间  第几场   pay         yq_money   名次    场次id
                                                5     0       

4.每一级对应的奖金 app_game_win_level

id game_id  level  gain   百分比

               1    50      10
               2    25      20
               3    10      30
               4    5       40
               5    1       50s

5. 前10名对应的奖金  app_game_top_10

    id game_id  rank   百分比   少于固定人数(只有前3有奖)

                1                   50%
                2                   30%
                3                   20%                           

app_game_rule     user_game_score   app_game_top_10     app_game_win_level       app_game_msatch
