# publish

public repo(`nikke-calc`)에 현재 앱 상태를 배포한다.

## 실행 순서

### 1. deploy 폴더 확인

`/c/tmp/nikke-deploy`가 없으면 먼저 clone한다:
```
git clone https://github.com/hhjj7210-code/nikke-calc.git /c/tmp/nikke-deploy
```

### 2. 마지막 publish 시점 확인

`/c/tmp/nikke-deploy`에서 마지막 커밋 시간을 확인한다:
```
cd /c/tmp/nikke-deploy && git log -1 --format="%ci"
```

### 3. 그 이후 dev 커밋 메시지 수집

main 프로젝트에서 그 시점 이후의 커밋 메시지를 수집한다:
```
git log --oneline --after="<마지막 publish 시간>"
```

수집한 커밋 메시지들을 보여주고, 이를 바탕으로 publish 커밋 메시지 초안을 만들어 유저에게 제안한다. 승인 없이 진행하지 않는다.

### 4. 파일 동기화

변경 대상 폴더/파일을 `/c/tmp/nikke-deploy`에 통째로 복사한다:
```
cp -r app.py ui/ calculator/ data/ image/ requirements.txt /c/tmp/nikke-deploy/
```

### 5. 커밋 및 push

```
cd /c/tmp/nikke-deploy
git add .
git commit -m "<승인된 메시지>"
git push origin master
```

push 결과를 확인하고 성공 여부를 알린다. 실패 시 오류 내용과 원인을 설명한다.

## 참고

- public repo는 LFS를 사용하지 않는다.
- `/c/tmp/nikke-deploy`가 없으면 초기 배포 절차가 필요하다고 알린다.
