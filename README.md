# birthday.html
🎂黄米琪生日祝福｜11月14日。有蛋糕烛光、彩带动画、生日背景音乐，生日当天自动开启特效，点击页面播放音乐，送给黄米琪的生日小惊喜。<!DOCTYPE html>
<html lang="zh-CN">
<head>
<meta charset="UTF-8">
<title>🎂 祝黄米琪生日快乐</title>
<style>
*{margin:0;padding:0;box-sizing:border-box;font-family:"Microsoft YaHei",sans-serif}
body{
  min-height:100vh;
  background:linear-gradient(135deg,#ffd6e0,#fff7bc);
  display:flex;
  flex-direction:column;
  align-items:center;
  justify-content:center;
  overflow:hidden;
}
.cake-box{
  position:relative;
  margin-bottom:30px;
}
.cake{
  width:220px;height:160px;
  background:#ffb6c1;
  border-radius:10px 10px 0 0;
  position:relative;
}
.cake::before{
  content:"";
  position:absolute;
  width:260px;height:40px;
  background:#f88fab;
  bottom:-10px;
  left:-20px;
  border-radius:8px;
}
.candle{
  width:12px;height:45px;
  background:#fff;
  position:absolute;
  top:-45px;
  left:50%;
  transform:translateX(-50%);
  border-radius:3px;
}
.flame{
  width:14px;height:22px;
  background:linear-gradient(#ffdd00,#ff7722,#ff3322);
  border-radius:50% 50% 50% 50% / 60% 60% 40% 40%;
  position:absolute;
  top:-20px;
  left:50%;
  transform:translateX(-50%);
  animation:flicker 0.25s infinite alternate;
}
@keyframes flicker{
  0%{scale:1;opacity:0.9}
  100%{scale:1.15;opacity:1}
}
.text{
  font-size:36px;
  color:#c82453;
  font-weight:bold;
  text-align:center;
  margin:15px 0;
}
.sub-text{
  font-size:20px;
  color:#a03050;
  margin-bottom:20px;
}
.tip{
  color:#666;
  font-size:15px;
}
.confetti{
  position:fixed;
  width:10px;height:10px;
  border-radius:50%;
  animation:fall 4s linear infinite;
}
@keyframes fall{
  0%{top:-10px;}
  100%{top:100vh;}
}
</style>
</head>
<body>
<div class="cake-box">
  <div class="cake">
    <div class="candle">
      <div class="flame"></div>
    </div>
  </div>
</div>
<div class="text">🎂 祝黄米琪生日快乐！</div>
<div class="sub-text">11月14日 · 生日快乐呀✨</div>
<div class="tip" id="tip">等待日期校验中...</div>

<audio id="birthdayAudio" loop>
  <source src="https://www.soundhelix.com/examples/mp3/SoundHelix-Song-1.mp3" type="audio/mpeg">


<script>
// 目标生日：11月14日
const targetMonth = 11;
const targetDay = 14;
const today = new Date();
const m = today.getMonth() + 1;
const d = today.getDate();

const audio = document.getElementById("birthdayAudio");
const tipDom = document.getElementById("tip");

if(m === targetMonth && d === targetDay){
  tipDom.innerText = "🎉 今天是生日！自动播放生日歌~";
  audio.play().catch(e=>{tipDom.innerText="点击页面任意位置播放音乐";});
  // 彩带
  function addConfetti(){
    const div = document.createElement("div");
    div.className="confetti";
    div.style.left = Math.random()*100 + "%";
    div.style.backgroundColor = ["#ff5588","#ffdd44","#44ddff","#88ff88","#bb77ff"][Math.floor(Math.random()*5)];
    document.body.appendChild(div);
    setTimeout(()=>div.remove(),4000);
  }
  setInterval(addConfetti,180);
}else{
  tipDom.innerText = `还没到生日哦，生日是 ${targetMonth}月${targetDay}日`;
}
document.onclick = ()=>audio.play();
</script>
</body>
</html>

