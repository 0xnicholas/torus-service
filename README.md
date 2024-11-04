# Torus Service
Torus Service提供用于与DeFi协议进行交互的统一API。Dapp与每个协议进行构建集成既耗时, 成本高昂且容易出错。Service Provider API允许开发人员构建一次并与所有协议集成。

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
