### If someone accidentally merges a feature (feature/delete-user) onto production and has a list of commitId ended with (0492978, fc9348c, k101100), then another commit (a1fsas8) is added on top of the production branch. How do we remove that merged feature?

1. Dùng git revert:

**Giải thích**: sử dụng git revert để tạo một commit mới hoàn tác các thay đổi từ các commit sai, và vẫn giữ nguyên các commit trong quá khứ

**Ví dụ**:

feature/user : A -> B -> C -> D -> E
git revert commitId-D

==> feature/user : A -> B -> C -> D -> E -> D'

2. Sử dụng git reset:

**Giải thích**: Sử dụng git reset khi muốn xóa hoàn toàn các commit không mong muốn khỏi lịch sử và quay lại trạng thái trước khi các commit được hợp nhất

**Ví dụ**:

feature/user : A -> B -> C -> D -> E
git reset --hard commitId-C

==> feature/user : A -> B -> C
