# Hosmas.github-io
오픈소스SW개론 1차 과제

# getopt와 getopts
getopt는 "ls -l"과 같은 명령어 문자열에서 추가로 사용하는 옵션을 처리하기 위한 명령어이다.

getopt를 이용해 -a, -b, -c와 같이 -가 하나인 short option들을 처리하고 싶다면 -o 옵션을 붙여서 다음과 같이 사용할 수 있다.

`getopt -o abc`

 --help, --path 같은 long option들은 아래와 같이 -l 옵션을 붙여서 사용하면 된다.
 
 `getopt -l help,path`
 
 이 때, 어떤 옵션이 뒤에 추가적인 인자를 필요로 한다면 뒤에 :를 붙여주어야 한다.
 예를 들어 -a, -b, -c 옵션 중에 -a가 추가 인자를 받을 경우에는 아래처럼 표현해야 한다.
 
 `getopt -o a:bc`
 
|옵션|내용|사용법|
|---|-----|-------|
|-o|short option을 처리|getopt -o abc|
|-l|long option을 처리|getopt -l help,path|

아래처럼 while문과 함께 getopt를 사용한다면 쉽게 옵션을 처리할 수 있다.
```
while getopts abc opts; do
        case $opts in
        a)
        ...
        b)
        ...
        c)
        ...
        esac
done
```

# sed
sed 명령어는 텍스트를 변환하거나 필터링하여 출력하는 스트림 편집기이며 원본 파일은 바꾸지 않고 출력 결과만을 변화시키는 특징이 있다.

`sed [ 옵션 ] '명령어' 파일명`

![image](https://user-images.githubusercontent.com/94365974/142720825-4bf2cc06-3738-4427-b70e-b62758403e6d.png)

![image](https://user-images.githubusercontent.com/94365974/142720837-b282c09f-b857-44bb-93e2-e7873a74ddcf.png)

출처: https://tar-cvzf-studybackup-tar-gz.tistory.com/34


예를 들어, test.txt라는 파일에서 첫 1행부터 마지막 10행까지 출력하고 싶다면 출력 명령어 p를 이용하여

`sed '1, 10p' test.txt`처럼 사용하면 된다.

출력을 생략하고 파일 안의 apple을 orange로 바꾸고 그 줄만 출력하고 싶다면 -n 옵션과 s, p 명령어를 사용하면 된다.
`sed -n 's/apple/orrange/p' test.txt`

아래 표의 메타문자를 이용하면 sed를 사용할 때 더 간단하게 표현할 수 있다.

![image](https://user-images.githubusercontent.com/94365974/142721549-4af8c79e-2689-4c91-b79e-4e4673a95c07.png)

apple과 Apple을 파일에서 전부 삭제하려면 메타문제라를 이용하지 않을 경우

```
sed 'apple/d' test.txt
sed 'Apple/d' test.txt
```
처럼 sed를 두 번 써야 하지만, []를 이용하면, `sed '[Aa]pple/d' test.txt`로 간단하게 사용할 수 있다.

#awk
awk는 데이터가 여러 행 있는 텍스트 파일을 처리할 때 유용한 명령어로, 간단한 연산과 데이터 조작이 가능하다.

`awk '명령어' 파일명`

특정 문자로 데이터를 구분하여 필드에 저장한다.
test.txt 파일의 내용이 다음과 같다고 하자.

```
A 1 2 3 
B 4 5 6
C 7 8 9
```

`awk '{print $1 $2}' test.txt`를 했을 때 공백으로 구분하여 필드 1에는 (A, B, C) 필드 2에는 (1, 4, 7)의 출력은

```
//출력
A 1
B 4
C 7
```

awk 명령어를 통해 사칙연산이 가능하기 때문에 `awk '{print $2+$3}' test.txt`를 할 경우 출력은

```
//출력
3
9
15
```

-F 옵션을 이용하여, 공백이 아닌 다른 문자로도 구분이 가능하다.
예를 들어 test.txt 파일의 내용이

```
A,1,2,3 
B,4,5,6
C,7,8,9
```
로 변경되었을 경우

`awk -F, '{print $1 $2}' test.txt`를 해서 똑같은 출력값을 얻을 수 있다.

```
//출력
A 1
B 4
C 7
```
