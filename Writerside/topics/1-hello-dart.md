# 1. Hello, Dart

## 000.  create dart project
- 프로젝트생성 = Terminal 열기 - dart create first_project(프로젝트명)
    ```bash
    $dart create "프로젝트명"
    ```
- Finder - Go - Home 클릭 후, first_project 폴더 안에 Bin 폴더 - first_project.dart 파일 확인
- 생성한 파일 열어주기 (VisualStudioCode) = File - Open Folder - 파일 선택 후 (first_project) Open 클릭
- Extensions 클릭 - Dart 설치
- Extension = 다양한(서버,다트언어,개발,JavaETC..) 프로그래머들이 Visual Studio Code(VSC)를 사용하는데 각 프로그래머들에게 맞게끔 업데이트 해주는Tool
- Dart Extension 사용방법 = View - Command palette(Shift+Command+P) 검색 창에 'dart:NewProject' 검색 - Simple Console Application 클릭
- 프로젝트 저장해 줄 Folder 선택 후 저장 - 프로젝트명(first_project) 적고 저장!

## 001. run_application
- Dart 패키지 이용하여 Debug 실행해 주기.
- Print('...'); - 작은따옴표 안에 글씨가 찍힌다.
- Debug Shortcut
    1. (F5) - Start debug
    2. Control + F5 - run without debug
- `;`세미콜론 = 코드가 끝나는 지점에 넣어주는 기호
- `{}`Body 구성시 사용 (코드구역을나누어주는기능)
- `()`데이터를 전달하고 받을 때 사용한다.

## 002. print_function
- Print 함수를 통해 내가 한 코딩이 잘됐는지 안됐는지 확인하기 위해 사용!
    - 어떻게 작동하는지 이해하기보다는 `print`함수를 통해 체크할 데이터를 넣어서 콘솔에 보여준다.