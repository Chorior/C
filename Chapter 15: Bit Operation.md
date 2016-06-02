# Bit Operation
---
1. 4个位运算符用于整数，包括char: 取反(~)，位与(&)，位或(|)，位异或(^)；
2. 移位运算符：
    * 左移(<<): 丢弃移出左侧操作数末端的位，空出的位用0填充；`var << 3;`
    * 右移(>>): 丢弃移出右侧操作数末端的位，对unsigned类型，用0填充左端空出的位，对signed类型，结果依赖于机器；
3. 位字段难以移植；
4. unsigned int是位字段结构的基本布局单元；
5. 下面结构使用未命名字段将与填充相关的信息放在一个字节，与边框有关的字节放在第二个字节(使用时确保值没有超出字段的容量)：
    <pre>
    typedef unsigned int U4;
    struct box_props
    {
        U4 opaque       :1;
        U4 fill_color   :3;
        U4              :4;
        U4 show_border  :1;
        U4 border_color :3;
        U4 border_style :2;
        U4              :2;
    }
    </pre>   
