# P!npoint Beta Runtime

P!npoint closed Beta 클라이언트의 서명된 Runtime Pack과 업데이트 manifest를 배포하는 공개 저장소입니다.

## 배포 페이지

- [Beta Runtime Release](https://github.com/snowtie/Pinpoint-beta-runtime/releases/tag/beta-runtime)
- [현재 channel-manifest.json](https://github.com/snowtie/Pinpoint-beta-runtime/releases/download/beta-runtime/channel-manifest.json)
- [배포 Workflow 원본](https://github.com/snowtie/Pinpoint/blob/main/.github/workflows/release-runtime.yml)

Beta 클라이언트는 `channel-manifest.json`의 서명, SHA-256, Runtime Pack 서명, Native Host API 호환성을 모두 확인한 뒤 런타임을 교체합니다. 새 런타임이 실패하면 직전 런타임으로 rollback할 수 있습니다.

## 업로드 규칙

Runtime Pack은 P!npoint 저장소의 `Release Beta Runtime Pack` GitHub Actions workflow로만 게시합니다. Workflow는 Runtime Pack을 먼저 업로드하고, 모든 검증이 끝난 뒤 manifest를 마지막에 업로드합니다.

허용되는 Release asset:

- `Pinpoint_runtime_<version>.ppruntime`
- `Pinpoint_runtime_<version>.ppruntime.sig`
- `channel-manifest.json`
- `channel-manifest.json.sig`

이 저장소에는 설치 파일, Bootstrap Downloader, 비공개 테스트 묶음, 소스 코드, 인증서 또는 credential을 올리지 않습니다.

## 베타 클라이언트 자체 업데이트

Native Host가 바뀌는 Beta 클라이언트 업데이트는 Runtime Pack과 분리합니다. 승인된 테스터는 Windows용 `Pinpoint_<beta-version>_windows-<arch>-setup.exe` 또는 해당 설치 파일이 들어 있는 Release ZIP을 실행 중인 Beta 클라이언트에 드롭해 업데이트합니다. 클라이언트는 버전, 플랫폼, 실행 파일 헤더, 크기, SHA-256을 검사하고 명시적인 확인을 받은 뒤 종료·설치·재실행합니다.
