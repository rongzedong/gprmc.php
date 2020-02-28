### gprmc.php
=========

#### GPRMC报文解析

  采集回来的speed单位是节，即 海里每小时。 解析后的speed已经转换为公里每小时 km/h 如果需要海里每小时这个单位可以通过 speed_knot 参数获取。

#### GPRMC解析

#### 标准GPRMC报文:


    0      1          2           4            6      8      9      10              13
    |      |          |           |            |      |      |      |    |
    $GPRMC,161229.487,A,3723.2475,N,12158.3416,W,0.13,309.62,120598,     ,         *10
                        |           |            |                    |
                        3           5            7                    11


    0:  GPRMC报头
    1:  标准定位时间  hhmmss.sss
    2:  状态          A可用, V不可用
    3:  纬度          ddmm.mmmm
    4:  南北半球      N/S
    5:  经度          dddmm.mmmm
    6:  东西半球      E/W
    7:  对地速度      节 0.0 ~ 1851.8
    8:  对地方向      度 000.0 ~ 359.9 (以正北为参考基准)
    9:  日期          ddmmyy
    10: 磁偏角        ?
    11: 
    12:   only new version .
    13: 校验码

本地报文:
 
    $GPRMC,081412.00,A,3147.95419,N,11709.62783,E,0.000,347.53,180113,,,A*6B


 #### Demo:

    $rmc = new GPRMC('$GPRMC,161229.487,A,3723.2475,N,12158.3416,W,0.13,309.62,120598, ,*10<CR><LF>');
    print_r($rmc->RMC);
    echo "STATUS: " . $rmc->status;
    echo "DATE: " . $rmc->datetime;
    echo "LAT: " . $rmc->lat;
    echo "LONG: " . $rmc->long;
    echo "SPEED: " . $rmc->speed;
    echo "DIRECT: " . $rmc->direction;


