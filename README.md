- 基本功能：读取数据和写⼊数据；⽀持多种数据结构；⽀持过期时间；⽀持服务端和客户端；⽀持磁盘空间回
收；⽀持单独存磁盘和内存磁盘双存两种模式
- 设计理念：基于bitcask模型，⽇志形式存储，磁盘中的⽇志⽂件本身作为数据库，内存中存储⽇志⽂件索
引。相⽐于redis这种内存数据库，稍微损失了⼀点性能⽽获得了数倍于内存的存储空间
- 写操作：增删改全部为在磁盘上新增⼀条记录，即全部为顺序写，不需要磁盘寻址，每个记录有固定的格式。
磁盘写完之后更新内存中的相关索引
- 读操作：在内存中通过 key 定位到⽬标数据的相关记录，从该记录中读取到实际数据在磁盘中的具体位置
