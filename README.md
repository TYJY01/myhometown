# myhometown
<!DOCTYPE html>
<html>
<head>
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
    <meta name="viewport" content="initial-scale=1.0, user-scalable=no" />
    <style type="text/css">
        body, html, #allmap {
            width: 100%;
            height: 100%;
            overflow: hidden;
            margin: 0;
            font-family: "微软雅黑";
        }
    </style>
    <script type="text/javascript" src="//api.map.baidu.com/api?type=webgl&v=1.0&ak=GAx6DkvjPf1zXCjGDDcGhjN4rCDYIwml"></script>
    <title>计网作业 唐渝 3190104975</title>
</head>
<body>
    <div id="allmap"></div>
</body>
</html>
<script type="text/javascript">

    // 百度地图API功能
    var map = new BMapGL.Map("allmap");    // 创建Map实例
    map.centerAndZoom(new BMapGL.Point(105.33, 30.10), 11);  // 初始化地图,设置中心点坐标和地图级别
    map.enableScrollWheelZoom(true);     //开启鼠标滚轮缩放

    var point = new BMapGL.Point(111.577, 25.190);
    var marker = new BMapGL.Marker(point);  // 创建标注
    map.addOverlay(marker);              // 将标注添加到地图中

    var sContent =
"<h4 style='margin:0 0 5px 0;padding:0.2em 0'>四川省安岳县</h4>" +
"< img style='float:right;margin:4px' id='imgDemo' src='https://baike.baidu.com/pic/%E5%AE%89%E5%B2%B3%E5%8E%BF/1042174/1/fcfaaf51f3deb48f9056ff4afb1f3a292df57862?fr=lemma&ct=single#aid=1592917495&pic=faf2b2119313b07e24c0089c07d7912397dd8c21' width='200' height='104' title='安岳柠檬基地'/>" +
"<p style='margin:0;line-height:1.5;font-size:13px;text-indent:2em'>安岳县，隶属四川省资阳市，位于四川盆地中部，成渝经济区腹心和成都、重庆的直线中点，誉“成渝之心”；地跨东经104°56′51″～105°45′14″，北纬29°40′32″～30°18′53″之间</p >" + "<a style='color:#87CEFA;text-decoration:none;' href=' '>更多信息见百度百科</ a>"
    "</div>";

    var infoWindow = new BMapGL.InfoWindow(sContent);     // marker添加点击事件
    marker.addEventListener('click', function () {
        this.openInfoWindow(infoWindow);
        // 图片加载完毕重绘infoWindow
        document.getElementById('imgDemo').onload = function () {
            infoWindow.redraw(); // 防止在网速较慢时生成的信息框高度比图片总高度小，导致图片部分被隐藏
        };
    });
</script>

