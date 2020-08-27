# simple-clock-hec

简易闹钟实现

<h1>html文件</h1>
  <!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <link href="./style.css" rel="stylesheet">
  <title>简易时钟-hec</title>
</head>
<body>
  <div class="clock">
    <div class="hour">
      <div class="hr" id='hr'></div>
    </div>
    <div class="min">
      <div class="mn" id='mn'></div>
    </div>
    <div class="sec">
      <div class="sc" id='sc'></div>
    </div>
  </div>
</body>
<script>
  // 获取元素
  const deg = 6
  const hr = document.querySelector('#hr')
  const mn = document.querySelector('#mn')
  const sc = document.querySelector('#sc')
  
  // 开启时钟定时
  setInterval(() => {
    let day = new Date()
    let hh = day.getHours() * 30 // 时h  一圈360 度，有12格，每格 360/12 = 30
    let mm = day.getMinutes() * deg // 分m  一圈360 度， 有60格，每格 6 度
    let ss = day.getSeconds() * deg // 秒s  一圈360 度， 有60格，每格 6 度
    hr.style.transform = `rotateZ(${(hh) + (mm/12)}deg)` // 时的刻度等于时针走过的度数加上分针的偏移量
    mn.style.transform = `rotate(${mm}deg)`
    sc.style.transform = `rotate(${ss}deg)`
  })

</script>
</html>




css文件
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: '微软雅黑', sans-serif;
}
body{
  display: flex;
  align-items: center;
  justify-content: center;
  min-height: 100vh;
  background: skyblue;
}

.clock{  /*表盘外圈样式 + 添加表盘img*/
  width: 350px;
  height: 350px;
  display: flex;
  justify-content: center;
  align-items: center;
  background: url(clock.png);
  background-size: cover;
  border-radius: 50%;
  border: 3px solid #091921;
  box-shadow: 0 -15px 15px rgba(255, 255, 255, 0.05),
              inset 0 -15px 15px rgba(255, 255, 255, 0.05),
              0 15px 15px rgba(0, 0, 0, 0.05),
              inset 0 15px 15px rgba(0, 0, 0, 0.05);
}

.clock::before{ /*表盘中间点设置*/
  content: '';
  position: absolute;
  width: 15px;
  height: 15px;
  background: #fff;
  border-radius: 50%;
  z-index: 10000;
}

.clock .hour, 
.clock .min, 
.clock .sec {   /* 时分秒  绝对定位*/
  position: absolute;
}

.clock .hour, .hr{ /*时针长宽样式*/
  width: 160px;
  height: 160px;
}
.clock .min, .mn{  /*分针长宽样式*/
  width: 190px;
  height: 190px;
}
.clock .sec, .sc{  /*秒针长宽样式*/
  width: 230px;
  height: 230px;
}

.hr, .mn, .sc{ /*时分秒 同时设置*/
  display: flex;
  justify-content: center;
  position: absolute;
  border-radius: 50%;
}

.hr::before{ /*分针设置*/
  content: '';
  position: absolute;
  width: 8px;
  height: 80px;
  background: #ff105e;
  z-index: 10;
  border-radius: 6px 6px 0 0;
}

.mn::before{ /*时针设置*/
  content: '';
  position: absolute;
  width: 4px;
  height: 90px;
  background: #fff;
  z-index: 11;
  border-radius: 6px 6px 0 0;
}
.sc::before{ /*秒针设置*/
  content: '';
  position: absolute;
  width: 2px;
  height: 150px;
  background: #fff;
  z-index: 12;
  border-radius: 6px 6px 0 0;
}



