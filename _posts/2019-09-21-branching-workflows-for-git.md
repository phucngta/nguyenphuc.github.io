---
layout: post
published: false
title: Các quy trình phân nhánh khi sử dụng Git
---
# 4 quy trình phân nhánh cho Git

https://medium.com/@patrickporto/4-branching-workflows-for-git-30d0aaee7bf

Chúng ta sẽ đề cập đến các quy trình phân nhánh phổ biến nhất cho người dùng Git, để lựa chọn quy trình phù hợp cho chu kỳ phát triển của riêng bạn.

## Git flow
https://nvie.com/posts/a-successful-git-branching-model/
https://sandofsky.com/blog/git-workflow.html
https://danielkummer.github.io/git-flow-cheatsheet/index.vi_VN.html
https://buddy.works/blog/5-types-of-git-workflows


Git Flow là quy trình được biết đến nhiều nhất trong danh sách này. Được tạo bởi Vincent Driessen vào năm 2010 và nó dựa trên hai nhánh chính:
 
- master — nhánh này chứa production code. Tất cả code được phát triển sẽ được merge vào nhánh master này.
- develop — nhánh này chứa pre-production code. Khi các tính năng được phát triển xong sẽ merge vào nhánh develop này.

Trong chu kỳ phát triển, một loạt các nhánh hỗ trợ được sử dụng:
- `feature-*` - nhánh tính năng: được sử dụng để phát triển các tính năng mới cho các phiên bản sắp tới. Có thể tách từ nhánh `develop` và phải merge vào lại `develop` sau khi hoàn thành.
- `hotfix-*` - nhánh hotfix
- `release- *` - nhánh phát hành: hỗ trợ phát hành phiên bản mới. Chúng cho phép sửa nhiều lỗi nhỏ và chuẩn bị dữ liệu meta để phát hành.

### Ưu điểm:
- Đảm bảo trạng thái của các nhánh tại bất kỳ thời điểm nào trong vòng đời của dự án.
- Các nhánh được đặt tên một cách hệ thống, giúp việc đọc hiểu dễ hơn.
- Có công cụ [gitflow](https://github.com/nvie/gitflow) hỗ trợ và đều được hỗ trợ trên hầu hết các công cụ git.
- Mô hình lý tưởng khi cần có phát hành nhiều phiên bản.

### Nhược điểm
- Không thể truy vết lại được lịch sử Git.
- Việc phân nhánh `develop` / `master` nhiều khi dư thừa và khiến cho việc tích hợp CI/CD trở nên khó khăn hơn.
- Trong trường hợp chỉ có một version chính, thì mô hình này không tỏ ra không hiệu quả.

## GitHub Flow
Được tạo ra bởi GitHub vào năm 2011 và tuân theo 6 nguyên tắc sau:
1. Bất cứ thứ gì trên nhánh `master` đều có thể triển khai.
1. Để phát triển một tính năng mới, tạo một nhánh từ `master` và đặt tên nhánh mô tả cho tính năng đấy (ví dụ: new-oauth2-scopes)
1. Commit lên nhánh đó ở dưới local, và thường xuyên push code lên nhánh cùng tên trêns server.
1. Tạo một pull request khi bạn cần feedback, hỗ trợ, hoặc khi bạn nghĩ tính năng đã sẵn sàng để tích hợp.
1. Khi tính năng đã được review, có thể merge vào nhánh `master`. Sau khi merge nên deploy sớm nhất có thể.

### Ưu điểm
- Kết hợp tốt với quy trình CI/CD.
- Đơn giản hơn Git Flow.
- Giải pháp thích hợp trong trường hợp chỉ cần duy trì một phiên bản duy nhất.

### Nhược điểm
- Production code dễ mất ổn định.
- Không thích hợp khi cần các kế hoạch phát hành.
- Không giải quyết các vấn đề liên quan tới triển khai, môi trường, phát hành,...
- Không thích hợp khi cần phát hành nhiều phiên bản.
