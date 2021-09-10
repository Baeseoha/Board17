# 발견 문제점
## 1. 실행시 에러 발생

> 원인 : WriteDAO.xml 에서 view.do 페이지의 경로를 잘못 기재
```java
// 수정 
<!-- view.do -->
	<select id="selectByUid" resultType="com.lec.spring.WriteDTO">  
=> <select id="selectByUid" resultType="com.lec.spring.domain.WriteDTO">
```

## 2. '수정' 시 내용이 안보이는 증상 발생

> **원인** : updateOk.jsp 에서 update uid 값을 안불러옴 

``` html
// 수정 
location.href = "view.do?uid=${uid}";   
=>location.href = "view.do?uid=${param.uid}"; 
``` 

## 2. '글 삭제' 시 내용이 안보이는 상황 발생 

> **원인** : WriteDAO.xml 에서 삭제시 불러오는 uid 경로를 잘못 기재

``` html
// 수정 
<delete id="deleteByUid" flushCache="true">
		DELETE FROM test_write WHERE uid = #{uid}
</delete>  
=><delete id="deleteByUid" flushCache="true">
		DELETE FROM test_write WHERE wr_uid = #{uid}
</delete>
``` 




