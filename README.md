# Torus Service
Torus Service核心是其流动性服务层，并提供用于与区块链生态进行交互的统一API。Dapp与每个链/协议/dapp进行交互既耗时, 成本高昂且容易出错。`Service Provider` API允许开发人员构建一次并与所有产品集成。（灵感来源- MuleSoft from Salesforce）

**Key points**:
- Native transaction bundling.  允许用户在一个atomic transaction中执行多个交易
- DeFi actions. 提供多种DeFi操作, 可以batch以创建自定义工作流程。
- Best route execution. 考虑到gas, 滑点和收益, 给定的所需路径获取最佳路线(如果使用者对最佳路线不满意, 可通过solver network寻求solution).
> 以上都是全链流动性的部分
- Omni-chain liquidity. 全链流动性
- Standardization. 标准集成.
- Metadata. 提供与DeFi协议相关的元数据.

## Omni-chain Liquidity

总体三步
1. Infra Enhancement ()
2. Liquidity Aggregation
3. Integration

### Motivation
分散的流动性带来的差异:

1. 链太多，链上资金池都是独立存在，流动性分散，无法充分利用
2. 跨链交易的复杂操作和高费用
3. 价格差异，不同链上资产价格会有一些差异，影响交易体验
4. 流动性和交易随时变化，如交易失败或滑点过高

简化交易流程, 将摩擦成本降到最低, 用户只需提交交易意图请求，服务层会自动寻路执行交易, 通过将不同链的流动性整合为一个全链流动性池，显著提升交易效率和用户体验：

<ins>流动性深度，无缝跨链交易，价格一致性，预测和优化（最佳寻路-可能会用到AI），安全透明（合约）</ins>

**挑战**
- 准确性，任何错误或不完整都可能会导致交易失败或延迟
- 隐私保护，可能会暴露用户交易意图（同时也一样可能创造MEV机会）
- 执行效率，计算和验证的复杂度
- 安全性，交易传输和存储 (zk)

### 全链流动性服务层
包括以下核心组件：
- Cross-chain Liquidity Pool
- **Cross-chain Trasactions Protocol**
- Liquidity Bridge

简化步骤：
1. 


> 可选特性组件，AI优化；ZKP安全机制。



### 交易模式
用户定义其预期交易结果(outcome)，而协议则优化和管理通过节点的特定执行路径。这一模式旨在提高(跨链)流动性的利用效率。

在该交易模式中，用户只需signed一份意图(意图编码为`Li-JSON`)，表达他们对最终产出的预期。在此过程中交易协议的作用包括：
- 流动性评估和选择
- 路径优化和执行
- 安全保证

交易示例:


#### 交易拆分 (Transaction Split)
协议通过动态拆分和流动性聚合来优化交易执行，实现最低成本和最高流动性利用率。

**交易拆分算法**的目标是是将交易分配给多个流动性供应商，以尽量减少总fee，同时满足funding。

Input parameters:

Objective function:

Constraints:

算法步骤：

#### 流动性预测


### 协议节点



## API套件
> 首先要获得API key(Torus Account), API风格为REST

### Router API
DeFi聚合和订单路由.

- `GET/v1/route`
- `GET/v1/quote`

有3种路由策略选项:
- `router`: 通用router
- `delegate`: 以delegateCalls形式返回智能帐户的calldata
- `bagelwallet`: 返回calldata以部署bagel智能帐户, 并在同一交易中执行智能帐户内部的所有逻辑

> Bagel Wallet: 基于Torus平台的wallet组件:

### Bundler API
开发人员可以将多个DeFi操作打包到一个交易中。旨在简化操作和提高效率。

- `POST/v1/bundle`

### Metadata API
数据网关

- `GET /v1/tokens`
- `GET /v1/protocol`
- `GET /v1/networks`
- `GET /v1/actions`
- `GET /v1/standards`

Bagel Wallet:
- `GET /v1/wallet`
- `GET /v1/wallet/appprove`
- `GET /v1/wallet/balances`


## React Hooks
