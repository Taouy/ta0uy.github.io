<!DOCTYPE html>
<html lang="zh-CN">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>个人成长目标管理</title>
<style>
*{box-sizing:border-box;margin:0;padding:0;font-family:-apple-system,BlinkMacSystemFont,Segoe UI,Roboto,Helvetica,Arial}
body{background:#f6f8fb;color:#222;padding:20px}
.container{max-width:1000px;margin:0 auto}
.header{display:flex;justify-content:space-between;align-items:center;margin-bottom:20px;flex-wrap:wrap;gap:12px}
.card{background:#fff;border-radius:16px;box-shadow:0 2px 12px rgba(0,0,0,0.06);padding:20px;margin-bottom:16px}
.title{font-size:22px;font-weight:700;color:#111;margin-bottom:12px}
.search-bar{width:100%;padding:10px 14px;border-radius:12px;border:1px solid #e2e8f0;outline:none;font-size:14px;margin-bottom:16px}
.goal-item{display:flex;align-items:center;justify-content:space-between;padding:12px 14px;border-radius:12px;background:#f9fafb;margin-bottom:8px;gap:10px}
.goal-item.done{background:#e6f7e6}
.goal-text{flex:1;font-size:14px}
.goal-meta{display:flex;gap:8px;font-size:12px;color:#666}
.btn{padding:6px 12px;border-radius:10px;border:none;cursor:pointer;font-size:13px;font-weight:500}
.btn-primary{background:#3b82f6;color:#fff}
.btn-success{background:#10b981;color:#fff}
.btn-light{background:#e2e8f0;color:#333}
.timetable{display:grid;grid-template-columns:80px 1fr;gap:8px;font-size:14px;margin-top:12px}
.time-item{background:#eff6ff;padding:8px 10px;border-radius:10px;text-align:center;font-weight:600}
.content-item{background:#f9fafb;padding:8px 12px;border-radius:10px}
.week-schedule{display:flex;gap:10px;flex-wrap:wrap;margin-top:12px}
.week-tag{padding:8px 12px;background:#f0f9ff;border-radius:12px;font-size:13px;color:#0369a1;font-weight:500}
.modal{position:fixed;top:0;left:0;width:100%;height:100%;background:rgba(0,0,0,0.4);display:none;justify-content:center;align-items:center}
.modal-content{background:#fff;width:90%;max-width:460px;border-radius:16px;padding:24px}
.modal-title{font-size:18px;font-weight:700;margin-bottom:16px}
.form-row{margin-bottom:14px}
.form-row label{display:block;font-size:14px;margin-bottom:6px}
.form-row input,.form-row textarea{width:100%;padding:10px 12px;border-radius:10px;border:1px solid #e2e8f0;outline:none}
.modal-buttons{display:flex;justify-content:flex-end;gap:10px;margin-top:20px}
</style>
</head>
<body>
<div class="container">

<div class="header">
<h1>个人成长目标管理</h1>
<div>
<button class="btn btn-light" id="openModal">设置目标</button>
</div>
</div>

<input type="text" class="search-bar" id="searchInput" placeholder="搜索目标...">

<div class="card">
<div class="title">今日待完成</div>
<div id="todayList">
</div>
</div>

<div class="card">
<div class="title">每日时间表</div>
<div class="timetable">
<div class="time-item">07:00</div><div class="content-item">起床、洗漱、拉伸</div>
<div class="time-item">07:20</div><div class="content-item">早餐 + 冥想5分钟</div>
<div class="time-item">07:40</div><div class="content-item">通勤</div>
<div class="time-item">09:30-18:00</div><div class="content-item">上班 + 一半时间学习（逆向/SRE/网络编程）</div>
<div class="time-item">18:00-18:40</div><div class="content-item">下班通勤</div>
<div class="time-item">18:40-19:40</div><div class="content-item">晚餐休息</div>
<div class="time-item">19:40-20:20</div><div class="content-item">健身 / 身体修复</div>
<div class="time-item">20:20-21:00</div><div class="content-item">阅读 / 自省</div>
<div class="time-item">21:00-22:00</div><div class="content-item">娱乐（刺客信条/影视）</div>
<div class="time-item">22:00-22:30</div><div class="content-item">护肤、形象整理</div>
<div class="time-item">22:30-22:50</div><div class="content-item">情绪复盘</div>
<div class="time-item">23:00</div><div class="content-item">睡觉</div>
</div>
</div>

<div class="card">
<div class="title">每周学习安排</div>
<div class="week-schedule">
<div class="week-tag">周一/三/五：逆向破解</div>
<div class="week-tag">周二/四：SRE + 网络编程</div>
<div class="week-tag">周六：AI Coding + 阅读 + 社交</div>
<div class="week-tag">周日：放松、健身、总结</div>
</div>
</div>

<div class="card">
<div class="title">周期目标总览</div>
<div style="overflow-x:auto">
<table style="width:100%;border-collapse:separate;border-spacing:0;border-radius:12px;overflow:hidden">
<thead>
<tr style="background:#eff6ff">
<th style="padding:12px;text-align:left">项目</th>
<th style="padding:12px;text-align:left">一周目标</th>
<th style="padding:12px;text-align:left">半个月目标</th>
<th style="padding:12px;text-align:left">一个月目标</th>
</tr>
</thead>
<tbody>
<tr><td style="padding:10px;border-bottom:1px solid #f0f0f0">逆向破解</td><td style="padding:10px;border-bottom:1px solid #f0f0f0">x64dbg断点、调用栈</td><td style="padding:10px;border-bottom:1px solid #f0f0f0">定位3处校验逻辑</td><td style="padding:10px;border-bottom:1px solid #f0f0f0">完成一次小破解</td></tr>
<tr><td style="padding:10px;border-bottom:1px solid #f0f0f0">SRE</td><td style="padding:10px;border-bottom:1px solid #f0f0f0">Linux命令、日志</td><td style="padding:10px;border-bottom:1px solid #f0f0f0">排查简单异常</td><td style="padding:10px;border-bottom:1px solid #f0f0f0">自动化脚本</td></tr>
<tr><td style="padding:10px;border-bottom:1px solid #f0f0f0">网络编程</td><td style="padding:10px;border-bottom:1px solid #f0f0f0">TCP/UDP+抓包</td><td style="padding:10px;border-bottom:1px solid #f0f0f0">Socket Demo</td><td style="padding:10px;border-bottom:1px solid #f0f0f0">分析网络问题</td></tr>
<tr><td style="padding:10px;border-bottom:1px solid #f0f0f0">健身</td><td style="padding:10px;border-bottom:1px solid #f0f0f0">每周3次</td><td style="padding:10px;border-bottom:1px solid #f0f0f0">肩颈好转</td><td style="padding:10px;border-bottom:1px solid #f0f0f0">体态精力提升</td></tr>
<tr><td style="padding:10px;border-bottom:1px solid #f0f0f0">身体修复</td><td style="padding:10px;border-bottom:1px solid #f0f0f0">坚持护理</td><td style="padding:10px;border-bottom:1px solid #f0f0f0">睡眠颈椎改善</td><td style="padding:10px;border-bottom:1px solid #f0f0f0">不适明显减轻</td></tr>
<tr><td style="padding:10px;border-bottom:1px solid #f0f0f0">早睡早起</td><td style="padding:10px;border-bottom:1px solid #f0f0f0">23:00睡 7:00起</td><td style="padding:10px;border-bottom:1px solid #f0f0f0">生物钟稳定</td><td style="padding:10px;border-bottom:1px solid #f0f0f0">白天精神充足</td></tr>
<tr><td style="padding:10px;border-bottom:1px solid #f0f0f0">心态训练</td><td style="padding:10px;border-bottom:1px solid #f0f0f0">烦躁先停10秒</td><td style="padding:10px;border-bottom:1px solid #f0f0f0">快速平复情绪</td><td style="padding:10px;border-bottom:1px solid #f0f0f0">冷静不内耗</td></tr>
<tr><td style="padding:10px;border-bottom:1px solid #f0f0f0">自省冥想</td><td style="padding:10px;border-bottom:1px solid #f0f0f0">每日5分钟复盘</td><td style="padding:10px;border-bottom:1px solid #f0f0f0">每周总结</td><td style="padding:10px;border-bottom:1px solid #f0f0f0">稳定觉察习惯</td></tr>
<tr><td style="padding:10px;border-bottom:1px solid #f0f0f0">交流交友</td><td style="padding:10px;border-bottom:1px solid #f0f0f0">主动联系朋友</td><td style="padding:10px;border-bottom:1px solid #f0f0f0">轻度社交</td><td style="padding:10px;border-bottom:1px solid #f0f0f0">稳定关系</td></tr>
<tr><td style="padding:10px;border-bottom:1px solid #f0f0f0">文学阅读</td><td style="padding:10px;border-bottom:1px solid #f0f0f0">每日20分钟</td><td style="padding:10px;border-bottom:1px solid #f0f0f0">读完半本~1本</td><td style="padding:10px;border-bottom:1px solid #f0f0f0">读完1~2本</td></tr>
<tr><td style="padding:10px;border-bottom:1px solid #f0f0f0">影视娱乐</td><td style="padding:10px;border-bottom:1px solid #f0f0f0">控制时长</td><td style="padding:10px;border-bottom:1px solid #f0f0f0">看完1部</td><td style="padding:10px;border-bottom:1px solid #f0f0f0">不沉迷</td></tr>
<tr><td style="padding:10px;border-bottom:1px solid #f0f0f0">刺客信条</td><td style="padding:10px;border-bottom:1px solid #f0f0f0">每周2~3次</td><td style="padding:10px;border-bottom:1px solid #f0f0f0">推进主线</td><td style="padding:10px;border-bottom:1px solid #f0f0f0">完成一部</td></tr>
<tr><td style="padding:10px;border-bottom:1px solid #f0f0f0">AI Coding</td><td style="padding:10px;border-bottom:1px solid #f0f0f0">用AI写脚本</td><td style="padding:10px;border-bottom:1px solid #f0f0f0">完成小工具</td><td style="padding:10px;border-bottom:1px solid #f0f0f0">完成小项目</td></tr>
<tr><td style="padding:10px;border-bottom:1px solid #f0f0f0">购物改造</td><td style="padding:10px;border-bottom:1px solid #f0f0f0">整理清单</td><td style="padding:10px;border-bottom:1px solid #f0f0f0">购入形象物品</td><td style="padding:10px;border-bottom:1px solid #f0f0f0">外在干净精神</td></tr>
<tr><td style="padding:10px;border-bottom:1px solid #f0f0f0">情绪调控</td><td style="padding:10px;border-bottom:1px solid #f0f0f0">不冲动不内耗</td><td style="padding:10px;border-bottom:1px solid #f0f0f0">波动减少</td><td style="padding:10px;border-bottom:1px solid #f0f0f0">心态平稳</td></tr>
</tbody>
</table>
</div>
</div>

</div>

<div class="modal" id="modal">
<div class="modal-content">
<div class="modal-title">设置今日目标</div>
<div class="form-row">
<label>目标内容</label>
<input type="text" id="goalContent" placeholder="输入今天要完成的事">
</div>
<div class="modal-buttons">
<button class="btn btn-light" id="closeModal">取消</button>
<button class="btn btn-primary" id="saveGoal">保存</button>
</div>
</div>
</div>

<script>
const defaultGoals = [
"完成逆向破解学习30分钟",
"SRE 命令练习",
"健身/肩颈拉伸",
"阅读20分钟",
"情绪复盘5分钟",
"早睡23:00前"
]

const todayList = document.getElementById('todayList')
const searchInput = document.getElementById('searchInput')
const modal = document.getElementById('modal')
const openModal = document.getElementById('openModal')
const closeModal = document.getElementById('closeModal')
const saveGoal = document.getElementById('saveGoal')
const goalContent = document.getElementById('goalContent')

function renderGoals(list){
todayList.innerHTML = ''
list.forEach((g,i)=>{
const item = document.createElement('div')
item.className = `goal-item ${g.done?'done':''}`
item.innerHTML = `
<div class="goal-text">${g.text}</div>
<div class="goal-meta">
<button class="btn ${g.done?'btn-light':'btn-success'}" onclick="toggleDone(${i})">${g.done?'已完成':'今日已完成'}</button>
</div>
`
todayList.appendChild(item)
})
}

let goals = JSON.parse(localStorage.getItem('myGoals')) || defaultGoals.map(t=>({text:t,done:false}))

function saveToStorage(){
localStorage.setItem('myGoals',JSON.stringify(goals))
}

function toggleDone(index){
goals[index].done = !goals[index].done
saveToStorage()
renderGoals(goals)
}

searchInput.addEventListener('input',(e)=>{
const kw = e.target.value.toLowerCase()
const filtered = goals.filter(g=>g.text.toLowerCase().includes(kw))
renderGoals(filtered)
})

openModal.onclick = ()=>{modal.style.display='flex'}
closeModal.onclick = ()=>{modal.style.display='none'}
saveGoal.onclick = ()=>{
const t = goalContent.value.trim()
if(!t)return
goals.unshift({text:t,done:false})
saveToStorage()
renderGoals(goals)
goalContent.value=''
modal.style.display='none'
}

renderGoals(goals)
</script>
</body>
</html>