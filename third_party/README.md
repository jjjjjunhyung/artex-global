# third_party

한국어 · [English](#english)

이 디렉터리에는 상류 원저작자의 **개인 저장소에서만 받을 수 있는** 의존성을 그대로 복사해 둡니다.
원본 저장소가 사라지거나 내용이 바뀌어도 이 저장소만으로 빌드가 되게 하려는 것입니다.
일반 공개 라이브러리(`golang.org/x/...`, `pgx` 등)는 여기에 두지 않고 평소처럼 Go 모듈로 받습니다.

## norma

| 항목 | 값 |
| --- | --- |
| 모듈 | `github.com/Autumn-27/norma` |
| 버전 | `v0.4.3` (태그 커밋 `320ae32`, 2026-09-29) |
| 출처 | <https://github.com/Autumn-27/norma> 의 `v0.4.3` 태그를 `git archive` 로 내보낸 것 |
| 라이선스 | Apache-2.0 ([norma/LICENSE](norma/LICENSE)) |
| 연결 | 루트 `go.mod` 의 `replace github.com/Autumn-27/norma => ./third_party/norma` |

- **수정하지 않았습니다.** `LICENSE` 를 뺀 210개 파일은 태그 내용과 바이트 단위로 같습니다.
  이전에 `go.sum` 이 고정하던 모듈 해시(`h1:DnmOhJPL6OZSMnCVYO5Ujh4yVINuDarEickVi9jx1hI=`)와
  이 파일들로 다시 계산한 해시가 일치하는 것을 확인했습니다.
- **`LICENSE` 만 덧붙였습니다.** `v0.4.3` 태그에는 라이선스 파일이 없고, 원저작자가 2026-10-11
  커밋 `52f17dd` 에서 저장소에 Apache-2.0 `LICENSE` 를 추가했습니다. 그 파일을 그대로 가져왔습니다.
- 코드 수정이 필요하면 이 디렉터리를 직접 고치지 말고, 새 태그로 통째로 교체하는 방식을 권합니다.
  직접 고쳤다면 이 표에 그 사실을 적어 두십시오.

### 새 버전으로 바꾸는 방법

```bash
git clone https://github.com/Autumn-27/norma /tmp/norma
rm -rf third_party/norma && mkdir -p third_party/norma
git -C /tmp/norma archive vX.Y.Z | tar -x -C third_party/norma
cp /tmp/norma/LICENSE third_party/norma/LICENSE   # 태그에 LICENSE 가 없을 때만
# go.mod 의 require 줄 버전을 vX.Y.Z 로 맞춘 뒤
go build ./... && go test ./... -count=1
```

이 문서의 버전·커밋 값도 함께 갱신합니다.

---

## English

This directory holds verbatim copies of dependencies that are **only available from the upstream
author's personal repositories**, so this repository still builds if those repositories disappear or
change. Ordinary public libraries (`golang.org/x/...`, `pgx`, and so on) are not copied here; they are
fetched as normal Go modules.

### norma

- **Module / version:** `github.com/Autumn-27/norma` `v0.4.3` (tag commit `320ae32`, 2026-09-29),
  exported with `git archive` from <https://github.com/Autumn-27/norma>.
- **Wiring:** `replace github.com/Autumn-27/norma => ./third_party/norma` in the root `go.mod`.
- **Unmodified.** Apart from `LICENSE`, the 210 files are byte-identical to the tag. Their recomputed
  module hash matches the `h1:DnmOhJPL6OZSMnCVYO5Ujh4yVINuDarEickVi9jx1hI=` that `go.sum` pinned before.
- **`LICENSE` added.** The `v0.4.3` tag has no license file; the author added the Apache-2.0 `LICENSE`
  in commit `52f17dd` on 2026-10-11, and that file is copied here unchanged.
- To upgrade, follow the commands above and update the version and commit in this file.
