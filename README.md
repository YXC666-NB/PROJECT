# K8s云原生运维实战项目
> 基于 openEuler 24.03 LTS SP2 + Kubernetes 1.30 模拟生产环境，完整复现容器化业务部署、存储管理、CI/CD流水线、监控告警、日志采集整套运维流程。

## 仓库目录说明
| 目录 | 项目说明 |
|------|--------|
| Ghost | Ghost博客容器化业务，StatefulSet部署MySQL数据库 |
| harbor-project | Harbor私有镜像仓库部署配置 |
| helm-project | 自定义Helm Chart，支持多环境部署管理 |
| jenkins-project | Jenkins Pipeline CI/CD流水线脚本，实现代码到K8s自动发布 |
| local‑path‑provisioner‑project | LocalPV + StorageClass本地动态存储方案 |
| monitor | Prometheus+Grafana监控告警体系，钉钉告警通知 |
| statefulSet‑mysql‑redis‑cronJob‑project | 有状态应用部署，CronJob定时数据库备份 |

## 技术栈
- **容器编排**：Kubernetes1.30、Docker
- **应用管理**：Helm、StatefulSet、Deployment、RBAC、ConfigMap、Secret、探针
- **CI/CD**：Jenkins Pipeline、Harbor私有镜像仓库
- **存储**：LocalPV、StorageClass
- **可观测**：Prometheus、Grafana、Alertmanager、Loki、Fluent‑Bit
- **系统&脚本**：openEuler Linux、Shell脚本

## 项目实现功能
1. 搭建1Master+2Worker K8s集群，使用Namespace做资源隔离，RBAC最小权限管控集群访问；
2. 使用StatefulSet部署MySQL有状态服务，CronJob定时执行数据库备份，提升业务容灾能力；
3. LocalPV改造存储，解决Pod漂移带来的数据丢失问题；ConfigMap/Secret分离配置与敏感信息；
4. 封装Helm Chart，通过多套values文件区分开发、测试环境，简化YAML冗余，实现应用一键部署、升级、回滚；
5. 完整CI/CD流水线：代码提交→镜像构建→Harbor推送→K8s滚动更新，将人工部署耗时缩短至数分钟；
6. 监控体系：采集集群、数据库、业务站点指标，配置钉钉告警，故障及时通知；
7. Loki+Fluent‑Bit实现容器日志统一采集检索，完善集群可观测能力。

## 个人收获
完整实践云原生运维全链路，熟悉K8s各类资源对象、故障排查思路，掌握CI/CD自动化发布、存储、监控告警落地方案，积累SRE基础实战经验。
