> Короче, я закоммитил недокументированную возможность строить проивзольные карты меток. Если хотите попробовать, вам нужно спулить новую версию clever и пересобрать пакеты clever и aruco\_pose.

Нужно поставить у aruco\_pose &lt;param name="type" value="custom"/&gt;

Маркеры задаются так:

&lt;rosparam param="markers"&gt;

'0': 0.33 0 0 0 0 0 0

'1': 0.2 0 1 0 0 0 0

&lt;/rosparam&gt;

```
‘id’: size x y z yaw pitch roll (x, y, z указывают на центр маркера)
```

yaw pitch и roll игнорируются

![](/assets/photo5291837177317140520.jpg)

![](/assets/photo5255821183595686225.jpg)

