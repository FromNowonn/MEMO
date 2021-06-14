# primary key Generate

> Field 'Column' doesn't have a default value 

## primary key로 지정해준 Column에 값에 초기값이 없어서 발생하는 문제.

<GenerationType.auto>를 사용하거나 DB상에서 primary key값의 변수를 auto_increment로 설정
 
DB를 이미 만들어놓은 상태이므로, DB상에서 auto_increment를 사용하여 key 값을 자동으로 증가시킴으로 오류 해결
 
 
