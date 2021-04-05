## Merge vs Rebase

Merge 이든 Rebase 든 둘 다 합치는 관점에서는 서로 다를 게 없습니다.
하지만 Rebase가 좀 더 깨끗한 히스토리를 만듭니다.
Rebase 한 브랜치의 LOG를 살펴보면 히스토리가 선형이며, 일을 병렬로 동시에 진행해도 Rebase하고 나면 모든 작업이 차례대로 수행된 것처럼 보입니다.

`그래서 Rebase는 커밋을 깔끔하게 적용하고 싶을 때 사용하면 유용합니다.`

Rebase를 하든지, Merge를 하든지 최종 결과물은 같고 커밋 히스토리만 다르다는 것이 중요합니다.
Rebase의 경우는 브랜치의 변경사항을 순서대로 다른 브랜치에 적용하면서 합치고 Merge의 경우는 두 브랜치의 최종결과만을 가지고 합칩니다.

### 주의사항

로컬 브랜치에서 작업할 때는 히스토리를 정리하기 위해서 Rebase 할 수도 있지만, `리모트 등 어딘가에 Push로 내보낸 커밋에 대해서는 절대 Rebase 하지 말아야 합니다. `
rebase한 내용을 다른 사람이 git pull로 당겨 받으면 엄청난 conflict를 만날 수 있기 때문입니다. 
그러므로 local에서 작업하고 origin으로 push하기 전에 깔끔하게 커밋을 정리하는 차원에서 이용하는 것이 좋습니다.


## Rebase -i

`$ git rebase -i `
`-i`는 `--interactive`의 약어로 말그대로 git rebase 명령어를 대화형으로 실행하겠다는 의미입니다.



ex ) `git rebase -i HEAD~3`을 입력하면 HEAD~3부터 HEAD까지의 커밋들이 출력됩니다. 

![image](https://user-images.githubusercontent.com/46394672/113536369-eaed5e80-9610-11eb-9527-ff389910a2e4.png)


### pick
pick 은 커밋을 사용하겠다는 의미입니다. 이를 이용해서 커밋의 순서를 바꿀 수도 있고, 커밋의 해쉬값을 이용해 특정 커밋을 가져올 수도 있습니다.

### reword
reword 는 커밋 메시지를 변경하는 명령어입니다.

### edit
앞서 설명한 reword는 커밋 메시지만 변경하는 명령어였다면, edit 은 커밋 메시지 뿐만 아니라 커밋의 작업 내용도 변경할 수 있는 명령어입니다.

### squash
squash 은 해당 커밋을 이전 커밋과 합치는 명령어입니다.

### fixup
fixup 은 squash 와 동일하게 해당 커밋을 이전 커밋과 합치는 명령어지만, 커밋 메시지는 합치지 않습니다. 결과적으로 이전 커밋 메시지만 남게 됩니다.

### exec
exec 를 이용하면, 각각의 커밋이 적용된 후 실행할 shell 명령어를 지정할 수 있습니다.

### drop
drop 은 커밋 히스토리에서 커밋을 삭제하는 명령어입니다.



참고
------------
https://jupiny.com/2018/05/07/git-rebase-i-option/

https://flyingsquirrel.medium.com/git-rebase-%ED%95%98%EB%8A%94-%EB%B0%A9%EB%B2%95-ce6816fa859d

https://beomseok95.tistory.com/231

