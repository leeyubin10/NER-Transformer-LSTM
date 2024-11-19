# NLP Homework 2: Named Entity Recognition

## 1. Task
### 1.1 Named Entity Recognition
- 주어진 문장에서 Named Entity를 찾는 태스크입니다.
- **BIO notation**을 사용합니다.

---

## 2. Datasets
### 2.1 Tokenize_and_align_labels(examples)
- 입력 예제의 단어를 토큰화하고, 토큰에 해당하는 NER 태그를 정렬합니다.
- **특수 토큰**에는 `-100`을 할당합니다.
- 단어의 **첫 번째 토큰**에만 NER 태그를 할당합니다.
- 서브워드 토큰들은 `-100`으로 라벨링하여 학습 시 무시됩니다.
- 최종적으로 **정렬된 라벨**을 포함한 토큰화된 입력을 반환합니다.

---

## 3. Metrics
- **Precision**, **Recall**, **F1**, **Accuracy**를 사용하여 성능을 평가합니다.

---

## 4. Transformer Encoder
### 4.1 PositionalEncoding
- 입력 시퀀스의 각 위치에 대한 위치 인코딩을 생성합니다.
- 짝수 인덱스에는 **사인 함수**, 홀수 인덱스에는 **코사인 함수**를 사용하여 위치 인코딩을 생성합니다.
- 입력 시퀀스 길이에 맞는 위치 인코딩을 반환합니다.

### 4.2 MultiHeadAttention
- **Multi-head attention**을 구현합니다.
- Query, Key, Value 텐서를 **Projection**하고 Scaling합니다.
- Attention Weight를 계산하고 이를 멀티 헤드 형식으로 변환 후 최종 출력을 반환합니다.

### 4.3 Encoder
- Transformer의 **Encoder**를 구현합니다.
- 입력 토큰을 임베딩하고 Positional Encoding을 추가하여 초기 hidden states를 생성합니다.
- 여러 인코더 레이어를 통과시켜 최종 hidden states를 반환합니다.

---

## 5. LSTM
### 5.1 LSTM Cell
- 입력과 은닉 상태에 대한 선형 변환을 수행합니다.
- 게이트들을 기반으로 **새로운 셀 상태**와 **은닉 상태**를 계산합니다.
- **Sigmoid**와 **Hyperbolic Tangent** 활성화 함수를 사용합니다.
- 최종적으로 새로운 은닉 상태와 셀 상태를 반환합니다.

### 5.2 ModelForNER
- 입력을 **Transformer** 또는 **LSTM**을 사용하여 처리합니다.
- 결과를 분류기에 전달하여 **Logits**를 생성합니다.
- `config.use_lstm`에 따라 Transformer 또는 LSTM을 선택합니다.

---

## Summary
- 이 과제는 Transformer와 LSTM 모델을 사용하여 Named Entity Recognition(NER) 문제를 해결합니다.
- BIO Notation과 다양한 모델 구조를 통해 성능을 분석합니다.
