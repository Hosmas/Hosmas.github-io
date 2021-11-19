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
 
getopts는 while 구문과 같이 사용하기도 한다.
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


이 때, 명령어 옵션 뒤에 추가 인자가 필요할 경우에는 문자 뒤에 : 를 붙여야 한다.
만약 위의 코드에서 -a 옵션에 추가 인자가 필요할 경우에는 a 뒤에 :를 붙여서 다음과 같이 변경해야 한다.
```
while getopts a:bc opts; do
        case $opts in
        ...
        esac
done
```
