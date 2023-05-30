# AIFFEL Campus Online 4th Code Peer Review Templete
- 코더 : 김재환
- 리뷰어 : 이동익

# PRT(PeerReviewTemplate)
각 항목을 스스로 확인하고 토의하여 작성한 코드에 적용합니다.
- [🔺] 1.코드가 정상적으로 동작하고 주어진 문제를 해결했나요?
    - 데이터 전처리 과정까지 잘 진행되었으나, 모델 구현 및 학습이 진행되지 못했습니다.
- [⭕] 2.주석을 보고 작성자의 코드가 이해되었나요?
    - 전처리 단계별로 작성하였습니다.
    ```python
    # Need to split images up into 2 pieces
    # Check the separated images
    # Resizing to 286x286
    # Random cropping back to 256x256
    # Random mirroring
    ```
- [❌] 3.코드가 에러를 유발할 가능성이 있나요?
    - 없는 것 같습니다.
- [⭕] 4.코드 작성자가 코드를 제대로 이해하고 작성했나요?
    - Generator, Discriminator에서 모델의 각 레이어 구성 및 손실함수를 정의하는 과정을 인터뷰했습니다.
- [⭕] 5.코드가 간결한가요?
    - 간결하고 가시성 있게 작성되었습니다.

# 참고 링크 및 코드 개선

