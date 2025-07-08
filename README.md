# 题库数据文件说明

## 文件结构

```
data/
├── index.json          # 索引文件，包含所有分类信息
├── backend.json        # 后端题目数据
├── frontend.json       # 前端题目数据
├── middleware.json     # 中间件题目数据
├── java.json          # Java基础题目数据
├── cpp.json           # C++ STL题目数据
├── python.json        # Python题目数据
├── go.json            # Go题目数据
├── database.json      # 数据库题目数据
├── git.json           # Git题目数据
└── README.md          # 说明文档
```

## 数据格式

每个JSON文件包含以下结构：

```json
{
  "version": "1.0.0",
  "lastUpdate": "2024-01-15",
  "category": "分类名称",
  "topics": [
    {
      "id": "topic-id",
      "name": "专题名称",
      "questions": [
        {
          "id": 1,
          "title": "题目内容",
          "answer": "详细答案"
        }
      ]
    }
  ]
}
```

## 分类说明

### 1. 后端 (backend.json)
- **题目数量**: 25题
- **专题**: 高并发、分布式系统、微服务、缓存、安全与监控
- **内容**: 系统设计、架构模式、性能优化等

### 2. 前端 (frontend.json)
- **题目数量**: 19题
- **专题**: HTML/CSS、JavaScript、框架、性能优化、安全与测试
- **内容**: 前端技术栈、框架原理、性能优化等

### 3. 中间件 (middleware.json)
- **题目数量**: 11题
- **专题**: 消息队列、Nginx、ZooKeeper、分布式事务
- **内容**: 中间件原理、配置、使用场景等

### 4. Java基础 (java.json)
- **题目数量**: 13题
- **专题**: 基础语法、集合框架、多线程、JVM
- **内容**: Java核心概念、内存模型、并发编程等

### 5. C++ STL (cpp.json)
- **题目数量**: 5题
- **专题**: 容器、算法
- **内容**: STL容器原理、算法复杂度、使用场景等

### 6. Python (python.json)
- **题目数量**: 5题
- **专题**: 基础语法、高级特性
- **内容**: Python语法、装饰器、生成器等

### 7. Go (go.json)
- **题目数量**: 3题
- **专题**: 基础语法
- **内容**: Goroutine、Channel、接口等

### 8. 数据库 (database.json)
- **题目数量**: 7题
- **专题**: MySQL、Redis、ElasticSearch
- **内容**: 数据库原理、优化、使用等

### 9. Git (git.json)
- **题目数量**: 5题
- **专题**: 基础操作、高级操作
- **内容**: Git命令、工作流、版本管理等

## 使用方法

### 1. 本地使用
```javascript
// 加载题目数据
const fs = require('fs');
const questionData = JSON.parse(fs.readFileSync('./data/backend.json', 'utf8'));
```

### 2. 远程加载
```javascript
// 从远程服务器加载
async function loadQuestions(category) {
  const response = await fetch(`https://your-domain.com/data/${category}.json`);
  return await response.json();
}
```

### 3. 小程序中使用
```javascript
// 微信小程序中加载
wx.request({
  url: 'https://your-domain.com/data/backend.json',
  success: function(res) {
    const questions = res.data;
    // 处理题目数据
  }
});
```

## 更新维护

### 添加新题目
1. 在对应的JSON文件中添加新的question对象
2. 更新index.json中的questionCount
3. 更新lastUpdate时间戳

### 添加新分类
1. 创建新的JSON文件
2. 在index.json的categories数组中添加新分类信息
3. 更新totalQuestions数量

### 版本管理
- 每次更新时递增version号
- 在updateLog中添加更新记录
- 保持向后兼容性

## 注意事项

1. **数据格式**: 确保JSON格式正确，避免语法错误
2. **编码**: 使用UTF-8编码，支持中文内容
3. **大小**: 单个文件建议不超过1MB，便于网络传输
4. **缓存**: 建议实现本地缓存机制，提升加载速度
5. **备份**: 定期备份数据文件，防止数据丢失

## 扩展建议

1. **多语言支持**: 可以添加language字段支持多语言
2. **难度分级**: 可以添加difficulty字段标记题目难度
3. **标签系统**: 可以添加tags字段支持标签分类
4. **统计信息**: 可以添加统计字段记录使用情况
5. **评论系统**: 可以添加comments字段支持用户评论 