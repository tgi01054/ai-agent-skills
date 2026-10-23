# AI Agent Skills

외부 AI 에이전트 스킬과 플러그인을 Git submodule로 관리하는 저장소입니다.

## 포함된 저장소

| 이름 | 경로 | 원본 저장소 |
| --- | --- | --- |
| Superpowers | `vendor/superpowers` | [obra/superpowers](https://github.com/obra/superpowers) |
| gstack | `vendor/gstack` | [garrytan/gstack](https://github.com/garrytan/gstack) |
| Matt Pocock Skills | `vendor/mattpocock-skills` | [mattpocock/skills](https://github.com/mattpocock/skills) |
| Addy Osmani Agent Skills | `vendor/addyosmani-agent-skills` | [addyosmani/agent-skills](https://github.com/addyosmani/agent-skills) |
| pstack | `vendor/cursor-plugins/pstack` | [cursor/plugins](https://github.com/cursor/plugins) |
| Claude Feature Dev | `vendor/claude-code/plugins/feature-dev` | [anthropics/claude-code](https://github.com/anthropics/claude-code) |
| GitHub Spec Kit | `vendor/spec-kit` | [github/spec-kit](https://github.com/github/spec-kit) |
| OpenSpec | `vendor/openspec` | [Fission-AI/OpenSpec](https://github.com/Fission-AI/OpenSpec) |
| Compound Engineering | `vendor/compound-engineering-plugin` | [EveryInc/compound-engineering-plugin](https://github.com/EveryInc/compound-engineering-plugin) |
| Security Audit Skill | `vendor/security-audit-skill` | [cloudflare/security-audit-skill](https://github.com/cloudflare/security-audit-skill) |

## Vendor 레이아웃

외부 저장소는 기본적으로 `vendor/<저장소명>` 경로에 Git submodule로 포함합니다.
모노레포에서 특정 플러그인이나 스킬만 사용하는 경우에는 원본 저장소의 경로를 유지합니다.

```text
vendor/
  <외부 저장소>/
    skills/...

  cursor-plugins/
    pstack/skills/...

  claude-code/
    plugins/feature-dev/...
```

따라서 각 저장소의 `SKILL.md` 위치와 하위 디렉터리 구조는 원본 저장소의 레이아웃을 따릅니다.

## Clone

Submodule을 포함하여 저장소를 clone하려면 다음 명령어를 실행합니다.

```bash
git clone --recurse-submodules <repository-url>
```

이미 clone한 저장소에서 submodule을 초기화하려면 다음 명령어를 실행합니다.

```bash
git submodule update --init --recursive
```

## Submodule 업데이트

등록된 원격 저장소의 최신 커밋으로 submodule을 업데이트하려면 다음 명령어를 실행합니다.

```bash
git submodule update --remote --merge
```

업데이트한 submodule 커밋을 반영하려면 변경사항을 확인하고 commit합니다.

```bash
git status
git add .gitmodules vendor
git commit -m "chore: update skill submodules"
```
