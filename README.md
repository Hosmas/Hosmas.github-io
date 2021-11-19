# Hosmas.github-io
오픈소스SW개론 1차 과제

# getopts
getopts는 "ls -l"과 같은 명령어 문자열에서 옵션을 찾을 때 사용하는 명령어이다.
```
while getopts abc opts; do
        case $opts in
        ...
        esac
done
```과 같은 방식으로 사용할 수 있다.

이 때, 명령어 옵션 뒤에 추가 인자가 필요할 경우에는 문자 뒤에 : 를 붙여야 한다.

