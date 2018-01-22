# 设计

buffer_t 和 parser 紧密耦合，与其他部件解耦，可以进行模拟测试。request_t包含这两者，让两者耦合

为了性能，抽象出ssstr_t类型作为parser_archive成员，避免了内存的拷贝


# 测试

写了简单的单元测试，在开发过程中多次修改结构，有单元测试对于重构帮助很大

并发的瓶颈不在于内存的malloc和free（有内存池更好），如果可以利用HTTP/1.1中keep-alive功能，加入Content-Length或者Chunked可以极大增加并发数.