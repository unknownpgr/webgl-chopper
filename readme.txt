컴퓨터 그래픽스 프로젝트

1. Requirements 구현

Requirements에 제시된 모든 내용을 구현함

-   방향키 및 A,Z키를 사용한 chopper의 움직임

-   z-axis를 유지한 채로 (0,0,0)좌표를 중심으로 하는 화면 회전 및 zoom in/out

-   Indexed buffer를 사용한 N by N grid(400 by 400)

-   쉐이더에 texture image binding 및 이를 이용한 position, normal 계산

-   Point light 및 directional light를 사용한 전체 조명 및 bullet 조명 효과

-   자연스러운 bullet 발사 및 중력에 따른 낙하

단 쉐이더를 구현할 때 좀 더 다양한 효과를 사용하고자 THREE.js의 PhongMaterialShader를 수정하여 이용함. Vertex shader에서는 texture를 사용하여 position 및 normal값을 수정하도록 구현하였으며, fragment shader는 손대지 않고 그대로 사용함.

2. 추가로 더 구현한 것

-   키보드 키를 누르는 순간뿐만 아니라, 진짜 게임처럼 키보드 키를 누르는 동안 계속 chopper 및 view움직임이 발생

-   Chopper 및 view를 움직일 때 부드럽게 움직일 수 있도록 IIR low-pass filter를 사용하여 약간의 관성을 부여

-   실제와 비슷하게 보이도록 전진, 후진할 때 chopper를 약간 기울이도록 구현 (실제 진행 방향은 영향을 받지 않음)

-   Chopper가 공중에 미동도 없이 있으니 약간 어색하여, 작은 위아래 움직임을 추가

-   Bullet을 scene에 동적으로 추가하니 약간의 지연이 발생하는 문제점이 있어 bullet이 수명이 다할 경우(y<0이 되는 경우) clip space밖의 아주 먼 점으로 이동시키는 트릭을 적용

-   비직관적인 움직임을 막고자 view 회전 및 zoom 범위를 적절히 제한
