# 😄 人员卡车安全通道监测

## 👍 事前准备

1. yolov5 模型的预加载
2. 素材的准备
3. 需求分析

## 😕 需求分析

1. 需要将视频分成两块区域，一块存储卡车不能出现的地方，一块存储人不能出现的地方，方法类似于闯入告警
2. 人出现在不能出现的地方，或者车出现在不能出现的地方，触发图片存储，推送给告警后端
3. 需要分析人物是否逆向行走，需要进行跟踪算法，这个放在实现了两块区域告警成功后，再迁移模块

## 🚀️ 需求实现

1. 需要定义两块蒙版，mask_person：一块存储卡车不能经过的地方，mask_truck：一块存储人不能出现的地方
2. 拿到卡车和人的坐标点
3. 根据坐标点绘制封闭矩形
4. 卡车与moban1进行与操作，人物与moban2进行与操作
5. 得到结果

### cv2模块使用

* ```
  polylines(frame, [pts], True. (0,0,255))  # 绘制以pts为点坐标的矩形
  
  fillPoy(frame, [pts], (255, 255, 255))  # 绘制以pts的封闭矩形填充
  
  putText(frame, " Message txt", (x, y),  cv2.FONT_HERSHEY_COMPLEX_SMALL, 1, (55, 255, 155), 1)  # 在xy坐标以字体cv2...SMALL 绘制文字 Message txt
  ```



## 插件架构

在plugin文件夹中有相关插件，可以进行调整