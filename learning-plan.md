# ARM Enterprise 会员模块 & 销售模块 — 学习计划

> 制定日期：2026-06-27
> 学习方式：碎片时间（每天 30 分钟 ~ 1 小时）
> 总周期：约 14 周（2-3 个月）
> 目标：按 A（快速上手）→ B（深入理解）→ C（实战开发）→ D（架构审视）递进学习

---

> 学习进度见 [member-progress.md](member-progress.md)

---

## 模块概览

| 维度 | 会员（MS 模块） | 销售（跨模块） |
|------|----------------|---------------|
| 子域数量 | 30 个 | 13 个（跨 15 个模块） |
| Entity 文件 | 315（含 external/pojo） | 分散在 goods/sales/order/settle/inv/report 等 |
| JSP 页面 | 158 | 分散在多个模块目录 |
| 核心位置 | `arm-web/.../modules/ms/` | `goods/` `sales/` `order/` `settle/` `inv/` `report/` 等 |

---

## 会员（MS）子域全景

| # | 子域 | 核心实体（部分） |
|---|------|-----------------|
| 1 | 会员资料 | MsMemberDef, MsMemberDefExtend, MsMemberBaby, MsMemberLinkman, MsMemberLog |
| 2 | 会员等级 | MsMemberLevel, MsMemberUpgradeRule, MsMemberUpgradeRecord, MsMemberLevelRewardRule |
| 3 | 会员目标 | MsMemberTarget |
| 4 | 会员积分 | MsPointConfig, MsPointLogRecord, MsLoyaltyPointRecord, MsPointsExchangeDef, ServicePointRatio |
| 5 | 超级会员 | MsSuperMemberInstance, MsSuperMemberGradeDef, MsSuperMemberAccountList, MsSuperAutomaticRenewConfig |
| 6 | 新客/联合注册 | MsMemberJointRegistrationConfig, MsMemberJointRegistrationSynMember/Order/Logistics 等 |
| 7 | 往来账 | MsAcctBookConfig, MsAcctBookDef, MsCurrentAccountShopBalance, MsCurrentAccountShopPoint |
| 8 | 服务卡 | ServiceCardDef, MsCardDef, ServiceCardGoodsDef, ServiceCardLog, ServiceCardSalesExtractRule |
| 9 | 服务销售 | ServiceSales, ServiceSalesDetail, ServiceGoodsSales, CombinationPackageDef |
| 10 | 服务预约 | ServicePreserve, ServicePreserveRule, ServicePreservePeriod, ServiceOfficeArrangement |
| 11 | 服务评价 | ServiceEvaluateDef, ServiceEvaluateModule |
| 12 | 技师管理 | ServiceTechnicianArrangement, TechnicianUserRelation |
| 13 | 会员认证 | MsMemberAuthentication, MsMemberAuthenticationConfig, MsMemberCertificationRecord |
| 14 | 变更审批 | MsMemberChangeApprove, MsMemberChangeApproveDetail |
| 15 | 会员分配 | MsAutoDistributionRules, MsMemberDistribution, MsDistributionRulesExec |
| 16 | 会员追踪 | MsMemberTrace, MsMemberTrack, MsMemberPosition, MsMemberShoppingCount |
| 17 | 会员奖励 | MsRewardConfig, MsRewardRuleConfig, MsMemberReward, MsRewardCashBackDetail |
| 18 | 发货/配送 | MsSendGoodsOrderDef, MsShippingTemplate, MsShippingTemplateRegion |
| 19 | 罐体码 | MsCanBodyCode, MsCanBodyCodeDetail |
| 20 | 忠诚度 | MsOfficeLoyalty, MsLoyaltyClearPlan, MsLoyaltyClearLog |
| 21 | 会员档案 | MsArchivesTemplate, MsArchivesInstance, MsArchivesClassify |
| 22 | 发票管理 | MsInvoice, MsInvoiceBillsDetail, MsInvoiceGoodsDetail |
| 23 | PRM 联合权益 | PrmJoinManagementRule, PrmJoinExternalDataSyn |
| 24 | 第三方同步 | ThirdPartyDataSyn, MqMemberData, GoodsYbeRepairSaveData |
| 25 | 会员资产 | MsMemberAssetsLog, MsMemberPropertyVerifyConfig |
| 26 | 服务项目分类 | ServiceCategoryDef, ServiceTypeDef, ServiceTypeDeptSpecials |
| 27 | 信贷/赊账 | CreditOrder, CreditOrderRepayment |
| 28 | 定时营销 | MsFixedTimeLog, MsFixedTimeTaskConfig |
| 29 | 月嫂服务 | MsServiceMonthGirl, MsServiceMonthGirlEndMoneyList |
| 30 | 系统/标签 | SysDynamicCode, SysTagParamIns, SysTagParamValueIns |

---

## 销售子域全景（跨模块分布）

| # | 子域 | 主模块 | 核心实体（部分） |
|---|------|--------|-----------------|
| 1 | 销售主数据 | goods | GoodsSales, GoodsSalesDetail, GoodsSalesExtend |
| 2 | 销售退货 | goods, inv | GoodsSalesRefundExchange, InvReturnFactory |
| 3 | 寄存提取 | goods | GoodsSalesDeposit, GoodsSalesDepositPick, DepositPickSettle |
| 4 | 换货/退换货 | goods | GoodsSalesExchange, GoodsSalesRefundExchange, GrpExtProdExchange |
| 5 | 销售目标 | goods, inv, ms | SalesTask, StoreSalesTask, ServiceCardSalesTask, MsMemberTarget |
| 6 | 促销 | goods, ms | GoodsPromotionBase, GoodsPromotionDetail, ServiceSalesPromotion |
| 7 | 提成/返利 | goods, ms, cont, bp | GoodsSalesDeduct, GoodsDeductCalculate, MsSalesDetailRebateShare, ContRebateRule |
| 8 | 优惠券 | goods, sales, ms | GoodsTicket, GoodsSalesUseBrandCoupon, GoodsSalesTicketDeduction |
| 9 | 导购 | goods, ms | guideId/salesmanId 贯穿 GoodsSales/SalesTask/ResourceSales |
| 10 | 分摊 | goods, sales, ms | GoodsSalesDetailShare, GoodsPromotionShare, BrandCouponShare |
| 11 | 销售结算 | goods, settle | GoodsSalesSettle, BillSettle, BillSettleApplication |
| 12 | 销售支付 | goods | GoodsSalesPay, GoodsSalesPayConfig, GoodsSalesSelfPay |
| 13 | 销售报表 | report | SumGoodsSalesDay, SumMemberLevelSale, SumStaffSalesDay |
| + | 预售 | goods | PreSalesOrder, PreSalesOrderPick |
| + | 批发销售 | inv | InvWholesaleStock, InvWholesaleSettleOrder |
| + | 门店销售 | inv | InvStoreSales, InvStoreSalesDetail |
| + | 自助扫码购 | smg | SmgGoodsSales |
| + | 资源销售 | sales | ResourceSales, ResourceSalesConfig, ResourceSalesRule |
| + | 外部对接 | sales | GoodsSalesSynExternalBrandRecord, HaiBoOrderLogisticsApiInterface |
| + | 销售台账 | ledger | GoodsSalesDueLedger |
| + | 费用账户 | account | SalesSubAccount |

---

## 阶段 A：快速上手（第 1-3 周）

### 单元 1：会员基础 — 会员资料、等级、会员卡

| 日期 | 主题 | 核心文件 | 要点 |
|------|------|---------|------|
| Day 1-2 | 会员核心数据模型 | `MsMemberDef.java`、`MsMemberDefExtend.java`、`MsMemberBaby.java`、`MsMemberLinkman.java`、`MsMemberLog.java` | 会员编号生成规则、状态枚举、渠道概念、宝宝/联系人关联 |
| Day 3-4 | 会员等级体系 | `MsMemberLevel.java`、`MsMemberLevelService.java`、`MsMemberUpgradeRule.java`、`MsMemberUpgradeRecord.java`、`MsMemberLevelRewardRule.java` | 升降级触发条件、自动/手动升级、折扣计算、降级保护机制 |
| Day 5-6 | 会员卡管理 | `MsCardDef.java`、`MsCardTypeDef.java`、`MsCardLog.java`、`MsMemberCardLog.java`、对应 JSP 页面 | 卡类型定义、制卡/发卡/挂失流程、实体卡与虚拟卡 |
| Day 7 | 复盘 | 画出会员档案→等级变更→卡管理的完整数据流 | 输出实体关系图 + Service 调用链 |

### 单元 2：销售基础 — 销售主数据、支付、收款、导购

| 日期 | 主题 | 核心文件 | 要点 |
|------|------|---------|------|
| Day 1-2 | 销售主数据 | `GoodsSales.java`（goods模块）、`GoodsSalesDetail.java`、`GoodsSalesExtend.java` | 销售单结构、销售类型（销售/退货）、销售渠道、导购关联 |
| Day 3-4 | 支付与收款 | `GoodsSalesPay.java`、`GoodsSalesPayDetail.java`、`GoodsSalesPayConfig.java`、`GoodsSalesShiftcycle.java`（缴款单） | 支付方式（支付宝/微信/银联/现金）、收银流程、交接班 |
| Day 5-6 | 导购体系 | `GoodsSales.java`（guideId/salesmanId字段）、`GoodsTicketGuidSendLog.java`、`goods/vo/GuiderSalesTargetImportVo.java` | 导购归属、导购提成来源、导购发券 |
| Day 7 | 复盘 | 画出一笔销售从开单到收银的完整链路 | 输出时序图 + GoodsSales 字段速查表 |

### 单元 3：会员销售衔接 — 服务卡、服务销售、服务项目分类

| 日期 | 主题 | 核心文件 | 要点 |
|------|------|---------|------|
| Day 1-2 | 服务卡定义 | `ServiceCardDef.java`、`ServiceCardGoodsDef.java`、`ServiceCardGroupGoodsDef.java`、`MsCardDef.java` | 套盒/服务卡的区别、服务卡与普通商品的关系 |
| Day 3-4 | 服务销售 | `ServiceSales.java`、`ServiceSalesService.java`、`ServiceSalesDetail.java`、`ServiceGoodsSales.java` | 售卡/退卡事务、与 GoodsSales 的联动 |
| Day 5-6 | 服务项目分类 | `ServiceCategoryDef.java`、`ServiceTypeDef.java`、`ServiceTypeDeptSpecials.java`、`ServiceOfficeCategory.java` | 大类/小类/部门特项的层级关系 |
| Day 7 | 复盘 | 画出"选服务项目→生成服务卡→售卡→关联会员"完整链路 | 输出 ServiceSales ↔ GoodsSales ↔ MsMemberDef 三角关系图 |

---

## 阶段 B：深入理解（第 4-7 周）

### 单元 4：会员运营 — 积分、忠诚度、奖励、往来账

| 日期 | 主题 | 核心文件 | 要点 |
|------|------|---------|------|
| Day 1-2 | 积分体系 | `MsPointConfig.java`、`MsPointLogRecord.java`、`MsLoyaltyPointRecord.java`、`ServicePointRatio.java`、`MsPointsExchangeDef.java` | 积分获取/消费规则、积分比例计算、积分兑换逻辑 |
| Day 3-4 | 忠诚度与奖励 | `MsOfficeLoyalty.java`、`MsOfficeLoyaltyRecord.java`、`MsLoyaltyClearPlan.java`、`MsRewardConfig.java`、`MsRewardRuleConfig.java`、`MsMemberReward.java` | 门店忠诚度计算、积分清零计划、奖励来源/规则/发放 |
| Day 5-6 | 往来账 | `MsAcctBookConfig.java`、`MsAcctBookDef.java`、`MsCurrentAccountShopBalance.java`、`MsCurrentAccountShopPoint.java` | 会员账本实例、门店往来账余额/积分、账本与销售的关系 |
| Day 7 | 复盘 | 画出积分→忠诚度→奖励→往来账的运营闭环 | 输出积分流转图 + 忠诚度计算规则总结 |

### 单元 5：销售全链路 — 退货、寄存提取、换货退换货、预售

| 日期 | 主题 | 核心文件 | 要点 |
|------|------|---------|------|
| Day 1-2 | 销售退货 | `GoodsSales.java`（wholeRefund字段）、`GoodsSalesRefundExchange.java`、`goods/GoodsSalesRefundBusinessFlowTask.java`、`inv/InvReturnFactory.java` | 整单/部分/无单退货、退货业务流、工厂退货 |
| Day 3-4 | 寄存提取 | `GoodsSalesDeposit.java`、`GoodsSalesDepositPick.java`、`GoodsSalesDepositDetail.java`、`DepositPickSettle.java` | 寄存头表/明细、提货流程、寄存延期、寄存转销售 |
| Day 5-6 | 换货退换货 + 预售 | `GoodsSalesExchange.java`、`GoodsSalesRefundExchange.java`、`PreSalesOrder.java`、`PreSalesOrderPick.java` | 换货差额计算、退换货双单关联、预售→提货链路 |
| Day 7 | 复盘 | 画出"销售→退货/换货/寄存→提取"的完整状态流转图 | 输出 GoodsSales 生命周期状态机 |

### 单元 6：促销与优惠券

| 日期 | 主题 | 核心文件 | 要点 |
|------|------|---------|------|
| Day 1-2 | 促销体系 | `GoodsPromotionBase.java`、`GoodsPromotionDetail.java`、`GoodsPromotionGift.java`、`GoodsPromotionAcctBook.java`、`ServiceSalesPromotion.java` | 满减/满折/满赠/组合价/超量促销、促销与账本的关系 |
| Day 3-4 | 券体系 | `GoodsTicket.java`、`GoodsTicketClassify.java`、`GoodsTicketPackage.java`、`GoodsTicketGiveLog.java`、`GoodsSalesTicketDeduction.java` | 券码生成/分类/打包/赠送/核销/抵扣完整链路 |
| Day 5-6 | 品牌券 | `GoodsSalesUseBrandCoupon.java`、`GoodsSalesUseBrandCouponRule.java`、`GoodsSalesUseBrandCouponShare.java`、`GoodsSalesReceiveBrandCoupon.java` | 品牌券使用规则、券分摊、品牌券接收与核销 |
| Day 7 | 复盘 | 画出促销方案→券发放→销售用券→券分摊的完整链路 | 输出促销类型速查表 + 券状态流转图 |

### 单元 7：导购提成与分摊

| 日期 | 主题 | 核心文件 | 要点 |
|------|------|---------|------|
| Day 1-2 | 导购提成 | `GoodsSalesDeduct.java`、`GoodsDeductCalculate.java`、`GoodsDeductRecalculation.java`、`GoodsSalesRebateConfig.java` | 提成计算基准、提成重算触发时机、返利配置 |
| Day 3-4 | 促销与折扣分摊 | `GoodsSalesDetailShare.java`、`GoodsPromotionShare.java`、`GoodsDiscountShareDetail.java`、`GoodsShareRecal.java` | 促销费用分摊、折扣分摊、分摊重算 |
| Day 5-6 | 返利分摊 + 服务提成 | `MsSalesDetailRebateShare.java`、`MsSuperMemberRebateShareRecalculate.java`、`ServiceCardSalesExtractRule.java`、`ServiceOnceConsumerExtract.java` | 返利分部门/分导购、服务卡提成、一次性消费提成 |
| Day 7 | 复盘 | 画出一笔销售中促销/折扣/提成/返利的费用分拆图 | 输出分摊层次示意图 |

---

## 阶段 C：实战开发（第 8-11 周）

### 单元 8：超级会员

| 日期 | 主题 | 核心文件 | 要点 |
|------|------|---------|------|
| Day 1-2 | 超级会员等级与模板 | `MsSuperMemberGradeDef.java`、`MsSuperMemberGradeGoodsDef.java`、`MsSuperMemberGradeOfficeSpecial.java`、`MsSuperMemberTemplate.java` | 超会等级定义、等级商品、门店特项、模板复制 |
| Day 3-4 | 超级会员实例与续费 | `MsSuperMemberInstance.java`、`MsSuperMemberInstanceTicketApportion.java`、`MsSuperAutomaticRenewConfig.java`、`MsSuperManualRenewConfig.java` | 实例生命周期、券分摊、自动/手动续费配置 |
| Day 5-6 | 账户与返利分摊 | `MsSuperMemberAccountList.java`、`MsSuperMemberAccountLog.java`、`MsSuperMemberRebateShareRecalculate.java`、`MsSuperMemberIntroduce.java` | 超会账户流水、返利分摊重算、介绍人机制 |
| Day 7 | 复盘 | 画出超级会员"购买→生效→续费→到期"完整生命周期 | 输出超会状态机 + 返利分摊计算公式 |

### 单元 9：新客与联合注册

| 日期 | 主题 | 核心文件 | 要点 |
|------|------|---------|------|
| Day 1-2 | 联合注册配置 | `MsMemberJointRegistrationConfig.java`、`MsMemberJointRegistrationConfigDetail.java`、`MsMemberJointRegistrationRules.java`、`MsMemberJointRegistrationPrivacyAgreement.java` | 多品牌联合注册规则、隐私协议、奖励配置 |
| Day 3-4 | 数据同步 | `MsMemberJointRegistrationSynMember.java`、`MsMemberJointRegistrationSynOrder.java`、`MsMemberJointRegistrationSynLogistics.java`、`MsMemberJointRegistrationSynBodyCode.java` | 会员/订单/物流/罐体码同步、同步日志与重试 |
| Day 5-6 | 品牌对接 | `MsMemberJointRegistrationBrandEquity.java`、`MsMemberJointRegistrationBrandMember.java`、`MsMemberExternalRelation.java`、`entity/external/` 下的各品牌 DTO（飞鹤、君乐宝、慧氏等） | 品牌权益、外部会员关联、品牌 API 对接格式 |
| Day 7 | 复盘 | 画出联合注册"配置→规则→同步"的数据流 | 输出品牌对接清单 + 同步字段映射表 |

### 单元 10：销售结算与报表

| 日期 | 主题 | 核心文件 | 要点 |
|------|------|---------|------|
| Day 1-2 | 销售结算 | `GoodsSalesSettle.java`、`GoodsSalesSettleAvg.java`、`GoodsSalesShiftcycle.java`、`ServiceGoodsSalesSettle.java` | 成本核算（dealPrice - stockPrice）、缴款单、交接班结算 |
| Day 3-4 | 结算单管理 | `BillSettle.java`（settle模块）、`BillSettleDetail.java`、`BillSettleApplication.java`、`BillSettleRecalculation.java` | 结算单生成、结算申请/审批、结算重算 |
| Day 5-6 | 销售报表 | `report/SumGoodsSalesDay.java`、`report/SumMemberLevelSale.java`、`report/SumStaffSalesDay.java`、`report/SumMemberGoodsSalesCount.java` | 日报/员工/部门/会员维度报表、定时任务生成 |
| Day 7 | 复盘 | 画出"销售→结算单→往来账→报表"的财务闭环 | 输出报表维度清单 + 结算流程图 |

### 单元 11：资源销售与外部对接

| 日期 | 主题 | 核心文件 | 要点 |
|------|------|---------|------|
| Day 1-2 | 资源销售 | `ResourceSales.java`、`ResourceSalesConfig.java`、`ResourceSalesRule.java`、`ResourceSalesDetail.java` | 资源销售（非商品类销售）、资源规则与配置 |
| Day 3-4 | 品牌同步 | `GoodsSalesSynExternalBrandRecord.java`、`GoodsSalesSynHaiBoStatus.java`、`GoodsSalesReceiveBrandCoupon.java` | 品牌数据回传、券接收确认 |
| Day 5-6 | 物流对接 | `GoodsSalesHaiboLogisticCoordinate.java`、`GoodsSalesHaiboLogisticStatus.java`、`HaiBoOrderLogisticsApiInterface.java`、`GoodsLogisticsCodeInterface.java` | 海博物流状态同步、物流编码映射 |
| Day 7 | 复盘 | 画出"销售完成→品牌同步→物流回传"的外部对接全景 | 输出外部接口清单 + 对接品牌列表 |

---

## 阶段 D：架构审视（第 12-14 周）

### 单元 12：会员高阶子域

| 日期 | 主题 | 核心文件 | 要点 |
|------|------|---------|------|
| Day 1-2 | 会员认证与变更审批 | `MsMemberAuthentication.java`、`MsMemberAuthenticationConfig.java`、`MsMemberCertificationRecord.java`、`MsMemberChangeApprove.java` | 认证配置/记录、会员信息变更审批流程 |
| Day 3-4 | 会员分配与追踪 | `MsAutoDistributionRules.java`、`MsMemberDistribution.java`、`MsMemberTrace.java`、`MsMemberTrack.java`、`MsMemberLatestPosition.java` | 自动分配规则、会员归属分配、轨迹/位置记录、复购统计 |
| Day 5-6 | 档案、预约、其他 | `MsArchivesTemplate.java`、`MsArchivesInstance.java`、`ServicePreserve.java`、`ServicePreserveRule.java`、`ServiceEvaluateDef.java`、`MsInvoice.java`、`MsShippingTemplate.java` | 自定义档案模板、服务预约全流程、评价体系、发票、配送 |
| Day 7 | 复盘 | 梳理全 MS 模块的实体依赖关系图 | 输出 MS 模块完整子域地图 + 未覆盖项清单 |

### 单元 13：销售高阶子域

| 日期 | 主题 | 核心文件 | 要点 |
|------|------|---------|------|
| Day 1-2 | 门店销售与批发 | `InvStoreSales.java`（inv模块）、`InvWholesaleStock.java`、`InvWholesaleSettleOrder.java`、订单分解策略 `order/decompose/` | 门店/批发销售差异、销售订单分解模式 |
| Day 3-4 | 自助购、台账、费用 | `smg/SmgGoodsSales.java`、`ledger/GoodsSalesDueLedger.java`、`account/SalesSubAccount.java` | 自助扫码购流程、销售应计账、费用子账户 |
| Day 5-6 | 定时任务全景 | `task/arm/` 下各销售相关 Task：`DailySalesTask.java`、`GoodsSalesDetailShareTask.java`、`CountSalesCardExtractTask.java`、`DepositToSalesTask.java` 等 | 日常定时任务的执行时机、依赖关系、失败处理 |
| Day 7 | 复盘 | 梳理销售跨模块调用关系图 | 输出销售 13 个子域 × 15 个模块的矩阵图 |

### 单元 14：全局审视

| 日期 | 主题 | 内容 | 输出 |
|------|------|------|------|
| Day 1-2 | 跨模块调用链 | 梳理 MS ↔ goods ↔ order ↔ settle ↔ finance ↔ inv 的核心调用关系 | 模块依赖拓扑图 |
| Day 3-4 | 数据一致性 | 分析 ServiceSales / GoodsSales 的双写场景，积分/储值的事务边界，定时任务补偿机制 | 一致性风险清单 |
| Day 5-6 | 技术债务与重构方向 | 识别超大 Service（如 MsMemberDefService 150+ 方法）、JSP 页面复杂度、跨模块耦合点 | 重构优先级排序表 |
| Day 7 | 总结 | 整理完整的会员+销售知识地图，标注已掌握和待深入的部分 | 个人学习笔记归档 |

---

## 学习建议

1. **每单元 Day 7 的复盘不要跳过** — 这是碎片化学习的关键粘合剂，画图/记笔记能大幅提升记忆留存
2. **带着问题读代码** — 每看一个 Service，先想"如果我要实现这个功能，会怎么写"，再对照实际代码
3. **动手验证** — 学完一个子域后，在本地启动项目，走一遍对应页面的操作流程，打断点跟踪调用链
4. **交叉关联** — 看到会员侧的 ServiceSales 时，主动跳到 goods 侧看 GoodsSales 的实现，建立横向理解
5. **积累速查表** — 每个阶段结束后，整理一份"关键表/关键字段/关键接口"速查笔记，后续开发时直接查阅

---

---

## 关键入口速查

### 会员侧
| 入口 | 文件 | 说明 |
|------|------|------|
| 会员列表页 | `MsMemberDefController.java` → JSP | 会员管理主入口 |
| 会员等级 | `MsMemberLevelController.java` | 等级配置入口 |
| 服务销售 | `ServiceSalesService.java` | 售卡/退卡核心逻辑 |
| 积分记录 | `MsPointLogRecord.java` | 积分流水查询 |
| 超级会员 | `MsSuperMemberInstanceController.java` | 超会实例管理 |
| 联合注册 | `MsMemberJointRegistrationController.java` | 联合注册配置和管理 |

### 销售侧
| 入口 | 文件 | 说明 |
|------|------|------|
| 销售单 | `GoodsSales.java` (goods模块) | 销售主数据 |
| 退货 | `GoodsSalesRefundExchangeController.java` | 退货入口 |
| 寄存 | `GoodsSalesDepositController.java` | 寄存管理入口 |
| 促销 | `GoodsPromotionBaseController.java` | 促销配置入口 |
| 券管理 | `GoodsTicketController.java` | 券码管理入口 |
| 结算 | `BillSettleController.java` (settle模块) | 结算管理入口 |
| 报表 | `report/SumGoodsSalesDay.java` | 销售日报 |
