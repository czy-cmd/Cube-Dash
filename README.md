方块冲刺
当前版本：v2.1.6（设计版本 v2.6，作者 czy）
形态：单个 HTML 文件，纯前端、零依赖、打开即玩。
霓虹风格跑酷闪避游戏。点屏幕左右半区变道，贴着障碍擦边攒倍率，越跑越快。
1. 快速开始
- 入口：方块冲刺.html（项目根目录，当前 v2.1.6）
- 在线：https://wbapp-n26s0ofykrynokz16hzww7.app.workbuddy.host/?sharecode=JJBLGZKQ5U
- 本地双击 HTML 即可运行，无需服务器、无需构建。
2. 目录结构
方块冲刺/
├─ 方块冲刺.html              ← 部署入口（v2.1.6，从 v2.1.6/ 复制）
├─ README.md                  ← 本文件（完整版，含机密）
├─ 1.0/                       ← 历史归档
│   ├─ 方块冲刺2.1.5.html      ← v2.1.5 源码备份
│   ├─ 方块冲刺完整源码v2.1.5/ + .zip
│   ├─ 方块冲刺-v2.1.5功能说明.md
│   └─ 各版本文档（玩家/开发者/总开发者手册、设计稿、皮肤、教程等）
└─ 方块冲刺v2.1.6/
    ├─ 方块冲刺v2.1.6.html     ← 本次源码（朋友改版，v2.1.6）
    ├─ 方块冲刺v2.1.6-玩家手册.md
    └─ 方块冲刺v2.1.6-管理员手册.md
注：方块冲刺.html 与 方块冲刺v2.1.6/方块冲刺v2.1.6.html 内容一致。改动源码后要同步这两处。
3. 功能概览
3.1 核心玩法
- 点屏幕左/右半区或方向键变道；擦边攒倍率，越险分越高。
- 速度随波次递增；出口模式可额外得分。
- 五档难度：简单 ×0.8 / 普通 ×1.0 / 困难 ×1.2 / 极限 ×1.3 / 残疾 ×0.7。
3.2 障碍与技能
障碍
行为
单块 / 双块墙
基础躲避
急坠（箭头）
1.6× 速度，点本体 3 下消除
巨墙
横贯跑道留一道缺口
相位（隐身）
虚化态可穿过，用「现」技能逼出
追踪
接近时朝玩家平移一格
技能：慢放（0.5× 持续 4 秒，CD 10 秒）、现（CD 5 秒）、无敌（开发者 + 电脑模式）。
3.3 进阶系统
- 实验玩法 9 项：重力翻转、分数乱动、恐怖画风、幽灵方块、多车道、倒车、密集弹幕、巨墙模式、漂移惯性。可叠加，模式码 MX。
- 恐怖模式：kb-true 开启会话级沉浸恐怖（血红、血雾、心跳、独白、三双眼睛结局）。
- 挑战码：CZYFK2-… 加密，含难度/实验/车道/模式/种子/分数，好友导入严格复现，仅本局。
- 一车道通关：红/蓝/绿点 3/5/10 下，满 150 分通关→宝箱→金币+皮肤。
- 商店金币：游戏中冒金币，主菜单商店消费（测试版）。
- 皮肤/音乐：自定义皮肤代码；3 个音乐地址，B 站视频 iframe，仅声音/声音+视频两模式。
- 账户：昵称+密码登录（非强制），称号在主界面、专属编码在个人主页。
3.4 v2.1.6 修复
- 慢放不再双重减速；极限死亡只清成绩+设置，账户/金币/皮肤/称号保留。
- 渲染用独立随机流 rngVisual，种子复现更稳；开局不再秒冒金币。
- 出口阈值 100/500/1000 后每档 +500；擦边额外加半个倍率分。
- 商店黄金皮肤需先解锁；首次开局基础教程；结算页补用时/条件/种子。
- resetUiSnapshot() 启动复位界面（源码曾是从运行页面抓的快照）；从 save.profile 恢复登录态。
4. 文档索引
文档
面向
位置
方块冲刺v2.1.6-玩家手册.md
玩家
v2.1.6/
方块冲刺-新手教程.txt
纯新手
1.0/
方块冲刺-玩家使用手册.md
玩家（v2.1.5 通用）
1.0/
方块冲刺-普通开发者使用手册.md
二次开发者
1.0/
方块冲刺-总开发者使用手册.md
项目所有者
1.0/
方块冲刺v2.1.6-管理员手册.md
维护者
v2.1.6/
方块冲刺-游戏详细设计.md/.txt
设计稿
1.0/
方块冲刺-恐怖模式设计稿.md
恐怖模式
1.0/
方块冲刺-扩展的实验性玩法.md
实验玩法
1.0/
皮肤使用方法-玩家.md / -开发者.md
皮肤
1.0/
方块冲刺-功能讲解.mp4
功能讲解视频（38.5s）
1.0/
5. 技术架构
- 单文件：HTML + CSS + JS 全在 方块冲刺.html，逻辑包在一个 IIFE 里，顶层变量不挂 window。
- 渲染：Canvas 2D，1280×720 逻辑分辨率自适应。
- 音效：Web Audio 实时合成，无音频文件。
- 存档：localStorage 键 fkcc.save.v1，含设置、最高分、账户、称号、编码等。
- 随机数：三条独立流 rngMain（游戏）、rngDecor、rngVisual（渲染），保证同种子复现。
- 种子：parseSeedInput() 支持字母/数字/emoji，纯数字原样保留，显示统一走 dispSeed()。
- 状态机：state ∈ menu / playing / paused / adPaused / over；各 UI 是 .layer 面板。
6. 命令速查
主菜单「高级」→ 确定 → 输入框。命令不区分大小写，空格/连字符通用。
命令
作用
性质
get from enter
出口模式
本局
url-网址 [-t 秒]
定时开网页；url-none 关闭
本局
kb-true / kb-false
开/关恐怖模式
会话
tp N / tp N next / tp N M.ago
跳波
本局
about-things
永久操作写存档
永久
about-choose
本会话不写存档
会话
about-command
命令模式
本局
about-game
直接开局
本局
type on devczy
开发者模式
本局
7. 后台（未开发完整）
7.1 密码与后台
密码
权限
devczy
开发者模式总密码；后台只读
cczzyyopen
后台全开（新建/删除账户、增减金币积分、存档码/配置码）
后台入口：高级输入框 admin-view（只读）/ admin-edit（全开）/ admin-pw <密码>。
管理界面表格四列：账户 / 金币 / 积分 / 操作；支持导入存档码、±100 币、±100 分。
7.2 五级体系
LEVELS=[
  {lv:1,need:100, coins:500,  badge:'初露锋芒'},
  {lv:2,need:300, coins:1200, badge:'渐入佳境'},
  {lv:3,need:600, coins:2500, badge:'势不可挡'},
  {lv:4,need:1000,coins:5000, badge:'登峰造极'},
  {lv:5,need:1500,coins:10000,badge:'传说'}
];
级别
目标分
称号
等级码
1
100
初露锋芒
CZYFK2-O14WI3YJQYXAXGI9I4B
2
300
渐入佳境
CZYFK2-O14XI5YJQP94YT8WX95
3
600
势不可挡
CZYFK2-O14YI8YJQCXDETETZOQ
4
1000
登峰造极
CZYFK2-O14ZI3YJRENMZJIF161E
5
1500
传说
CZYFK2-O14.I32JRERL0HYIIOHW
达标结算：金币 + 称号 + CZYBD-… 专属编码（存档去重）。改 LEVELS.need 会改变码，须重新导出并同步本表。
7.3 加密与编码
- 密钥：CODE_KEY='FKCC-V16-CHALLENGE-2026-czy'
- codeSeal() / codeOpen()：流加密，外层 6 位校验防篡改 + 内层 4 位防伪造。
- 码前缀：挑战码 CZYFK2-、专属编码 CZYBD-、装逼码 CZYBB-JX-、配置码 FKCC-CFG:。
- 改 CODE_KEY 会让所有已发出的码一次性失效。
7.4 存档敏感字段
coins / lane1Cleared / seenTips / shopBought / accounts / profile / officialDone / badges / codes。
新增字段要四处同步：DEFAULT_SETTINGS、save 初始、两处硬编码重置（gameOver 极限分支已改为不清档，setDelete 仍重置）。
8. 测试与发布
- 冒烟测试：C:\Users\54215\AppData\Local\Temp\fkcc_v15_test.js（DOM 桩，217 项全过）；v2.1.6 副本 fkcc_v216_test.js。
- 校验：node --check + DOM 引用检查（$('id') 必须存在）+ 手册敏感词断言。
- 发布：workbuddy_sites_deploy，static，entryHtml:'方块冲刺.html'，domainPrefix:'block-dash'，复用 appId wbapp_n26S0ofyKrYNOkZ16HzWw7，分享链接不变。
- 发布前：改 CONFIG.appVersion + LOG 补条目 + 跑全部测试。
