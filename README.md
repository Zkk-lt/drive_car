# drive_car 完整目录备份

本仓库保存 `/home/ubuntu/drive_car` 的完整目录快照，备份日期为 2026-10-19（北京时间）。

包含源码、启动配置、第三方依赖、编译产物、实验数据、隐藏文件以及原目录和嵌套项目的 `.git` 历史；未应用 `.gitignore` 排除规则。符号链接按链接保存，不会复制链接指向的目录外文件。本备份不包含工作目录之外的 ROS、系统软件或硬件配置。

为了保存大文件，完整目录采用 gzip 压缩并拆分为每卷最多 45 MiB 的文件，按 `archive/drive_car.tar.gz.part-*` 文件名顺序拼接。代码位于压缩备份中，恢复后可直接查看。

## 校验

在本仓库根目录执行：

```sh
sha256sum -c SHA256SUMS
```

所有分卷都必须显示 `OK`。

## 恢复

请使用新的空目录作为恢复目标，避免覆盖现有工作区：

```sh
mkdir restored
cat archive/drive_car.tar.gz.part-* | tar -xzf - -C restored
```

完整目录恢复到 `restored/drive_car/`，原始 Git 历史也在其中。`mkdir restored` 如果提示目录已存在，请改用另一个新的空目录。

恢复不会自动启动 ROS 节点或车辆程序。编译产物来自原机器；在其他环境使用时可能需要重新编译。
