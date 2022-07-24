# 2021-iFLYTEK-LoanPredction-competition

## 赛题介绍

datawhale&科大讯飞举办的学习挑战赛————“车辆贷款违约预测挑战赛” Rank4 方案

[赛题链接](https://challenge.xfyun.cn/topic/info?type=car-loan&ch=dc-web-banner01)

给定某机构实际业务中的相关借款人信息，包含53个与客户相关的字段，其中`loan_default`字段表明借款人是否会拖欠付款。任务目标是通过训练集训练模型，来预测测试集中`loan_default`字段的具体值，即借款人是否会拖欠付款，以此为依据，降低贷款风险。

赛题数据由训练集和测试集组成，总数据量超过25w，包含52个特征字段。为了保证比赛的公平性，将会从中抽取15万条作为训练集，3万条作为测试集，同时会对部分字段信息进行脱敏。

本次竞赛的评价标准采用 `F1-score` 指标。

## 方案介绍

这个比赛属于学习实践性质，比较简单。主要参考使用了@第一次打比赛 大佬的baseline套路。

- 特征工程思路
    - 构造新特征。例如：有效贷款总数、主账户违约比率、二级账户违约比率、总违约比率、总未还贷款金额比率等。
    - 数值特征的统计特征。计算构造credit-score关于类别特征的mean统计特征。
    - 尝试对age/loan_to_asset_ratio_bin进行较粗粒度的序数编码，希望增强泛化能力（但好像没什么用）。
    - 目标编码（target encoding）。对employee_code_id/supplier_id/branch_id等类别特征做目标编码。
    - 计数编码（count encoding）。对employee_code_id/supplier_id/branch_id等类别特征做计数编码。
- 模型
    - 单模 10折交叉验证 LightGBM


## 运行环境

> numpy 1.21.1
> pandas 1.3.1
> scikit-learn 0.24.2
> lightgbm 3.2.1
> tqdm 4.51.0





 
