+++
title = "설치하기"
description = "Goyo를 설치하고 시작하는 방법을 알아보세요."
weight = 1
sort_by = "weight"

[extra]
+++

Goyo 테마는 Zola에서 동작하는 테마입니다. 문서를 사용하기 위해선 Zola 설치가 필요합니다. 여러 OS에 대해 아래와 같이 간단한 방법으로 설치할 수 있습니다.

```bash
# macOS Example
brew install zola
```

자세한 내용은 Zola 공식 웹 페이지의 [설치 문서](https://www.getzola.org/documentation/getting-started/installation/)를 참고해주세요.

zola를 설치했다면 아래와 같이 zola app을 생성합니다.

```bash
zola init your-docs
cd docs
```

그리고 이제 `zola serve` 명령을 통해 웹 페이지를 구동할 수 있고 `http://localhost:1111` 로 접근하여 확인할 수 있습니다.

## Install Goyo Theme

Zola에서 테마를 설치하는 가장 쉬운 방법은 zola 프로젝트의 themes 하위 디렉토리에 clone 또는 submodule로 연결하는 방법입니다.

Clone 예시

```bash
git clone https://github.com/hahwul/goyo themes/goyo
```

Submodule 예시

```bash
git submodule add https://github.com/hahwul/goyo themes/goyo
```

## Goyo 테마 업데이트

Goyo 테마를 최신 버전으로 업데이트하려면 아래 방법을 사용할 수 있습니다.

### clone으로 설치한 경우

저장소를 직접 clone하여 Goyo를 설치한 경우, 다음 명령으로 업데이트할 수 있습니다:

```bash
cd themes/goyo
git pull origin main
```

이 명령은 main 브랜치에서 최신 변경 사항을 가져와 병합합니다.

### submodule로 설치한 경우

Goyo를 git submodule로 설치한 경우, 다음 명령으로 업데이트할 수 있습니다:

```bash
git submodule update --remote themes/goyo
```

또는 모든 submodule을 포괄적으로 업데이트하려면:

```bash
git submodule sync
git submodule update --remote
```

submodule 업데이트 후, 변경 사항을 저장소에 커밋합니다:

```bash
git add themes/goyo
git commit -m "Update Goyo theme to latest version"
git push
```

최신 Goyo 테마의 기능과 버그 수정 사항을 적용할 수 있습니다.

### GitHub Actions를 통한 자동 업데이트

GitHub에 호스팅된 프로젝트의 경우, GitHub Actions를 사용하여 테마 업데이트를 자동화할 수 있습니다. 이를 통해 새로운 버전의 Goyo가 출시될 때마다 주기적으로 Pull Request가 생성됩니다.

문서 저장소에 `.github/workflows/update-goyo-theme.yml` 파일을 생성합니다:

```yaml
name: Update Goyo Theme

on:
  schedule:
    # 매주 월요일 오전 9시(UTC)에 실행
    - cron: "0 9 * * 1"
  workflow_dispatch: # 수동 실행 허용

env:
  GIT_USER_NAME: "github-actions[bot]"
  GIT_USER_EMAIL: "github-actions[bot]@users.noreply.github.com"
  THEME_PATH: "themes/goyo"

jobs:
  update-theme:
    runs-on: ubuntu-latest
    permissions:
      contents: write
      pull-requests: write

    steps:
      - name: Checkout repository
        uses: actions/checkout@v4
        with:
          submodules: true
          token: ${{ secrets.GITHUB_TOKEN }}

      - name: Update Goyo submodule
        id: update
        run: |
          git config user.name "${{ env.GIT_USER_NAME }}"
          git config user.email "${{ env.GIT_USER_EMAIL }}"

          # 현재 커밋 해시 가져오기
          OLD_COMMIT=$(git rev-parse HEAD:${{ env.THEME_PATH }})

          # submodule을 최신 버전으로 업데이트
          git submodule update --remote ${{ env.THEME_PATH }}
          git add ${{ env.THEME_PATH }}

          # 새 커밋 해시 가져오기
          NEW_COMMIT=$(git --git-dir=${{ env.THEME_PATH }}/.git rev-parse HEAD)

          # 변경 사항 확인
          if [ "$OLD_COMMIT" != "$NEW_COMMIT" ]; then
            echo "updated=true" >> $GITHUB_OUTPUT
            echo "old_commit=$OLD_COMMIT" >> $GITHUB_OUTPUT
            echo "new_commit=$NEW_COMMIT" >> $GITHUB_OUTPUT
          else
            echo "updated=false" >> $GITHUB_OUTPUT
          fi

      - name: Create Pull Request
        if: steps.update.outputs.updated == 'true'
        uses: peter-evans/create-pull-request@v6
        with:
          token: ${{ secrets.GITHUB_TOKEN }}
          commit-message: "Update Goyo theme to latest version"
          title: "Goyo 테마 업데이트"
          body: |
            이 PR은 Goyo 테마를 최신 버전으로 업데이트합니다.

            **변경 사항:** ${{ steps.update.outputs.old_commit }} → ${{ steps.update.outputs.new_commit }}

            새로운 기능에 대한 자세한 내용은 [Goyo 변경 로그](https://github.com/hahwul/goyo/releases)를 참조하세요.

            ---
            *이 PR은 Update Goyo Theme 워크플로우에 의해 자동으로 생성되었습니다.*
          branch: update-goyo-theme
          delete-branch: true
          labels: dependencies, documentation
```

워크플로우를 커스터마이징할 수 있습니다:
- **스케줄**: `cron` 표현식을 수정 (예: `'0 9 * * *'` 매일, `'0 9 1 * *'` 매월)
- **수동 실행**: 저장소의 Actions 탭에서 수동으로 실행 가능
- **Git 사용자**: `env` 섹션에서 `GIT_USER_NAME`과 `GIT_USER_EMAIL`을 원하는 계정으로 변경
- **테마 경로**: 테마가 다른 위치에 설치된 경우 `THEME_PATH`를 수정
- 저장소 설정에서 Actions가 Pull Request를 생성할 수 있도록 허용 필요 (Settings → Actions → General → Workflow permissions)

## Set theme in config.toml

마지막 단계입니다. config.toml에서 theme를 작성하여 goyo 테마를 사용하도록 합니다.


```toml
title = "Your App"
theme = "goyo"
```

이제 zola 실행 시 goyo 테마로 동작합니다.

```bash
zola serve
```

다만 아직 컨텐츠가 없기 떄문에 영롱한 색상의 빈 페이지만 확인됩니다. 다음 문서에서 첫 페이지를 만들어봅니다.
