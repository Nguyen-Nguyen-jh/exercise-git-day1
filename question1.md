### When creating a new feature, what branch should we base it on and why?

1. Checkout một tính năng mới, riêng biệt và chỉ cần các code trên production là đủ

**Trả lời**
==> Checkout trực tiếp từ production để phát triển tính năng mới. Vì nhánh master đang chứa những feature chưa cần release, và feature mới này lại không liên quan gì đến những feature trên nhánh master thì ta nên ưu tiên việc checkout từ production branch

```sh
git checkout production
git checkout -b feature/new-feature
```

2. Nếu như feature branch mới đang cần dựa vào một feature branch khác đã được update xong

**Trả lời**
==> checkout từ feature branch đã chạy ổn định và sau khi làm xong thì có thể tạo PR lại nhánh feature đã chạy ổn định đấy

```sh
git checkout feature/feature-base
git checkout -b feature/new-feature
```

==> tạo pull request nhánh new-feature-branch vào nhánh feature branch

3. Nếu như feature branch mới cần code ở 2 nhánh, nhưng cả 2 nhánh đó đều chưa được đưa vào master hoặc production

**Cách 1**: Checkout vào nhánh branch 1 và tạo nhánh mới từ đó, sau đó merge branch2 vào branch1:

```sh
git checkout feature/branch1
git checkout -b new-feature-branch
git merge feature/branch2
```

**Cách 2**: Checkout vào nhánh branch 1 và tạo nhánh mới từ đó, sau đó sử dụng cherry-pick để lấy các commit cần thiết ở branch 2

```sh
git checkout feature/branch1
git checkout -b new-feature-branch
git cherry-pick <commitId-branch2>
```
