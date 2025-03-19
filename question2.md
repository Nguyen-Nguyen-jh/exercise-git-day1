### If we have a feature branch that hasn't been merged to production and that branch has a bug, what course of action are you going to do with Git before resolving the bug?

1. Nếu nhánh master bị bug:

**Trường hợp 1**: Bug do merge logic. Sau khi merge xong gặp lỗi ==> tạo 1 nhánh mới từ master để sửa lỗi, sau khi sửa xong thì tạo pull request vào nhánh master

```sh
git checkout master
git checkout -b fix-merge-bug
```

==> Tạo PR từ nhánh fix-merge-bug vào master

**Trường hợp 2**: nếu muốn sửa lỗi ở master mà không mất các commit trước đó ==> sử dụng git revert để hoàn tác lại quá trình merge, sau đó quay lại nhánh feature để sửa lỗi và tạo pull request vào nhánh master

```sh
git checkout master
git revert <merge-commit-id>

git checkout feature/feature-base
```

==> sau khi sửa lỗi ở nhánh feature-base xong thì tạo pull request vào nhánh master

==> Tạo PR từ nhánh fix-merge-bug vào master

2. Nếu nhánh feature đang code bị bug:

**Hướng giải quyết**: Tiến hành sửa lỗi ngay trên nhánh feature đang bị bug, sao đó push lên origin như bình thường

```sh
git checkout feature/feature-base
# Sửa lỗi trong mã của bạn
git add .
git commit -m "Fix bug in feature logic"
```

3. Nhánh feature bị bug nhưng bug tới từ nhánh feature khác mà mình base trên đó:

**Hướng giải quyết**: checkout về nhánh feature-base để sử lỗi như bình thường, tiếp theo hãy chuyển sang nhánh feature, sau đó merge nhánh feature-base vào nhánh feature để tiến hành sửa lỗi

```sh
git checkout feature/feature-base
# sửa lỗi tại nhánh feature-base

git checkout feature/sub-feature
git merge feature/feature-base
```

4. Nhánh feature bị bug nhưng bug là do gom code từ các nhánh đang phát triển khác và lúc merge vào bị conflict logic

**Hướng giải quyết**: checkout một nhánh mới từ feature-base bị bug do gom code, sau đó tiến hành fix conflict đã merge trước đó, sau khi fix xong merge lại vào nhánh feature/base.

```sh
git checkout feature/feature-base
git checkout -b feature/new-feature
# tiến hành fix conflict

git checkout feature/feature-base
git merge feature/new-feature
```
