# C++动态内存
-----


##内存分类
* 静态内存：局部static对象，类static数据成员，全局变量
* 栈内存：函数内的非static对象
* 堆内存：储存动态分配的对象
* 总结：
    * 静态和栈内存由编译器自动创建和销毁
    * 栈对象在程序块运行时才存在
    * static对象在使用之前分配，程序结束时销毁
    
##智能指针
* ###shared_ptr
    * 智能指针也是模板

            shared_ptr<string> p1;

    * 安全的初始化分配 —— mark_shared
    
            shared_ptr<int> p3 = mark_shared<int>(42);
            auto p6 = make_shared<vector<string>>();

    * 拷贝和赋值
    
            auto r = make_shared<int>(42); //r指向的int只有一个引用者
            r = q;  //给r赋值，令它指向另一个地址
                    //递增q指向的对象的引用计数
                    //递减r原来指向的对象的引用计数
                    //r原来指向的对象已没有引用者，会自动释放

    * 自动销毁所管理的对象
        * 在析构函数中递减他所指向的对象的引用计数，引用计数为0时，则会销毁对象并释放内存
* ###shared_ptr和new结合使用
    * 直接初始化形式，不能进行赋值初始化
    
            shared_ptr<int> p2（new int（1024））;

* ###unique_ptr
    * 只能有一个unique_ptr指向一个指定的对象
    * 必须用直接初始化的形式
    
            unique_ptr<int> p2（new int（42））；
            
    * 不支持普通的拷贝和赋值

* ###weak_ptr
    * 指向一个shared_ptr管理的对象，不会改变其引用计数
    * 检查shared_ptr的有效性
    
            if(shared_ptr<int> np = wp.lock())
            所指的对象有效存在才执行条件中的内容
                
##动态数组
* ###初始化动态分配对象的数组

        int *p1 = new int[10]();
        int *p2 = new int[10]{0,1,2,3,4,5,6,7,8,9};
        
* ###释放动态数组

        delete []p1;




------

Copyright 2015 WangLin
<!-- create time: 2015-04-05 10:15:37  -->
