# Whisper + T5를 활용한 자동 자막 서비스

참여자: 손기훈

# 프로젝트 배경

- whisper의 놀라운 성능으로 우리는 다양한 음성 리소스들을 손쉽게 텍스트로 변환 가능하게 되었다.
- 하지만 생성된 자막을 자동으로 번역하는 경우, 발화의 시간 단위로 분절 되어 있기 때문에, 라인 그대로 번역을 하게 되면 번역의 질이 상당히 떨어지는 경향을 보이게 되었다.
- 따라서, 기존 라인 인덱스를 유지하면서 문장들을 완성된 하나의 문장으로 합쳐준 후에 번역을 진행하고 다시 기존의 라인 인덱스에 따라 분할을 진행하는 작업이 필요하였다.
- 기존에 실험한 파일럿 테스트에서는, (line break) 라는 분할점을 붙여주어 번역을 진행해주었더니, 기존의 번역 퀄리티를 해치지 않으면서 ‘(라인 브레이크)’ 라는 형태의 분할점을 생성해주었다.
- 다만, 기존의 사전 학습 된 T5 번역기는 훨씬 더 긴 토큰 길이를 가지고 학습이 되었기 때문에 불필요한 크기를 지니게 되었다.
- 따라서, 자막 데이터셋과 문장의 길이가 길지 않은 (한-영) 데이터셋을 구하여 T5를 파인튜닝을 진행하여 그 부분을 보완하고자 한다.

# 프로젝트 계획

1. 데이터셋 수집
2. 데이터 처리 (srt 파일과 같은 형태의 포맷으로 다시 만들어 줌)
3. T5 파인튜닝 (quantization, Onnx 등을 사용하여 경량화)
    1. (line break) 라는 custom 토큰을 추가하는 것 고려
4. whisper + T5를 사용하여 서비스화
    1. whisper를 통해 STT 진행
    2. whisper로 생성된 SRT 파일을 T5 모델로 번역 진행
    3. 자막 파일 반환
    4. 위의 서비스를 Gradio로 구현하여 huggingface space 배포
5. 프로젝트의 끝은 gradio로 구현하여 huggingface space 배포하는 것으로 정의한다.

# 프로젝트 소요 기간 예상

- 1번과 2번을 합쳐 약 1주 소요 예상
- 3번에 3~4일 소요 예상
- 4번에 3~4일 소요 예상
- 총 소요 기간 약 2주~3주 예상

# 프로젝트를 통한 가치 창출

- 영어로 생성된 다양한 영상 정보에 접근하기 힘든 사람들에게 진입 장벽을 낮춰줄 수 있다.

# 프로젝트 진행

## 데이터셋 제작

- 대상 사이트

| 사이트 | 방법 |
| --- | --- |
| https://www.opensubtitles.org/ko/search/sublanguageid-kor | 1. 수동|
2. 크롤링 코드 제작 
| youtube - playlists 한국어 자막 있는. | 1. youtube api 활용 |
- 코드 진행상황
    

- 대상 데이터셋 youtube 카테고리

[ ] 음식
[ ] 여행
[ ] 게임
[ ] 뉴스
[ ] 기술
[ ] 과학
[ ] 예능
[ ] v-log
[ ] etc...

|재생목록|태그|
    

---

- [ ]  데이터 수집 소스 찾기
- [ ]  수집 코드 작성

---

## 데이터 처리

아직 진행 안 되고 있음

- 수집 - srt 나 youtube 자막 파일 형태
- 처리
    1. (Line Break) 토큰 추가
    2. 이전 문장도 함께 들어가게 할지?

---

- [ ]  데이터 수집 완료
- [ ]  데이터 처리 코드

---

## T5 파인튜닝

진행 중이지 않음

---

- [ ]  모델 코드 제작
- [ ]  모델 학습
- [ ]  모델 검증

---

## Whisper + T5 서비스화

---

- [ ]  whisper pipeline 제작
- [ ]  whipser 결과 파싱
- [ ]  text input ⇒ T5 pipeline 제작
- [ ]  T5 결과 파싱
- [ ]  결과 검증

---

## Gradio 구현 및 서비스 배포

---

- [ ]  Gradio Tutorial
- [ ]  Gradio 제작
- [ ]  space 올리기

---
