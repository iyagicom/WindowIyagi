# 창이야기 (WindowIyagi)

**열려 있는 창을 모두 보고 제어합니다 — GNOME·KDE Plasma·Hyprland·sway·X11 어디서나. 창으로도, 스크립트로도.**

[English](README.md) · [한국어](README_ko.md)

## 왜 창이야기인가

- **모든 창을 목록 하나에.** 제목·프로그램·상태·가상 데스크톱을 아이콘과 함께 보여 주고, 창이 열리고 닫히고 바뀌면 바로 반영합니다.
- **어떤 창이든 제어.** 앞으로 가져오기·최소화·최대화·복원·닫기. 닫기는 프로그램에 정상적으로 요청하므로 저장 안 한 작업이 날아가지 않습니다.
- **다른 도구가 멈추는 곳에서도.** `wmctrl`·`xdotool` 은 Wayland 에서 창을 못 봅니다. 창이야기는 데스크톱마다 맞는 방법을 씁니다 — GNOME·KDE Plasma·labwc·Wayfire·niri·Hyprland·sway·X11.
- **스크립트로.** `WindowIyagi --list` 로 모든 창을 출력하고, `--activate`·`--minimize`·`--maximize`·`--restore`·`--close` 에 창 id 를 주면 됩니다. 단축키와 자동화에 딱입니다.
- **안 되면 이유를 알려 줍니다.** 이 데스크톱에서 볼 수 없거나 할 수 없는 것이 있으면 안내가 뜨고, 원인이 풀리면 알아서 다시 연결합니다.

## 명령줄

```bash
WindowIyagi --list                  # 창 목록 출력
WindowIyagi --activate <창 id>      # 앞으로
WindowIyagi --minimize <창 id>
WindowIyagi --maximize <창 id>
WindowIyagi --restore  <창 id>
WindowIyagi --close    <창 id>
```

## 지원 데스크톱

| 데스크톱 | 목록 | 앞으로 | 최소화 | 최대화·복원 | 닫기 |
|---|---|---|---|---|---|
| GNOME | ✅ | ✅ | ✅ | ✅ | ✅ |
| KDE Plasma | ✅ | ✅ | ✅ | ✅ | ✅ |
| labwc · Wayfire · niri · Hyprland | ✅ | ✅ | ✅ | ✅ | ✅ |
| sway | ✅ | ✅ | — | — | ✅ |
| X11 (XFCE · MATE · Cinnamon · LXQt …) | ✅ | ✅ | ✅ | ✅ | ✅ |

GNOME Wayland 에서는 처음 실행할 때 창 목록을 전해 주는 작은 확장을 설치합니다 — 한 번 다시 로그인하세요. (sway 는 자체적으로 최소화·최대화를 받지 않습니다.)

## 다운로드

우분투(deb)·페도라(rpm)·아치(pkg.tar.zst)·그 밖의 배포판(AppImage·zip)용 패키지가 **[Releases](https://github.com/iyagicom/WindowIyagi/releases)** 에 올라올 예정입니다.

창이야기는 모든 리눅스 데스크톱용 작업표시줄 **[작업이야기(TaskIyagi)](https://github.com/iyagicom/TaskIyagi)** 안에서 창을 다루는 엔진이기도 합니다.
