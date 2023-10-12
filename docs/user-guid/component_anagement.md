---
sidebar_position: 3
title: 组件管理
sidebar_label: 组件管理
---

组件管理主要分三部分能力：
- 我发布的：手动发布组件到仓库；同一组件可发布多版本
- 我安装的：手动、自动安装组件；版本更新推送；历史版本管理和一键回滚
- 我订阅的：订阅和取消订阅

## 我发布的

手动发布组件，发布后，可在“组件市场”浏览、下载、订阅或安装。同一组件可发布多版本。

操作步骤如下：
1. 进入[组件市场/组件管理/我发布的]页面，点击** +组件发布 **
2. 弹框中选择组件仓库，上传 helm 包，**确定**后，即开始发布组件，发布成功，返回列表页面
3. “我发布的”列表中展示组件名称、最新版本、组件仓库、当前状态、更新时间，操作：更新、删除
- 当前状态有两种，同步中、正常。
- 更新组件，不可修改组件仓库，可上传新的 helm 包，即发布新版本。
- 删除组件，即删除其所有版本信息，删除后将不再<组件市场>展示。
4. 点击**组件名称**，进入其详情页，展示组件版本列表、组件仓库名称、组件关键词、产品介绍信息
5. 组件详情页，选择版本后，支持删除某一版本

:::info
- 目前仅支持系统管理员admin发布组件到Chart Museum类型的仓库
- 用户主动将组件所有版本均设置为“废弃”状态，则不会显示在“我发布的”列表及组件市场中
:::

## 我安装的

在“组件市场”浏览组件，按需安装组件，当组件有新版本推送时可选择手动或自动更新。

### 安装组件

操作步骤如下：
1. 进入[组件市场/组件管理/我安装的]页面，点击** +组件安装 **，跳转到“组件市场”页面，选择目标集群，浏览组件
2. 找到目标组件，点击**安装**，进入安装页面，填写部署名称、选择组件版本、更新方式、选择租户&项目、查看或调整配置文件、按需添加镜像替换规则
- **建议安装前仔细阅读安装说明**，助您快速正确的安装组件，进行体验
- 部署名称：由3~56个小写字母、数字、中划线“-”或点“.”组成，并以字母、数字开头或结尾。项目&集群内唯一。
- 组件名称和组件仓库自动回显，只读
- 组件版本：下拉列表选择要安装的版本
- 更新方式：默认手动更新。
    - 选择“手动更新”后，当组件有新版本发布后，用户按需手动更新成最新版本。
    - 选择“自动更新”后，当组件有新版本发布后，无需手动更新，按设置的更新时间自动更新成最新版本。
        - `更新时间`支持设置每天的时分，设置后，组件当天有新版本发布后，如果在`更新时间`前发布，则当日`更新时间`即自动更新，否则次日`更新时间`再自动更新。
        - `更新时间`不设置，即有新版本发布后，立即自动更新。此方式需注意对使用组件用户的影响，避免组件服务更新导致用户使用卡顿或中断。
        - 选择“自动更新”，会自动订阅此组件。
- 安装位置：选择租户、项目（上一步已选择集群）
    - 同一项目&集群中也可安装多次相同组件，例如数据库、存储类组件，可部署多个，但部署名称需唯一。 
- 配置文件：value.yaml，支持查看、编辑
- 镜像替换：组件级别的镜像覆盖重写。默认无规则，按需添加。
    - 填写规则：选择已有镜像，替换为新镜像、新镜像名称、新tag。其中选择已有镜像，即依次选择域名、仓库组、镜像名称、tag。
    - 选择已有镜像 - 域名、仓库组后，如果匹配到组件仓库的镜像替换规则，则自动填充替换后的新镜像；否则新镜像用户自定义填写
    - 选择已有镜像 - tag时，选择指定tag，则仅替换此tag；选择全部，则全部替换
3. 填写完成，点击**确定**后，即开始安装，返回安装列表。列表展示部署名称、组件名称、版本、状态、更新方式、所属组件仓库、更新时间。
- 状态：安装中、安装成功、安装失败、卸载中、卸载失败、未知。 其中卸载失败、未知比较少见，如遇到请联系管理员检查kubebb的系统服务组件。
4. 当组件发布新版本后，一周内会有推新的标识。也可点击“版本”旁的new，过滤所有近一周有推新的组件

### 安装版本管理

1. 进入[组件市场/组件管理/我安装的]页面，找到目标部署组件，点击**组件名称**，进入其详情页面
2. 安装信息：展示当前安装的版本信息，包括部署名称、组件名称、组件仓库、版本、更新方式、安装位置、配置文件、镜像替换规则
3. 历史版本：展示此次部署组件的历史版本列表，包括组件名称、版本、更新方式、安装时间。版本处会标识当前版本
- 支持查看各历史版本的安装信息
- 支持按需回滚到某历史版本。主动回滚后，注意会更新其`更新方式`为手动更新。

### 更新组件

1. 进入[组件市场/组件管理/我安装的]页面，找到目标部署组件，按需更新
- 选择新版本升级
- 选择旧版本回退
- 或不调整版本，仅修改配置文件或镜像替换规则等
2. 点击**更新**，进入组件更新页面，部署名称、组件名称、组件仓库、安装位置，不允许修改，其他选项按需调整，点击**确定**，开始更新组件

:::info
更新组件时，组件服务会重启，可能会对用户使用造成影响，请评估后选择合适时间进行更新。
:::

### 卸载组件

1. 进入[组件市场/组件管理/我安装的]页面，找到目标部署组件，点击**卸载**
2. 卸载组件会同步删除此部署下的所有历史版本信息，二次弹框提示，确定后，开始卸载。

## 我订阅的

浏览组件市场，想关注的组件可以提前订阅，及时关注其动态。

操作步骤如下：
1. 进入[组件市场/组件管理/我订阅的]页面，点击** +组件订阅 **，跳转组件市场，找到目标组件，点击卡片区域，进入其详情页面
2. 右上角操作处点击“订阅”，弹框内填写订阅项目，即选择租户、项目，点击**确定**，完成订阅
3. 返回我订阅的列表页，展示订阅的组件列表，包括组件名称、版本、所属组件仓库、订阅时间，操作：取消订阅
4. 点击**组件名称**跳转其组件市场的详情页面，可查看详细信息
5. 如不想继续关注，可取消订阅

:::info
在同一集群中，相同的租户&项目对相同组件只能订阅一次。
:::