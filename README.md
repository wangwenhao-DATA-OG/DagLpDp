# DagLpDp
用动态规划求解有向无环图的最长路径问题

# 安装
pip install DagLpDp

# 功能
1.支持多起点和多终点
2.可计算到任意节点的最长路径和路径值
3.可计算到每个终点的最长路径和路径值
4.可计算所有路径中的最长路径和路径值
5.采用非递归方式求解，提升运行效率

# 示例
```
from DP import DAGLP
def __print(daglp):
    print('起点（无入度）:',daglp.starts) 
    print('终点（无出度）:',daglp.ends) 
    print('到任意节点的最长路径:',daglp.nodePV)
    print('到每个终点的最长路径:',[v for k,v in daglp.nodePV.items() if k in daglp.ends])
    max_value = 0
    for k,v in daglp.nodePV.items():
        if v[1] > max_value:
            longest_path_in_all_node = v[0]
            max_value = v[1]        
    print('最长路径:%s,最长路径值:%f'%(longest_path_in_all_node,max_value))
       
def test_single_start_and_end():
    graph = {}
    graph[(1,2)] = 2
    graph[(1,3)] = 10
    graph[(2,4)] = 5
    graph[(2,5)] = 12
    graph[(3,4)] = 2
    graph[(4,6)] = 2
    graph[(5,6)] = 1
    return DAGLP(graph) 
    
def test_multi_start_and_end():
    graph = {}
    graph[(0,2)] = 4
    graph[(1,2)] = 2
    graph[(1,3)] = 10
    graph[(2,4)] = 5
    graph[(2,5)] = 12
    graph[(3,4)] = 2
    graph[(4,6)] = 2
    graph[(4,7)] = 2
    graph[(5,6)] = 1
    return DAGLP(graph)   

if __name__ == '__main__':
    daglp_single = test_single_start_and_end()
    __print(daglp_single)
       
    daglp_multi = test_multi_start_and_end()
    __print(daglp_multi)
```
