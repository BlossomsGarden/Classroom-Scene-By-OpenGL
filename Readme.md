# Wandering around Classroom! 👋

## 💿 简介

本项目是2023年秋计算机图形学课程期末大作业，使用OpenGL实现的简单3D教室场景。

<img src="https://github.com/user-attachments/assets/4ecbe1f3-5b66-484a-a49d-7208e67e0af5" width="600px">

纹理贴图使用顶点着色器+片元着色器加载

场景光源使用 Blinn-Phong Shader 进行渲染

窗帘飘动基于顶点着色器动画实现，由水平方向的正弦波动函数组成。垂直方向自下而上波动幅度递减，营造出飘动的效果。

樱花飘落效果基于粒子系统实现。设定生存时间后，让它们从特定空间呈抛物线方式自旋进入窗户，触碰到地板时清除角度和速度。

阴影效果采用PCF实现。通过 9*9 PCF片段采样过滤得到阴影（但由于场景中包含动态元素，需要在每个渲染循环中生成新的DepthMap，开销较大，
因此选择只生成室外光源产生的阴影。


## 👨‍💻 项目架构

src：主要代码及头文件。test.cpp 为项目启动文件、main()函数所在地。

res：建模obj文件、物体纹理、着色器代码存放处。

vendor：库文件提供者。

其他根目录下的 dll 由动态编译产生，用以支持点击 final.exe 直接运行。


## 🔧 运行

本机存在 OpenGL 相关库文件及 dll 文件后，双击根目录下的 final.exe 可以直接运行

系统：Windows 10 + VS2022

依赖：glm库提供的向量、矩阵的数据结构与运算函数；使用GLFW创建窗口、处理键盘输入事件；使用GLEW获取OpenGL的库函数；使用assimp 用以加载obj模型，obj模型使用 3Ds Max 制作。

交互：W/A/S/D可以移动视角；Shift 键下降； 空格键上升； Esc 键退出


## 🍓 其他

unsigned int 在不同的编译器和不同平台下可能具有不同的值，比如OpenGL中就没有规定 GLuint 类型大小和 unsigned int 相同。

