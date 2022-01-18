
# Error

## Keyboard shortcut 오류

- 일부 커맨드가 적용되지 않는 다면 `한/영`에 대한 오류일 수 있다.
- 우측 하단의 한영설정을 `Microsoft 입력기` 로 지정해준다.

## PHP Undefined variables 오류

- 원인 : Global 변수에 대한 Inspection Scope 문제
- 해결 : `Settings` > `Editor` > `inspections` > `PHP` > `Undefined symbols` > `Undefined variable` > `Options` > Check `Search for variable's definition outside the current file`
- 참고 : [PhpStorm Community](https://intellij-support.jetbrains.com/hc/en-us/community/posts/207069775-Undefined-variables-in-included-files-in-php)