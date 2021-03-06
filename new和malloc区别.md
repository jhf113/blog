# new和malloc区别

* new为关键字，malloc为库函数

* new申请空间时候无需只等内存的大小，编译器会自动计算，而malloc需要计算出的给出所需的内存空间大小

*  new分配成功返回的是对象类型指针，与对象严格匹配，而无需类型转换，故new是符合类型安全行操作符，malloc返回的是void*

*  new可以重载，malloc不可以

*  内存区域：new分配的是自由存储区，malloc分配的是堆

*  想要申请失败后得到空指针用nothrow new 来申请空间

* new/delete是C++运算符，需要编译器支持。Malloc/free是库函数，需要头文件支持

* new操作符内存分配成功时，返回的对象是指针，类型严格与对象匹配，无需进行类型转换，故new是符合类型安全性的操作符，而malloc内存分配成功时则返回的是void *，需要通过强转将void * 转换到我们需要的类型。

* new内存分配失败时会抛出bac_alloc异常，malloc分配内存失败时返回NULL

* new会先调用operator new函数，申请足够的内存（通常底层用malloc实现）然后调用类型的构造函数，初始化成员变量，最后返回自定义类型指针。delete先调用析构函数，然后调用operator delete函数释放内存(通常底层使用free）。Malloc/free是库函数，只能申请和释放内存，无法强制要求自定义类型对象构造和析构工作。

* C++允许重载new/delete操作符，特别的，new就不需要为对象分配内存，而是指定一个地址作为内存起始区域，new在这段内存上为对象调用构造函数完成初始化工作，并且返回此地址，而malloc不允许重载。

* new操作符从自由存储区（free store）上为对象动态分配内存空间，而malloc函数从堆上动态分配内存。自由存储区是C++基于new操作符的一个抽象概念，凡是通过new操作符进行内存申请，该内存即为自由存储区，而堆是操作系统中的术语，是操作系统所维护的一块特殊的内存，用于程序的内存动态分配。C语言使用malloc从堆上分配内存，使用free释放已经分配的内存，自由存储区不等于堆，如上所诉，new就可以不位于堆中。
