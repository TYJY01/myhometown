# myhometown
<html>
<head>
    <meta charset="UTF-8">
    <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
    <meta name="viewport" content="initial-scale=1.0, user-scalable=no" />
    <style type="text/css">
        body, html,#allmap {width: 100%;height: 100%;overflow: hidden;margin:0;font-family:"微软雅黑";}
        #allmap{width: 100%;height: 100%;margin:0;height: 300px}
    </style>
    <script type="text/javascript" src="http://api.map.baidu.com/api?v=1.0&ak=x93W9PhY34OtT003qS5BXpQCVdquLmHx"></script>
    <title>浏览器定位</title>
</head>
<body>
<div id="allmap"></div>
</body>
</html>
<script type="text/javascript">
    // 百度地图API功能
    var map = new BMap.Map("allmap");
    var point = new BMap.Point(105.33, 30.10);
    map.centerAndZoom(point,20);
 
    // 创建地址解析器实例
    var myGeo = new BMap.Geocoder();
    // 将地址解析结果显示在地图上,并调整地图视野
    myGeo.getPoint("深圳市福田区第一世界广场", function(point){
        if (point) {
            var opts = {type: BMAP_NAVIGATION_CONTROL_ZOOM}
            map.addControl(new BMap.NavigationControl(opts));//地图平移缩放控件，PC端默认位于地图左上方，它包含控制地图的平移和缩放的功能。移动端提供缩放控件，默认位于地图右下方。
            map.addControl(new BMap.OverviewMapControl()); //缩略地图控件，默认位于地图右下方，是一个可折叠的缩略地图。
            map.addControl(new BMap.MapTypeControl());//地图类型控件，默认位于地图右上方。
            map.centerAndZoom(point, 20);
            var marker =new BMap.Marker(point);
            map.addOverlay(marker);
            marker.setAnimation(BMAP_ANIMATION_BOUNCE); //跳动的动画
            var optss = {
                width : 240,     // 信息窗口宽度
                height: 70,     // 信息窗口高度
                title : "第一世界广场" , // 信息窗口标题
                enableMessage:true,//设置允许信息窗发送短息
            }
            var infoWindow = new BMap.InfoWindow("地址：深圳市福田区第一世界广场", optss);  // 创建信息窗口对象
            marker.addEventListener("click", function(){
                map.openInfoWindow(infoWindow,point); //开启信息窗口
            });
 
            setTimeout(function () {
                map.setZoom(20);
            },2000);
            map.enableScrollWheelZoom(true);
 
        }else{
            alert("您选择地址没有解析到结果!");
        }
    }, "安岳县");
 
</script>
<img src="园觉洞.png"/>
<a href="https://baike.baidu.com/item/%E5%9C%86%E8%A7%89%E6%B4%9E/13141?fr=aladdin">安岳县圆觉洞风景区</a>
</html>
