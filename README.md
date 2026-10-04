# SecondProject
두 번째 실습을 진행하기 위한 저장소

새로운 브랜치를 생성하는 방식 등, 최대한 영상에서 소개된 명령어들을 이용하여 해결하는 방법들을 시도했지만 결국 실패하고 feature/div 브랜치에서 restore를 이용하여 파일을 복구한 새로운 커밋을 1개 만든 후 develop과 PR 하는 방식으로 해결하였습니다. (저녁 6시 부터 시작해서 새벽 3시까지 했어요!!)


첫 번째 시도 : add mul function 커밋으로 reset --hard 한 후 미리 파일 탐색기에서 빼놓은 div.py를 끼워넣어 커밋을 시도 -> 원격저장소에 커밋이 더 앞서 있어서 push가 거부됨 (이와 같은 문제는 gitTest repository에서 다룸) [README 참고](https://github.com/Roxxog/gitTest.git)

두 번째 시도 : add mul function 까지의 커밋을 가진 feature/div2 브랜치를 새로 만들어서 모든 파일이 들어간 상태로 커밋 후 PR -> 이미 develop의 커밋에 add div function 커밋으로 인해 feature/div2에 모든 파일이 있더라도 develop에서는 mul.py와 zero.py가 add div function 커밋 이후에 추가된 적이 없다고 판단함


위의 시도들의 문제 : reset을 이용하여 mul.py와 zero.py가 존재하게 만들더라도 add div function이 develop의 최근 커밋에 남아있을 경우 reset으로 파일을 복원하는 것은 소용없음. develop에 남길려면 이미 추가된 add div function 커밋 이후에 다시 +mul.py, +zero.py 상태가 되도록 만들어야 함.

restore를 사용할 경우 add div function 이후에 mul.py, zero.py가 다시 추가된 것으로 판단함. 그 상태에서 새로운 커밋을 만들면 develop에도 +mul.py +zero.py 변경 사항을 남길 수 있다.
