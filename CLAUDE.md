# OMLX 升级流程 — ModelScope & Grammar 支持

本仓库 fork 自 jundot/omlx，配方文件 `Formula/omlx.rb` 已添加 `--with-modelscope` 选项。

## 升级命令

需要同时保留 **xgrammar（结构化输出）** 和 **modelscope SDK（魔塔下载）**：

```bash
cd /opt/homebrew/Library/Taps/jundot/homebrew-omlx
git pull upstream main
# 如有冲突，只解决版本号冲突（url/sha256），保留 with-modelscope 相关行
git push origin main
brew upgrade omlx --with-grammar --with-modelscope
```

## 验证

```bash
/opt/homebrew/opt/omlx/libexec/bin/python3.11 -c "import modelscope; print(f'OK: modelscope {modelscope.__version__}')"
tail -5 /opt/homebrew/var/log/omlx.log | grep "ModelScope Downloader"
```

## 首次设置（已配好，仅用于参考）

```bash
git remote set-url origin https://github.com/formp3/omlx
git remote add upstream https://github.com/jundot/omlx
git remote set-url --push upstream no_push
```
