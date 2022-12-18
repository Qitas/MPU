
.. _devops:

DevOps
===============

.. contents::
    :local:
    :depth: 1

简介
-----------

DevOps 是一个完整的面向IT运维的工作流，以 IT 自动化以及持续集成（CI）、持续部署（CD）为基础，来优化程式开发、测试、系统运维等所有环节。

DevOps（英文Development和Operations的组合）是一组过程、方法与系统的统称，用于促进开发（应用程序/软件工程）、技术运营和质量保障（QA）部门之间的沟通、协作与整合。它的出现是由于软件行业日益清晰地认识到：为了按时交付软件产品和服务，开发和运营工作必须紧密合作


DevOps的引入能对产品交付、测试、功能开发和维护（包括──曾经罕见但如今已屡见不鲜的──“热补丁”）起到意义深远的影响。在缺乏DevOps能力的组织中，开发与运营之间存在着信息“鸿沟”──例如运营人员要求更好的可靠性和安全性，开发人员则希望基础设施响应更快，而业务用户的需求则是更快地将更多的特性发布给最终用户使用。这种信息鸿沟就是最常出问题的地方。

一般而言，当企业希望将原本笨重的开发与运营之间的工作移交过程变得流畅无碍，他们通常会遇到以下三类问题：
发布管理问题：很多企业有发布管理问题。他们需要更好的发布计划方法，而不止是一份共享的电子数据表。他们需要清晰了解发布的风险、依赖、各阶段的入口条件，并确保各个角色遵守既定流程行事。
发布/部署协调问题：有发布/部署协调问题的团队需要关注发布/部署过程中的执行。他们需要更好地跟踪发布状态、更快地将问题上升、严格执行流程控制和细粒度的报表。
发布/部署自动化问题：这些企业通常有一些自动化工具，但他们还需要以更灵活的方式来管理和驱动自动化工作──不必要将所有手工操作都在命令行中加以自动化。理想情况下，自动化工具应该能够在非生产环境下由非运营人员使用。
要开始优化发布流程，可以从问题识别开始：看看上面提到的哪种问题在你的团队中具有最高的优先级。

全面自动化 —— 部署、 升级、 扩展、 维护、 数据卫生、 测试、 监测、 安全和策略管理。在自动化方面投入巨资，目标是100%的自动化，不考虑低于90%的可能性。但是，全面自动化也可能会引起自动化泛滥。集中审查和调整可以控制Chef或Puppet脚本库的无序增长。

工具链
-----------

现将工具类型及对应的不完全列举整理如下：

* 代码管理（SCM）：GitHub、GitLab、BitBucket、SubVersion
* 构建工具：Ant、Gradle、maven
* 自动部署：Capistrano、CodeDeploy
* 持续集成（CI）：Bamboo、Hudson、Jenkins
* 配置管理：Ansible、Chef、Puppet、SaltStack、ScriptRock GuardRail
* 容器：Docker、LXC、第三方厂商如AWS
* 编排：Kubernetes、Core、Apache Mesos、DC/OS
* 服务注册与发现：Zookeeper、etcd、Consul
* 脚本语言：python、ruby、shell
* 日志管理：ELK、Logentries
* 系统监控：Datadog、Graphite、Icinga、Nagios
* 性能监控：AppDynamics、New Relic、Splunk
* 压力测试：JMeter、Blaze Meter、loader.io
* 预警：PagerDuty、pingdom、厂商自带如AWS SNS
* HTTP加速器：Varnish
* 消息总线：ActiveMQ、SQS
* 应用服务器：Tomcat、JBoss
* Web服务器：Apache、Nginx、IIS
* 数据库：MySQL、Oracle、PostgreSQL等关系型数据库；cassandra、mongoDB、redis等NoSQL数据库
* 项目管理（PM）：Jira、Asana、Taiga、Trello、Basecamp、Pivotal Tracker

在工具的选择上，需要结合公司业务需求和技术团队情况而定。Ansible是用于在可重复的方式将应用程序部署到远程节点和配置服务器的开源工具。 它为您提供了使用推送模型设置推送多层应用程序和应用程序工件的通用框架，但如果愿意，您可以将其设置为主客户端。 Ansible是建立在playbooks，你可以应用于各种各样的系统部署你的应用程序。


