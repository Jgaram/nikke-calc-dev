# publish

public repo(`nikke-calc`)에 현재 앱 상태 배포.

## 순서

### 1. deploy 폴더 확인

`/c/tmp/nikke-deploy` 없으면 clone:
```
git clone https://github.com/Jgaram/nikke-calc.git /c/tmp/nikke-deploy
```

### 2. 마지막 publish 시점 확인

```
cd /c/tmp/nikke-deploy && git log -1 --format="%ci"
```

### 3. 이후 dev 커밋 메시지 수집

```
git log --oneline --after="<마지막 publish 시간>"
```

수집한 커밋 메시지 보여주고 publish 커밋 메시지 초안 제안. 승인 없이 진행 금지.

### 3. 파일 동기화

```
cp -r app.py ui/ calculator/ data/ image/ requirements.txt /c/tmp/nikke-deploy/
```

### 4. 커밋 및 push

```
cd /c/tmp/nikke-deploy
git add .
git commit -m "<승인된 메시지>"
git push origin master
```

push 결과 확인·보고. 실패 시 오류·원인 설명.

## 참고

- public repo는 LFS 미사용.
- `/c/tmp/nikke-deploy` 없으면 초기 배포 절차 필요 안내.
