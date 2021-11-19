# Hosmas.github-io
오픈소스SW개론 1차 과제

# getopt
getopt 함수는 <unistd.h>에 정의된 함수로, "ls -l"과 같은 명령어에서 옵션을 찾아, 아스키 코드 값을 반환하는 함수이다.

함수의 원형은 다음과 같다.
```
int getopt(int argc, char * const argv[], const char *optstring);
```

