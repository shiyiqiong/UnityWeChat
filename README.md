# Unity微信小游戏优化
**WASM（网络程序集）优化：**
- 优化方向：提高加载速度，减少内存占用。
- 优化原理：
  - 编译器将C++代码编译为，已函数为单位的二进制指令集。
  - 如果包含的函数越少，包体越小，运行编译加载速度越快，占用内存越低。
- 优化方法：
  - 去掉冗余重复功能代码。 
  - 移除非WebGL平台下代码。
  - 删除没有有用到包。
  - 启用代码剥离；
  - 避免装箱，拆箱；
  - 尽量不使用反射，避免代码剥离出现异常。 
***
**内存优化：**
- 资源下载导致内存升高：
  - 资源并行下载，可以提高加载速度，但同时也会增加内存占用；
  - 资源按排序下载，可以降低内存占用，但会降低加载速度。
  - 根据实际情况，权衡内存和加载效率。
- 避免使用Resource（资源）文件夹：
  - 资源文件资源会打包进，webgl数据包里面；
  - 这部分数据，在游戏启动后就需要加载；
  - 并且会常驻内存。
- lua内存优化：
  - 尽量减少C#和lua绑定类型；去掉没有在lua访问到的类型。
- 渲染方面：
  - 降低渲染过程中的渲染目标分辨率，已经最终显示分辨率
- 资源优化：
  - 避免一份资源在多个AB包中有多份副本，导致加载时在内存有多份相同数据。 
  - 纹理压缩格式：ASTC（自适应可伸缩纹理压缩）。
  - 音频优化：
    - 双声道设置为单声道。
    - 音效：设置为加载的时候解压；
    - 背景音乐：内存保持压缩状态，播放是解压。 
***
**性能优化**
