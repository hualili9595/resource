
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>弹幕测试</title>
    <style>
        *{margin: 0;padding: 0;}
        html,body{
            width: 100%;
            height: 100%;

        }
        .box{
            position: absolute;
            left: 50%;
            top:50%;
            width: 100%;
            height: 500px;
            background: url("111.jpg")  no-repeat;
            background-size: cover;
            z-index: 1;
            transform: translate(-50%,-50%);
        }
        .tipbox{
            width: 100%;
            height: 100%;
            position: absolute;
            top:0;
            left: 0;
            background: rgba(0,0,0,.1);
            z-index: 2;
        }
        .tipbox>p{
            width: 100%;
            height: 40px;
            line-height: 40px;
            position: relative;
        }
        .tipbox>p>span{
            position: absolute;
            right: 0;
            animation: danmu 10s linear 0s infinite;
            font-size: 16px;
            opacity: 0;
        }

        @keyframes danmu {
            from {
                right: 0;
                transform: translateX(0);
                opacity:1;
            }
            to {
                right: 100%;
                transform: translateX(-100%);
                opacity: 1;
            }
        }
    </style>
</head>
<body>
    <div class="box">
        <div>我是视频</div>
        <div class="tipbox">
            <!--<p><span>我是弹幕11111</span></p>-->
            <!--<p><span>我是弹幕22222</span></p>-->
            <!--<p><span>我是弹幕33333</span></p>-->
            <!--<p><span>我是弹幕44444</span></p>-->

        </div>
    </div>

</body>
</html>
<script src="jquery-3.2.0.min.js"></script>
<script>
    var arr = ['弹幕1111','我是弹幕22222','3333333','弹幕1111','弹幕2222','3333333'];
    $(arr).each(function (i,v) {

        $('.tipbox').append('<p><span>'+v+'</span></p>');
       var row = Math.floor($('.tipbox').height()/40);
        if( $('.tipbox>p').length >row){
            console.log('停止创建p标签')
        }
        $('.tipbox>p>span').eq(i).css('animation', 'danmu 10s linear '+i+'s infinite');
        $('.tipbox>p>span').eq(i).hover(
            function () {
                console.log($(this));
                $(this).css('animation-play-state', 'paused ');
            }
            ,
            function () {
                $(this).css('animation-play-state', 'running');
            }
        );


$('.tipbox>p>span').click(function(){
    $(this).css('color','pink')
})
    })
</script>
