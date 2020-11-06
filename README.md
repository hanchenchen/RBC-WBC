# RBC-WBC
医学图像中的细胞识别

# 医学图像中的细胞识别

实现了医学图像中的红细胞与白细胞的识别

#### 工具🔧

Python、LableImg、Yolo v3

#### 步骤

1. ##### 下载已有红细胞标注的数据集 https://github.com/cosmicad/dataset.git

2. ##### 使用LableImg对白细胞进行标注 ![LableImg](LableImg.png)

3. 使用Yolo v3对模型进行训练

❌

  ```
  python train.py --data-cfg data/rbc.data --cfg cfg/yolov3-tiny.cfg --epochs 10
  ```

`cd yolov3`后，输入以下命令☑️

  ```
  python3 train.py --data data/rbc.data --cfg cfg/yolov3-tiny.cfg --epochs 40 --weights 'weights/yolov3-tiny.weights'
  ```

4. 使用samples文件夹中的样本进行测试

❌


  ```
  python3 detect.py --data-cfg data/rbc.data --cfg cfg/yolov3-tiny.cfg --weights weights/best.pt
  ```

☑️

  ```
  python3 detect.py --names data/rbc.names --source data/samples/ --cfg cfg/yolov3-tiny.cfg --weights weights/best.pt --conf-thres 0.055
  ```