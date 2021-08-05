# 코딩테스트 백문 알고리즘 문제 풀기


### 2798번 블랙잭 (정렬,완전탐색 문제) https://www.acmicpc.net/problem/2798


#### 문제

카지노에서 제일 인기 있는 게임 블랙잭의 규칙은 상당히 쉽다. 카드의 합이 21을 넘지 않는 한도 내에서, 카드의 합을 최대한 크게 만드는 게임이다. 블랙잭은 카지노마다 다양한 규정이 있다.

한국 최고의 블랙잭 고수 김정인은 새로운 블랙잭 규칙을 만들어 상근, 창영이와 게임하려고 한다.

김정인 버전의 블랙잭에서 각 카드에는 양의 정수가 쓰여 있다. 그 다음, 딜러는 N장의 카드를 모두 숫자가 보이도록 바닥에 놓는다. 그런 후에 딜러는 숫자 M을 크게 외친다.

이제 플레이어는 제한된 시간 안에 N장의 카드 중에서 3장의 카드를 골라야 한다. 블랙잭 변형 게임이기 때문에, 플레이어가 고른 카드의 합은 M을 넘지 않으면서 M과 최대한 가깝게 만들어야 한다.

N장의 카드에 써져 있는 숫자가 주어졌을 때, M을 넘지 않으면서 M에 최대한 가까운 카드 3장의 합을 구해 출력하시오.


#### 입력 

첫째 줄에 카드의 개수 N(3 ≤ N ≤ 100)과 M(10 ≤ M ≤ 300,000)이 주어진다. 둘째 줄에는 카드에 쓰여 있는 수가 주어지며, 이 값은 100,000을 넘지 않는 양의 정수이다.

합이 M을 넘지 않는 카드 3장을 찾을 수 있는 경우만 입력으로 주어진다.

#### 출력 

첫째 줄에 M을 넘지 않으면서 M에 최대한 가까운 카드 3장의 합을 출력한다.



## SOLUTION

n,m = list(map(int,input().split(" ")))
b = list(map(int,input().split(" ")))

c = 0
length = len(b)




for i in range(0,length):
    for j in range(i+1, length):
        for k in range(j + 1, length):
            if b[i]+b[j]+b[k] <=m:
                c = max(c,b[i]+b[j]+b[k])


print(c)


원소갯수 , 최대값 , 각각의 원소를 입력받고 배열의길이만큼 3중 반복문을 돌려서 해당 최대값을 넘지않으면서 최대값을

매번 갱신하면서 최대값을 알아낸다 





### 2920번 음계 (정렬문제) https://www.acmicpc.net/problem/2920


#### 문제

다장조는 c d e f g a b C, 총 8개 음으로 이루어져있다. 이 문제에서 8개 음은 다음과 같이 숫자로 바꾸어 표현한다. c는 1로, d는 2로, ..., C를 8로 바꾼다.

1부터 8까지 차례대로 연주한다면 ascending, 8부터 1까지 차례대로 연주한다면 descending, 둘 다 아니라면 mixed 이다.

연주한 순서가 주어졌을 때, 이것이 ascending인지, descending인지, 아니면 mixed인지 판별하는 프로그램을 작성하시오.


#### 입력 

첫째 줄에 8개 숫자가 주어진다. 이 숫자는 문제 설명에서 설명한 음이며, 1부터 8까지 숫자가 한 번씩 등장한다.

#### 출력 

첫째 줄에 ascending, descending, mixed 중 하나를 출력한다.



## SOLUTION

1

a = list(map(int,input().split(" ")))

ascending = True
deseding = True

for i in range(0,7):
    if a[i]>a[i+1]:
        ascending = False
    elif a[i]<a[i+1]:
        deseding = False


if ascending:
    print('ascending')
elif deseding:
    print('deseding')
else:
    print('mix')
    
2

a = list(map(int,input().split(" ")))
b = 0
c = 0

ascending = True
deseding = True

for i in range(0,7):
    if a[i]>a[i+1]:
        b = b+1
    elif a[i]<a[i+1]:
        c = c+1


if b==7:
    print('descending')
elif c==7:
    print('ascending')
else:
    print('mixed')
    
    
배열에 숫자를 입력받고 갯수많큼 반복문을 돌려준다음 위로정렬인지 아래로정렬인지 조건식을 따져서

조건을 고쳐주고 반복문끝나고 조건문을 통해 ascending,descending,mixed 인지 확인한다.





