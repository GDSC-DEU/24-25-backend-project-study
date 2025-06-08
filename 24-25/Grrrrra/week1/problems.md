## 1. URL 작성
> 적혀 있는 동작에 따른 API의 URL을 REST 규칙에 맞춰 작성해 보세요. 이 서비스는 온라인 쇼핑몰 서비스고, 상품을 구매하는 소비자와 상품을 등록하는 관리자 2 종류가 있습니다.
>
> API를 작성할 때는 `[메소드] URL` 형식으로 작성해 주세요!

- 모든 상품 목록을 조회하는 API : `GET/products`
- 특정 카테고리(id: {category_id})의 상품 목록을 조회하는 API : `GET /category/123/products`
- id가 {product_id}인 상품의 상세 정보를 조회하는 API : `GET/products/123`
- 새로운 상품을 등록하는 API (관리자용) :`POST/products`
- id가 {product_id}인 상품 정보를 수정하는 API (관리자용) : `PUT/products/123`

## 2. REST API 설계 평가
다음 API 설계가 REST 원칙에 맞는지 평가하고, 맞지 않다면 올바르게 수정하세요.

- 사용자 목록 조회: `GET /getUsers`
    ```
    올바르지 않음.

    REST 원칙에 따라, URL 경로에는 동사를 배제하고, 가능한 한 명사형 단어만 사용해야 함. GET이라는 동작은 이미 HTTP 메소드를 통해 나타내었으므로, 올바른 URL은
    
    GET /users
    ```

- 특정 사용자 조회: `GET /findUserById/123`
    ```
  올바르지 않음
  REST 원칙에 따라, 동사(findUserBy)를 배제하고, 가능한 한 명사형 단어만 사용하기 권장함, 특정 리소스 접근 시에는 해당 리소스의 ID 경로를 포함. Get이라는 동작이 find를 의미하는데 이미 HTTP 메소드를 통해 나타난 것, 올바른 URL은
  
  GET/users/123
    ```
- 새 사용자 등록: `POST /insertUser`
    ```
  올바르지 않음
  REST 원칙에 따라, 동사 배제,명사를 복수형으로 기제하도록 지향(users로 복수형) , 가능한 한 명사형 단어만 사용(insert는 동사), POST의 의미가 insert로 HTTP 메소드에 이미 나타나 있음, 올바른 URL

  POST/users
    ```
- 사용자 정보 수정: `POST /updateUser/123`
    ```
  올바르지 않음
  REST 원칙에 따라, 동사 배제(update X) 명사를 복수형 지향, 수정은 PUT 메서드를 사용해야한다. 부분 부정의 내용이 기제된다면 PATCH 사용, PATCH,PUT의 동작은 이미 HTTP 메소드를 통해 나타내었으므로, 올바른 URL은
  
  PUT/users/123
  PATCH/users/123
    ```
- 사용자 삭제: `GET /users/delete/123`
    ```
  올바르지 않음
  1. 삭제할땐 DELETE 사용
  2. URL 주소에 들어간 동사는 제외해야함(delete)
  3. DELETE라는 동작은 HTTP 메소드를 통해 나타내었으므로, 올바른 URL은
  
  DELETE/users/123
    ```

## 3: Path Parameter와 Query Parameter 구분
다음 URL을 보고, 질문에 답하세요.
https://api.library.com/v2/libraries/1316754/books/978-0321127426/reviews?rating=5&page=2

- 위 URL에서 Path Parmaeter 2가지를 찾고, 이 Path Parameter를 통해 찾고자 하는 정보가 무엇인지 적어 주십시오.
    - 파라미터 1:/libraries/1316754
    - 파라미터 2:/books/978-0321127426
    - 이 URL이 나타내는 정보: libraries의 식별코드는 1316754이고, books의 식별코드는 978-0321127426이 된다.
- 위 URL에서 Query Parameter를 찾고, 만약 리뷰 종류 중 일반 사용자 리뷰만 찾고 싶다고 가정할 때, URL의 가장 뒤에 어떤 URL이 추가되어야 하는지 작성해 주세요.
    - 파라미터 1: rating=5
    - 파라미터 2: page=2
    - 추가되어야 하는 URL 문자열: /reviews?rating=5&page=2&type=user

## 4. HTTP 상태코드 활용
다음 각 상황에 가장 적합한 HTTP 상태 코드는 무엇인가요?

- 요청이 성공적으로 처리됨 : 200 OK
- 새 리소스가 성공적으로 생성됨 :  201 Created
- 요청한 리소스를 찾을 수 없음 : 404 Not Found
- 인증이 필요한 리소스에 접근 시도 : 403 Forbidden
- 클라이언트의 요청이 잘못된 형식임 : 400 Bad Request

## 5. Path/Query 파라미터를 응용한 설계
영화 스트리밍 플랫폼의 영화 검색 API를 설계한다고 가정할 때, 다음 조건을 모두 충족하는 검색을 위한 URL을 설계하세요.

> tip: x-www-form-urlencoded 형식에서 배열(같은 키의 여러 데이터)를 표현할 때는, 동일한 키를 여러 번 반복해서 제공합니다.
> 
> ex: `array-val=1&array-val=2&array-val=3` << `array-val [1,2,3]`

- 장르: 액션, SF
- 상영 시간(time): 90분(minimum) ~ 150분(maximum)
- 개봉 연도(year): 2010년 이후(2010)
- 배우(actor): 톰 크루즈, 스칼렛 요한슨
- 평점(review): 7.5점 이상(7.5)
- 정렬 기준(std-sort): 인기도 높은 순(desc)
- 페이지(page): 3페이지, 페이지당 15개 항목
```
https://api.movie.stream.service.com/v2/movie?
genre=action,sci-fi&
time_min=90&
time_max=150&
year=2010&
actor=Tom,scarlett&
review=7.5&
page_size=15
sort=popularity.desc&
page=3&

```
