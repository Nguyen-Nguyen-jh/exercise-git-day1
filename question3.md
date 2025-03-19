### If someone accidentally merges a feature (feature/delete-user) onto production and has a list of commitId ended with (0492978, fc9348c, k101100), then another commit (a1fsas8) is added on top of the production branch. How do we remove that merged feature?

1. Dùng git revert:

**Giải thích**: sử dụng git revert để tạo một commit mới hoàn tác các thay đổi từ các commit sai, và vẫn giữ nguyên các commit trong quá khứ ==> nên chọn revert vì nó không làm thay đổi lịch sử commit, nếu đang làm việc trên một nhánh được chia sẻ giữa nhiều người, revert là sự lựa chọn phù hợp.

**Ví dụ**:

feature/user : A -> B -> C -> D -> E
git revert commitId-D

==> feature/user : A -> B -> C -> D -> E -> D'

2. Sử dụng git reset:

**Giải thích**: Sử dụng git reset khi muốn xóa hoàn toàn các commit không mong muốn khỏi lịch sử và quay lại trạng thái trước khi các commit được hợp nhất ==> Chọn revert nếu muốn loại bỏ các commit không mong muốn mà không để lại dấu vết trong lịch sử, nhưng phải lưu ý các commit đã được push lên remote chưa vì có thể gây xung đột với người khác

**Ví dụ**:

feature/user : A -> B -> C -> D -> E
git reset --hard commitId-C

==> feature/user : A -> B -> C

### Kết luận: Nếu trong môi trường làm việc nhóm thì sử dụng git revert thường là lựa chọn an toàn hơn, vì nó không thay đổi lịch sử commit đã chia sẻ và giúp tránh các xung đột với các thành viên trong team.
