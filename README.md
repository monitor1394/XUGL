<p align="center">
  <a href="">
    <img src="" alt="" width="" height="">
  </a>
</p>
<h2 align="center">XUGL</h3>
<p align="center">
  UGUI Graphics Library for Unity.
  <br>
  UGUI 图形库。
</p>
<p align="center">
  <a href="https://github.com/monitor1394/XUGL/blob/master/LICENSE">
    <img src="https://img.shields.io/github/license/monitor1394/XUGL">
  </a>
  <a href="">
    <img src="https://img.shields.io/badge/Unity Version-5.6+-green">
  </a>
</p>

`XUGL`是一款基于UGUI实现的图形库。图表插件[XCharts](https://github.com/monitor1394/unity-ugui-XCharts)正是使用该图形库来实现图表的绘制。`XUGL`通过重载 `UGUI` 的 `OnPopulateMesh()` 重新填充顶点缓冲区来实现绘制自定义图形效果，可绘制点、线、箭头、三角形、正方形、圆形、扇形、环形、椭圆形等其他常见的图形，并支持绘制`SVG`矢量图。

## API

| | |
| --| --|
| UGL.DrawArrow( ) | 画箭头 |
| UGL.DrawLine( ) | 画直线 |
| UGL.DrawDashLine( ) | 画虚线 |
| UGL.DrawDotLine( ) | 画点线 |
| UGL.DrawDashDotLine( ) | 画点划线 |
| UGL.DrawDashDotDotLine( ) | 画双点划线 |
| UGL.DrawZebraLine( ) | 画斑马线 |
| UGL.DrawDiamond( ) | 画菱形（钻石形状） |
| UGL.DrawSquare( ) | 画正方形 |
| UGL.DrawRectangle( ) | 画带长方形 |
| UGL.DrawQuadrilateral( ) | 画任意的四边形 |
| UGL.DrawRoundRectangle( ) | 画圆角矩形 |
| UGL.DrawBorder( ) | 画边框 |
| UGL.DrawTriangle( ) | 画三角形 |
| UGL.DrawCricle( ) | 画圆 |
| UGL.DrawEmptyCricle( ) | 画空心圆 |
| UGL.DrawSector( ) | 画扇形 |
| UGL.DrawRoundCap( ) | 画圆帽 |
| UGL.DrawDoughnut( ) | 画圆环 |
| UGL.DrawCurves( ) | 画贝塞尔曲线 |
| UGL.DrawEllipse( ) | 画椭圆 |
| UGL.DrawEmptyDiamond( ) | 画空心菱形（空心钻石形状） |
| UGL.DrawEmptyTriangle( ) | 画空心三角形 |
| UGL.DrawPlus( ) | 画`+号` |
| UGL.DrawMinus( ) | 画`+号` |

## 使用

通过源码或`Package Manager`的方式导入`XUGL`。  
自定义类继承自`UGUI`的`Graphic`，或相关的可重载 `OnPopulateMesh()` 的类。

  ``` c#
  public class UGLExample : MaskableGraphic
  {
  }
  ```

重载 `OnPopulateMesh()`， 用 `XUGL` 重新填充 `UGUI` 的顶点缓冲区数据。

  ``` c#
  protected override void OnPopulateMesh(VertexHelper vh)
  {
      Vector3 sp, cp, ep;
      vh.Clear();

      //背景边框
      UGL.DrawSquare(vh, m_Center, m_Width / 2, m_BackgroundColor);
      UGL.DrawBorder(vh, m_Center, m_Width, m_Height, 10, Color.green, 0, m_BorderRadius);

      //点
      UGL.DrawCricle(vh, m_LeftTopPos + new Vector3(20, -20), 10, m_DrawColor);

      //直线
      sp = new Vector3(m_LeftTopPos.x + 50, m_LeftTopPos.y - 20);
      ep = new Vector3(m_LeftTopPos.x + 250, m_LeftTopPos.y - 20);
      UGL.DrawLine(vh, sp, ep, 3, m_DrawColor);

      //3点确定的折线
      sp = new Vector3(m_LeftTopPos.x + 20, m_LeftTopPos.y - 100);
      cp = new Vector3(m_LeftTopPos.x + 200, m_LeftTopPos.y - 40);
      ep = new Vector3(m_LeftTopPos.x + 250, m_LeftTopPos.y - 80);
      UGL.DrawLine(vh, sp, cp, ep, 5, m_DrawColor);
  }
  ```

完整代码请查阅`Examples`：`UGLExample.cs`

## 更新日志

* (2022.12.28) 优化扇形和环形的带边框绘制
* (2021.11.01) 增加绘制椭圆支持
* (2021.11.01) 优化大部分绘图接口
* (2021.09.12) 增加绘制对称圆角支持
* (2021.09.12) 增加绘制渐变线段支持
* (2021.08.02) 增加斑马线、点线和点划线的渐变支持
* (2021.04.26) 增加渐变边框支持
* (2021.04.24) 首次提交

## Licenses

[MIT License](https://github.com/monitor1394/XUGL/blob/master/LICENSE.md)
