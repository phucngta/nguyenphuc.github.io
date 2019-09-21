---
layout: post
published: false
title: ''
---
# 4 quy trình phân nhánh cho Git

https://medium.com/@patrickporto/4-branching-workflows-for-git-30d0aaee7bf

In this article, we will cover the most popular branching workflows for Git users, so you can decide which fits better to your own development cycle.


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
- `feature-*` - các nhánh tính năng được sử dụng để phát triển các tính năng mới cho các phiên bản sắp tới. Có thể tách từ nhánh `develop` và phải merge vào lại `develop` sau khi hoàn thành.
- `hotfix-*` - Các nhánh hotfix là cần thiết để hành động ngay lập tức khi có trạng thái không mong muốn của chủ. Có thể tách ra khỏi chủ và phải hợp nhất thành chủ và phát triển.
- `release- *` - chi nhánh phát hành hỗ trợ chuẩn bị phát hành sản xuất mới. Chúng cho phép sửa nhiều lỗi nhỏ và chuẩn bị dữ liệu meta để phát hành. Có thể tách ra khỏi sự phát triển và phải hợp nhất thành chủ và phát triển.

During the development cycle, a variety of supporting branches are used:
feature-* — feature branches are used to develop new features for the upcoming releases. May branch off from develop and must merge into develop.
hotfix-* — hotfix branches are necessary to act immediately upon an undesired status of master. May branch off from master and must merge into master anddevelop.
release-* — release branches support preparation of a new production release. They allow many minor bug to be fixed and preparation of meta-data for a release. May branch off from develop and must merge into master anddevelop.
Advantages
Ensures a clean state of branches at any given moment in the life cycle of project
The branches naming follows a systematic pattern making it easier to comprehend
It has extensions and support on most used git tools
It is ideal when there it needs to be multiple version in production
Disadvantages
The Git history becomes unreadable
The master/develop split is considered redundant and makes the Continuous Delivery and the Continuos Integration harder
It isn’t recommended when it need to maintain single version in production


