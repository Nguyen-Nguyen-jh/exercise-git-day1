### When creating a new feature, what branch should we base it on and why?

1. Nếu trong trường hợp tính năng mới cần release trước nhưng trong master lại đang có những tính năng chưa cần release

**Trả lời**
==> Checkout trực tiếp từ production để phát triển tính năng mới. Vì nhánh master đang chứa những feature chưa cần release, và feature mới này lại không liên quan gì đến những feature trên nhánh master thì ta nên ưu tiên việc checkout từ production branch

git checkout production
git checkout -b <new-feature>

2. Nếu như feature branch mới đang cần dựa vào một feature branch khác đã được update xong

**Trả lời**
==> checkout từ feature branch đã chạy ổn định và sau khi làm xong thì có thể merge lại nhánh feature đã chạy ổn định đấy

git checkout <feature-branch>
git checkout -b <new-feature-branch>

git checkout <feature-branch>
git merge <new-feature-branch>

3. Nếu như feature branch mới đang cần dựa vào một feature branch khác nhưng lại chưa được update xong

**Trả lời**
==> checkout từ feature branch với lần commit mới nhất đã chạy ổn định và sau khi làm xong thì có thể merge lại nhánh feature đã chạy ổn định đấy

git checkout <feature-branch>
git checkout -b <new-feature-branch>
git reset --hard <commitId-stable>

git checkout <feature-branch>
git merge <new-feature-branch>
