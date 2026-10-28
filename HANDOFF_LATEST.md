# 🎨 imagemaker — 크로스 PC 작업 인수인계서 (HANDOFF_LATEST)

> **최종 업데이트**: 2026-10-28 (`main` 브랜치 · 단독 독립 스튜디오 분리 완료)
> **저장소**: [https://github.com/ajwei0508-cpu/imagemaker.git](https://github.com/ajwei0508-cpu/imagemaker.git)
> **포트**: `http://localhost:4500`

---

## 🚀 1. 다른 컴퓨터에서 1초 만에 이어서 작업하는 방법

채팅창에 **"이미지메이커 실행해줘"** (또는 **"5번 실행해줘"**)라고 입력하시면:
1. 로컬에 `D:\imagemaker`가 없으면 `git clone https://github.com/ajwei0508-cpu/imagemaker.git D:\imagemaker`를 수행합니다.
2. 이미 폴더가 있으면 `git pull origin main`으로 최신 상태를 동기화합니다.
3. `npm install` 후 `node serve.js` (포트 4500) 스튜디오 서버를 즉시 구동합니다.

---

## 💎 2. 프로젝트 개요 & 아키텍처
- **목적**: 인물 사진 왜곡 없는 100% 얼굴 고정 AI 사진관 (원장님 프로필, 홈페이지 원본 얼굴 1:1 교체)
- **핵심 엔진**:
  1. **FLUX Portrait LoRA & PuLID-FLUX**: 두상·골격·안경·체형 일관성 유지
  2. **Face Lock (InsightFace + CodeFormer)**: 대표 얼굴 1:1 정밀 랜드마크 스왑 & 모공/안경테 초고해상도 복원
  3. **홈페이지 원클릭 얼굴 교정 (`apply-to-homepage`)**: `bareun-homepage/homepage` 내 원본 사진 자동 백업 후 얼굴만 교체

---

## 📂 폴더 구조
- `data/`
  - `profiles.json` : 인물 프로필 설정
  - `profiles/` : 인물별 참조 사진 (Reference Photos)
- `index.html` : 반응형 스튜디오 웹 UI
- `serve.js` : 로컬 Node.js 백엔드 서버 (포트 `4500`)
- `start-studio.bat` : 윈도우 원클릭 실행 배치파일
