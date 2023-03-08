# 저장소 설명
RealMySQL 책 공부 내용 저장

# 실습 환경 구성
### Test DB
`Employees` Test DB를 사용합니다. 
- https://dev.mysql.com/doc/employee/en/employees-installation.html
- https://github.com/datacharmer/test_db

### Test DB 셋업
1. Docker 실행
   ```
   docker run -it -d -p 3306:3306 --name mysql-employees -e MYSQL_ROOT_PASSWORD=secret -v {my-volume-folder}:/var/lib/mysql amd64/mysql:5.7.40
   docker run -it -d -p 3306:3306 --name mysql-employees -e MYSQL_ROOT_PASSWORD=secret -v {my-volume-folder}:/var/lib/mysql amd64/mysql:5.7.40 --explicit_defaults_for_timestamp
   ```
2. DB 파일을 Docker 볼륨 경로로 복사
   - dump를 포함한 전체 파일을 복사해야한다
3. Docker 접속 및 파일을 복사한 위치로 이동
   ```
   docker exec -it {container name} bash
   ```
4. 파일 설치
   ```
   mysql -u root -p < employees.sql
   ```
5. 설치 결과 확인
   ```sql
   show tables;

    +----------------------+
    | Tables_in_employees  |
    +----------------------+
    | current_dept_emp     |
    | departments          |
    | dept_emp             |
    | dept_emp_latest_date |
    | dept_manager         |
    | employees            |
    | salaries             |
    | titles               |
    +----------------------+
   ```