# 저장소 지침

- 루트에는 Node 프로젝트나 테스트 스크립트가 없습니다. 배포·빌드 기준은 `.github/workflows/publish.yml`이며, Quartz `97a2d05f80c4c50534959b1d0d41cc4b3895625e`와 Node 24를 사용합니다. 로컬 빌드는 workflow의 준비 단계를 재현한 뒤 Quartz 디렉터리에서 `npm ci`, `npm install --no-audit --no-fund @quartz-themes/default@^1.0.1`, `npx quartz build` 순으로 실행합니다.
- 공개 원본은 `posts/`이며, 하위 폴더는 목적별로 나뉩니다: `notes/`는 문서, `assets/`는 에셋, `bases/`는 Obsidian Base입니다. 이 구조를 유지하고, `posts/index.md`가 홈페이지임을 기억하세요. workflow가 `posts/` 전체를 Quartz `content/`로 복사하므로 비공개·미완성 자료는 `posts/` 밖에 두세요.
- `posts/bases/`의 Obsidian Base 필터는 vault 기준 `posts/` 경로를 사용합니다. workflow가 Quartz `content/`로 복사한 `.base` 파일에서 해당 접두어를 제거하므로, 로컬 빌드 재현 시 이 변환 단계도 포함하세요.
- 사이트 편집 시 Quartz 설정·테마·프론트매터·폰트 관련 세부 규칙은 `.opencode/skills/quartz-site/SKILL.md`를 따르세요.
