# Voice-to-Text with WhisperX and Diarization

## Introduction
OpenAI의 Whisper와 WhisperX를 기반으로 음성 파일(.m4a)을 텍스트로 전사하고, pyannote.audio를 통해 화자 구분(Speaker Diarization)까지 수행하는 프로젝트입니다.  
이 프로젝트는 혼합 언어 인터뷰 데이터에 대해 정확하고 구조화된 전사 결과를 얻기 위해 설계되었습니다.

## Features
- WhisperX 기반 고정밀 전사
- Pyannote.audio를 활용한 화자 구분
- 출력 형식: .txt, .srt, .vtt, .tsv, .json 등
- Hugging Face 토큰을 사용하여 gated 모델 접근 가능

## Installation and Setup
1. Python 3.10 이상 설치
2. 필수 라이브러리 설치:

```bash pip install -U git+https://github.com/m-bain/whisperx.git```

3. ffmpeg 설치 후 환경변수 등록 (윈도우의 경우 bin 폴더 경로를 PATH에 추가)
4. Hugging Face access token 발급 및 조건 수락:

- pyannote/speaker-diarization-3.1
- pyannote/segmentation-3.0

5. Token을 환경 변수로 등록 (PowerShell 기준):
`$env:HF_TOKEN="hf_YOUR_TOKEN"`


## Usage
whisperx "FILE_NAME.m4a" `
  --language English `
  --diarize `
  --output_dir ./output `
  --output_format all `
  --compute_type float32 `
  --hf_token $env:HF_YOUR_TOKEN

## Output Files
output/ 폴더에 다음 파일이 생성됩니다:
.txt: 텍스트 전사 결과
.json: 세부 전사 메타 정보
.srt, .vtt: 자막 파일
.tsv: 시간정보 포함 TSV


