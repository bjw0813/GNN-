# GNN-

﻿GNN
 
그래프(Graph)란, 꼭지점(Node)들과 그 노드를 잇는 변(간선, Edge)들을 모아 구성한 자료구조를 의미한다

1.관계, 상호작용과 같은 추상적인 개념을 다루기에 적합하다.

복잡한 문제를 더 간단한 표현으로 단순화할 수 있다.
소셜 네트워크, 바이러스 확산, 유저-아이템 소비 관계 등을 모델링할 수 있다.

2.비유클리드 공간의 표현 및 학습이 가능하다.

우리가 흔히 다루는 이미지, 텍스트, 정형 데이터는 유클리드 공간의 격자 형태로 표현 가능하지만, SNS 데이터, 분자(molecule) 데이터 등은 이가 불가능하므로 Non-Euclidean Space로 표현해야 합니다.

3.방향성

방향성 그래프는 그래프에서 모든 엣지가 방향을 띄고 있는 그래프를 말한다.
여기서 무방향 그래프는 방향성 그래프의 특별 케이스(엣지가 양방향으로 동일)로 생각하도록 한다.
그래프가 방향성이 없다면, 인접 행렬은 대칭이 된다.


등장배경

특정 구조로 정리되어 있지 않은 데이터를 처리하기 위해서 GNN은 등장했다. 구조화 되어있지 않은 데이터는 아직 처리되지 않은 데이터이거나 통상적으로 정리되어 있지 않은 형태를 가지고 있어 분석이 어렵다. 오디오, 이메일, 소셜미디어 데이터가 그렇다. 
이러한 데이터들을 이해하고 인사이트를 추려내기 위해서는 데이터들 간의 관계를 정의해야 하는데 기존의 머신 러닝 구조나 알고리즘으로는 이러한 처리되지 않은 데이터를 바탕으로 학습하는 것에 한계가 있었고 이에 대한 대안으로 나온 것이 GNN(그래프신경망)이다.

GNN의 적용

Node Classification

Node embedding을 통해 점들을 분류하는 문제다. 일반적으로 그래프의 일부만 레이블 된 상황에서 semi-supervised learning을 한다. 대표적인 응용 영역으로는 인용 네트워크, Reddit 게시물, Youtube 동영상이 있다.

Link Prediction

그래프의 점들 사이의 관계를 파악하고 두 점 사이에 얼마나 연관성이 있을지 예측하는 문제다. 대표적인 예로 페이스북 친구 추천, 왓챠플레이(유튜브, 넷플릭스) 영상 추천 등이 있다.

Graph Classification

그래프 전체를 여러가지 카테고리로 분류하는 문제이다. 이미지 분류와 비슷하지만 대상이 그래프라고 생각하면 된다. 분자 구조가 그래프의 형태로 제공되어 그걸 분류하는 산업 문제에 광범위하게 적용할 수 있으며 따라서 화학, 생의학, 물리학 연구자들과 활발히 협업을 하고 있다.



GNN분류

Recurrent Graph Neural Networks(RecGNNs)

Graph Neural Networks 가 recurrent 모델로부터 출발하였다. 그래프 자체가 시작과 끝이 있는 것이 아닌, 순환 구조이기 때문에 이 구조를 recurrent 모델을 통해 표현하고자 한 것으로 생각된다.
RecGNN은 노드 표현을 RNN으로 학습하고자 하는 것에 중점을 둔다. 여기서는 노드가 stable equilibrium에 도달할 때까지 계속해서 정보/메시지를 이웃 노드와 교환한다고 전제하였다.

Convolutional Graph Neural Networks(ConvGNNs)

ConvGNN 은 convolution이라는 연산을 일반 grid data 가 아닌, 그래프 데이터에 적용하는 방법을 정립하였다. ConvGNN의 핵심 아이디어는 바로 노드 v를 그 노드의 feature인 xv​와 이웃 노드의 feature인 
xu​,u∈N(v)를 aggregate 하여 표현했다는 점이다. RecGNN과 다른 것은 ConvGNN은 여러개의 graph convolutional layer를 쌓아서 노드를 고차원으로 표현했다는 것이다.
ConvGNN 은 여러 종류의 GNN 모델을 설계할 때 가장 중심적으로 사용된다. 예를 들어, graph convolution 사이에 ReLU를 두어 node classification 모델을 만들 수도 있고, convolution을 계속 pooling 하여 softmax 를 적용하면 graph classification 모델이 된다.

Graph Autoencoders(GAEs)

GA는 노드나 그래프를 인코딩하고 다시 복원하는 과정에서 latent vector를 얻는 비지도 학습이다. GAE는 네트워크 임베딩과 graph generative distributions를 학습하기 위한 용도로 사용된다. 네트워크 임베딩에서 GAE는 latent node representation을 학습한다.

Spatial-temporal Graph Neural Networks(STGNNs)






Spatial-temporal(공간적-시간적) 그래프의 숨겨진 패턴들을 학습하기 위한 네트워크다. 교통량 예측, 사람 동작 인식, 운전 행동 예측 등 다양한 분야에서 중요한 요소가 되고 있다. STGNNs의 핵심 아이디어는 공간적인 의존성과 시간적인 의존성을 동시에 고려하는 것이다.
현재 많은 접근방식들은 graph convolution을 통해 공간적 의존성을, RNN이나 CNN을 통해 시간적 의존성을 가져가는 방식을 사용하고 있다.
