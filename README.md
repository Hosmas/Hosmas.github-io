# Hosmas.github-io
오픈소스SW개론 1차 과제

# getopt
getopt 함수는 <unistd.h>에 정의된 함수로, "ls -l"과 같은 명령어에서 옵션을 찾아, 아스키 코드 값을 반환하는 함수이다.

함수의 원형은 다음과 같다.
`int getopt(int argc, char * const argv[], const char *optstring);`
argc는 인자의 개수, argv는 인자의 내용을 의미하며, optstring은 찾으려는 옵션의 문자열이다.
이 때, 명령어 옵션 뒤에 추가 인자가 필요할 경우에는 문자 뒤에 : 를 붙여야 한다.

예를 하나 들어보자면 -a, -b, -c 옵션이 있을 경우에는 'getopt(argc, argv, "abc");`과 같이 사용하면 된다.
만약, -a 옵션이 추가 인자를 필요로 한다면 :을 붙여서 'getopt(argc, argv, "a:bc");`과 같이 사용하는 것이 적절하다.
