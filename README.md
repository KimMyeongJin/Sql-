--모든 필드
select * from emp;
-----------------------

-- 테이블 필드 목록 확인
desc emp;
-----------------------
--사원이름순(오름차순) 정렬
select empno,ename from emp order by ename ;
-----------------------
--사원이름순(내림차순) 정렬
select empno,ename from emp order by ename desc;
-----------------------
--사원이름(ename), 급여(sal), 부서코드(deptno)=>급여 오름차순
select ename, sal, deptno from emp order by deptno, sal desc;
-----------------------
--사원이름(ename), 급여(sal), 부서코드(deptno)=>급여 내림차순
select ename, sal, deptno from emp order by deptno, sal asc;
-----------------------
--이름(ename)/입사일자(hiredate)/부서코드(deptno) 부서코드 오름차순, 입사일자(hiredate) 오름차순
select ename, hiredate, deptno 
from emp 
order by deptno,hiredate;
-----------------------
-- emp 테이블의 job 검색하기
select distinct job from emp;
select all job from emp;
-----------------------
-- emp 테이블의 sal 내림차순 정렬하기
select * from emp order by sal desc;
-----------------------
-- emp 테이블의 sal 내림차순 정렬하기
select * from emp
    order by job, sal desc;
-----------------------
--emp 테이블의 job 오름차순, sal 내림차순 정렬하기
select ename 이름, job 직급, sal 급여 from emp
    order by job, sal desc;
-----------------------    
-- 급여가 100보다 많고 400보다 작은 직원 검색하기(급여 내림차순)
select * from emp
where sal > 100 and sal < 400
order by sal desc;
-----------------------
-- 급여가 100 이하 또는 400 이상의 직원 검색하기(급여 내림차순)
select * from emp 
  where not(sal > 100 and sal < 400)
  order by sal desc;
-----------------------  
--부서코드(deptno)가 30인 직원들
select * from emp where deptno = 30;
-----------------------
-- Ctrl+Enter, F9 현재 명령어 실행
-- F5 : 전체 명령어 실행
-----------------------
--부서코드가 10 또는 20 또는 30인 직원들
select distinct deptno from emp;
-----------------------
select * from emp 
where deptno=10 or deptno=20 or deptno =30;
-----------------------
select * from emp 
where deptno in(10,20,30);
-----------------------
-- 급여가 300~500인 직원들
select * from emp
where sal>=300 and sal<=500
order by sal;
-----------------------
select*from emp
    where sal between 300 and 500;
-----------------------

--성이 김씨들만 찾기
select ename from emp
    where ename like '김%';
-----------------------    

--이름안에 성이 들어가는 사람 찾기
select ename from emp 
    where ename like '%성%';
-----------------------    
--이름 중간에 철이 들어가는 사람 찾기
select ename from emp
    where ename like '_철%';
-----------------------
select ename from emp 
    where comm is null;
-----------------------  

--연봉계산
--null과의 연산결과는 null이 되므로 주의
select ename,sal,sal*12+comm as 연봉 from emp;
-----------------------

--nvl(A,B) A의 값이 null이면 B, null이 아니면 A
select ename,sal,sal*12+nvl(comm,0) as 연봉 from emp;
-----------------------

--각 사람의 급여를 검색해서 '누구누구의 급여는 얼마입니다'로 컬럼명을 만들어서 출력하기
select ename || '의 급여는' || sal || '입니다' from emp;
-----------------------

-- 괄호(): 연산자 우선순위보다 우선함.
-- (비교예제)
-- 급여가 200~300인 직원
select empno, sal from emp
where sal > 200 and sal < 300 order by sal;
-- 급여가 200 이하 또는 300이상인 직원
select empno, sal from emp
    where not(sal > 200 and sal< 300)
    order by sal;
-- 급여가 200 이하인 직원
select empno, sal from emp
    where not sal > 200 and sal < 300
    order by sal;
-----------------------    
-- 실습문제
-- 2005년 1월 1일 이전 입사자
select ename, hiredate, deptno from emp
    where hiredate< '2005-01-01'
    order by hiredate;
-----------------------    
-- 부서코드가 20 또는 30인 직원들
select ename,job,deptno
from emp
where deptno in (20,30)
order by ename;
-----------------------
