### If we have a feature branch that hasn't been merged to production and that branch has a bug, what course of action are you going to do with Git before resolving the bug?

1. Tạo một bugfix branch từ nhánh master, nếu bug đó đã được merge vào master, và sau khi đã fix xong thì merge về lại nhánh master:

git checkout master
git checkout -b bugfix/bug-feature

git checkout master
git merge bugfix/bug-feature

2. Tạo một bugfix branch từ nhánh feature, nếu bug đó chưa được merge vào master, và sau khi đã fix xong thì merge về lại nhánh feature ban đầu:

git checkout feature
git checkout -b bugfix/bug-feature

git checkout feature
git merge bugfix/bug-feature

3. Nếu như trên nhánh bug feature đó đã phát triển thêm một feature khác và nhánh bug feature chưa được merge vào master:

**Hướng giải quyết**: Tạo một nhánh mới từ bug feature để sửa lỗi, sau đó merge vào nhánh bug feature

git checkout feature/bug-feature
git checkout -b bugfix/fix-bug-feature

git checkout feature/bug-feature
git merge bugfix/fix-bug-feature

**Hướng giải quyết**: Sau đó tiếp tục merge nhánh bug feature vào nhánh feature khác đã được tách ra trước đó để sửa lỗi nếu có phát sinh bug

git checkout feature/sub-feature
git merge feature/bug-feature

4. Nếu như có một feature khác đã xây dựng trên bug-feature và đã merge vào master

**Hướng giải quyết**: Vì đã được merge vào master, nên ta sẽ checkout 1 nhánh từ nhánh master để fix bug đấy, và sau khi fix xong sẽ merge lại vào master.

git checkout master
git checkout -b bugfix/fix-bug-feature

git checkout master
git merge bugfix/fix-bug-feature

**Hướng giải quyết**: Sau đó tiếp tục merge master vào nhánh feature khác đã được tách ra trước đó để sửa lỗi nếu có phát sinh bug

git checkout feature/sub-feature
git merge master
