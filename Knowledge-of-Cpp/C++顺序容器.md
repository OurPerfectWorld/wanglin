# C++顺序容器

<!-- create time: 2015-04-04 11:09:53  -->
----

##顺序容器类型
* ###vector

        可变大小的数组
        支持快速随机访问
        在尾部之外的位置插入或删除元素操作慢 

* ###deque

        双端队列
        支持快速随机访问
        在头尾插入或删除的速度快

* ###list

        双向链表
        只支持双向顺序访问，无法随机访问
        在任何位置进行插入或删除的操作快

* ###forward_list

        单向链表
        只支持单向顺序访问
        任意位置进行插入或删除的操作快

* ###array

        固定大小的数组
        支持快速随机访问
        不能添加或删除元素

* ###string

        与vector容器相似，但用于保存字符
        随机访问快
        在尾部插入或删除速度快

---

##如何选择容器
* ###程序有很多小元素，内存开销大时，不选择list或forward_list
* ###程序需要随机访问，应用vector或deque
* ###程序需要在中间位置插入或删除数据，应用list或forward_list
* ###程序需要在头尾位置插入或删除数据，但不会在中间位置进行插入或删除，则使用deque
* ###程序需要在中间位置插入并可以随机访问
    * ####用vector在尾部进行插入元素，再用sort函数进行排序即可
    * ####插入过程可以用list做过渡的保存，再拷贝到vector

##容器中的迭代器
* ###begin：容器中的第一个元素
* ###end：容器中尾元素最后的位置
* ###begin和end相等，则容器为空；不等则至少有一个元素
* ###可以对begin递增若干次，使得begin＝end

        while(begin!=end){
            *begin = val;
            ++begin;
        }
        
##容器中的其他操作
* ###定义和初始化
* ###赋值与swap
    * ####assign用参数指定的元素替换左边容器中所有元素，仅限顺序容器（array除外）
    * ####swap交换两个相同容器的内容，元素本事不交换，两个容器的内部数据结构交换
* ###容器大小的操作
    * ####成员函数size，返回元素的数目，单向链表forward_list不支持
    * ####empty为0返回true，否则返回false
    * ####max_size返回能容纳的元素数最大值
    * ####capacity：容器的预留空间大小
* ###容器的添加操作
    * ####push_back：将元素追加到container的尾部，array和forward_list不支持
    * ####push_front：链表，双向链表，双端队列支持，将元素插入到头部
    * ####insert：将元素插入到指定位置之前
    * ####emplace：在容器中直接构造元素，包含_front,_back
* ###容器的删除操作
    * ####pop_back：删除尾元素，单向链表不支持
    * ####pop_front：删除首元素，vector和string不支持
    * ####erase：删除指定的元素 or 指定范围内的元素
    * ####clear：删除全部元素
* ###容器的访问操作
    * ####at和下标操作，只用于vector，string，deque，array
    * ####back，不用于forward_list单向列表
    * ####front，back：对应容器中的第一和最后一个元素，访问前保证容器非空
    * ####begin，end：对应容器中第一个和最后一个元素之后的位置（不存在的）
* ###容器的修改大小
    * ####resize：修改容器大小，array数组不适用

##容器的适配器
* ###容器顺序的适配器：stack，queue，priority_queue
* ###使容器的行为看起来像不同类型的容器，如
    * ####stack接受vector，使vector像stack一样可以进行操作
* ###栈适配器stack
    * ####基于deque实现，也可以在list或vector上实现
    * ####pop，push，top，emplace
* ###先进先出的队列适配器queue
    * ####基于deque实现
    * ####pop，front，back，top，push，emplace
* ###根据优先级排列的队列适配器priority_queue
    * ####基于vector实现



------

Copyright 2015 WangLin
<!-- create time: 2015-01-24 17:36:47  -->

