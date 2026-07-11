# 선박 대기시간 예측 경진대회

[![Python](https://img.shields.io/badge/python-3.10-3776AB?logo=python&logoColor=white)](https://www.python.org) [![License](https://img.shields.io/badge/license-Apache--2.0-blue.svg)](LICENSE)

선박이 입항한 뒤 접안까지 기다리는 시간을 예측한 HD현대 AI Challenge 기록입니다. 예선에서 대기시간을 회귀로 예측해 2위에 올랐고, 본선에서는 시계열 신호 데이터를 다뤄 6위를 기록했습니다.

## 개요

| 구분 | 내용 |
| --- | --- |
| 대회 | HD현대 AI Challenge |
| 기간 | 2023.09.25 – 2023.11.10 (예선·본선) |
| 주최 / 운영 | HD한국조선해양 AI Center / 데이콘 |
| 평가지표 | MAE |
| 결과 | 예선 2위, 본선 6위 |
| 예선 과제 | 선박 대기시간 `CI_HOUR` 회귀 예측 |
| 본선 과제 | 시계열 신호 기반 trial 단위 회귀 |

## 접근

- 예선에서는 결측 처리와 시간 파생 변수, target encoding을 적용하고 XGBoost·CatBoost 앙상블을 구성했습니다.
- `DIST == 0` 같은 특수 케이스를 후처리로 보정했습니다.
- 본선에서는 시계열 신호 파일을 trial 단위로 파싱하고 sliding window 피처를 만들었습니다.
- LightGBM 예측을 ID 단위 백분위 집계와 반올림으로 제출 형식에 맞췄습니다.

## 저장소 구성

```text
.
├── notebooks/
│   ├── preliminaries/     # 예선: EDA·피처 엔지니어링, XGBoost·CatBoost 앙상블
│   └── finals/            # 본선: 신호 EDA·피처 엔지니어링, LightGBM 파이프라인
└── requirements.txt
```

## 공개 범위

대회 원본 데이터, 전처리 산출물, 모델 파일, 제출 파일은 포함하지 않았습니다. 데이터는 대회 참가자에게만 제공되어 그대로 재현하기는 어렵고, 저장소에는 접근 방식을 담은 노트북만 남겼습니다.

## 링크

- [대회 페이지](https://dacon.io/competitions/official/236158/overview/description)
- [최종 리더보드](https://dacon.io/competitions/official/236158/leaderboard)

## 라이선스

Apache License 2.0. 자세한 내용은 [LICENSE](LICENSE)에 있습니다.
