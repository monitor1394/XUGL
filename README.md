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

一款孵化自[XCharts](https://github.com/monitor1394/unity-ugui-XCharts)的`UGUI`图形库，可绘制点、线、面等其他常见的图形。通过重载 `UGUI` 的 `OnPopulateMesh()` 重新填充顶点缓冲区来实现绘制自定义图形效果。

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

## 日志

[更新日志](https://github.com/monitor1394/XUGL/blob/master/CHANGELOG.md)  

## Licenses

[MIT License](https://github.com/monitor1394/XUGL/blob/master/LICENSE.md)
