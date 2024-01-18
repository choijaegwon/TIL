# 하나의 View Controller 코드에서 여러 TableView Controller 역할을 해야 할 경우 어떻게 구분해서 구현해야 하는지 설명하시오.

- func tableView(_ tableView: UITableView, cellForRowAt indexPath: IndexPath) -> UITableViewCell 에서 파라미터로 받는 tableView 를 객체 비교를 통해 구분한다.
- 테이블 뷰의 Tag 를 등록, 비교해서 구분한다.
