# 코딩테스트 백문 알고리즘 문제 풀기


### 1874번 프린터 큐 (큐, 구현 ,그리디 문제) https://www.acmicpc.net/problem/1966


#### 문제

여러분도 알다시피 여러분의 프린터 기기는 여러분이 인쇄하고자 하는 문서를 인쇄 명령을 받은 ‘순서대로’, 즉 먼저 요청된 것을 먼저 인쇄한다. 여러 개의 문서가 쌓인다면 Queue 자료구조에 쌓여서 FIFO - First In First Out - 에 따라 인쇄가 되게 된다. 하지만 상근이는 새로운 프린터기 내부 소프트웨어를 개발하였는데, 이 프린터기는 다음과 같은 조건에 따라 인쇄를 하게 된다.

현재 Queue의 가장 앞에 있는 문서의 ‘중요도’를 확인한다.
나머지 문서들 중 현재 문서보다 중요도가 높은 문서가 하나라도 있다면, 이 문서를 인쇄하지 않고 Queue의 가장 뒤에 재배치 한다. 그렇지 않다면 바로 인쇄를 한다.
예를 들어 Queue에 4개의 문서(A B C D)가 있고, 중요도가 2 1 4 3 라면 C를 인쇄하고, 다음으로 D를 인쇄하고 A, B를 인쇄하게 된다.

여러분이 할 일은, 현재 Queue에 있는 문서의 수와 중요도가 주어졌을 때, 어떤 한 문서가 몇 번째로 인쇄되는지 알아내는 것이다. 예를 들어 위의 예에서 C문서는 1번째로, A문서는 3번째로 인쇄되게 된다.


#### 입력 

첫 줄에 테스트케이스의 수가 주어진다. 각 테스트케이스는 두 줄로 이루어져 있다.

테스트케이스의 첫 번째 줄에는 문서의 개수 N(1 ≤ N ≤ 100)과, 몇 번째로 인쇄되었는지 궁금한 문서가 현재 Queue에서 몇 번째에 놓여 있는지를 나타내는 정수 M(0 ≤ M < N)이 주어진다. 이때 맨 왼쪽은 0번째라고 하자. 두 번째 줄에는 N개 문서의 중요도가 차례대로 주어진다. 중요도는 1 이상 9 이하의 정수이고, 중요도가 같은 문서가 여러 개 있을 수도 있다.

#### 출력 

각 테스트 케이스에 대해 문서가 몇 번째로 인쇄되는지 출력한다.


## SOLUTION

n = int(input())

for i in range(0,n):

    a,b = list(map(int,input().split(" ")))   
    
    queue = list(map(int,input().split(" ")))   
    
    queue = [(i,idx) for idx, i in enumerate(queue)]   // [(1,0 )  , (2,1) , (3,2) , (4,3) ]  튜플형태로 인덱스랑같이 저장


    count = 0 ;
    
    while True:
    
        if queue[0][0]  == max(queue , key=lambda x:x[0])[0]:      //큐의 최대값과 같다면
        
            count+=1
            
            if queue[0][1] ==b:		//찾는인덱스라면
            
                print(count)                 //몇번째로 출력되는지 알려줌
                
                break
            else:
            
                queue.pop(0)		//최대값인데 찾는인덱스가 아니면 그냥 뽑아버림
                
        else:
        
            queue.append(queue.pop(0))  //최대값이 아니라면 팝해서 맨뒤에 넣음                




큐의 중요도와 인덱스를 튜플형태로 만들고 반복문을통해 중요도가 제일높은 문서를찾고 아니면 뒤로보내고

맞약 찾았다면 찾는 인덱스 위치를 비교해 맞다면 최대값을찾은 횟수(count)를 출력하고 반복문을끝낸다 . 그렇지 않다면

큐에서 그냥 뽑기만하고 다시 반복문을 진행한다




* * *

***

*****

- - -

---------------------------------------

### 1874번 스택수열 (스택,그리디 문제) https://www.acmicpc.net/problem/1874


#### 문제

스택 (stack)은 기본적인 자료구조 중 하나로, 컴퓨터 프로그램을 작성할 때 자주 이용되는 개념이다. 스택은 자료를 넣는 (push) 입구와 자료를 뽑는 (pop) 입구가 같아 제일 나중에 들어간 자료가 제일 먼저 나오는 (LIFO, Last in First out) 특성을 가지고 있다.

1부터 n까지의 수를 스택에 넣었다가 뽑아 늘어놓음으로써, 하나의 수열을 만들 수 있다. 이때, 스택에 push하는 순서는 반드시 오름차순을 지키도록 한다고 하자. 임의의 수열이 주어졌을 때 스택을 이용해 그 수열을 만들 수 있는지 없는지, 있다면 어떤 순서로 push와 pop 연산을 수행해야 하는지를 알아낼 수 있다. 이를 계산하는 프로그램을 작성하라.


#### 입력 

첫 줄에 n (1 ≤ n ≤ 100,000)이 주어진다. 둘째 줄부터 n개의 줄에는 수열을 이루는 1이상 n이하의 정수가 하나씩 순서대로 주어진다. 물론 같은 정수가 두 번 나오는 일은 없다.

#### 출력 

입력된 수열을 만들기 위해 필요한 연산을 한 줄에 한 개씩 출력한다. push연산은 +로, pop 연산은 -로 표현하도록 한다. 불가능한 경우 NO를 출력한다.


## SOLUTION

n = int(input())


stack = []

result = []

count = 1


for i in range(0,n):

    a = int(input())                     
    while count <= a:                      
        stack.append(count)
        count += 1
        result.append('+')                  

    if stack[-1] == a:                    
        stack.pop()
        result.append('-')

    else:                                   
        print('NO')
        exit(0)


print('\n' .join(result))                 



입력한수만큼 반복문을 돌려주며  특정수를 입력받을때 1부터 그수까지 스택에 삽입한후

스택의 마지막 인덱스의 수가 입력받은수이고 , 스택에 원소를 연달아 빼낼때 내림차수를 유지할 수

있느냐가 문제의 핵심 포인트였다




#### 번외

n = int(input())

stack = []

result = []

count=1


for i in range(0,n):

    data = int(input())
    while count<=data:
        print("+")
        stack.append(count)
        count+=1


    if stack[-1]==data:
        print("-")
        stack.pop()


    else:
        print("NO")
        exit(0)
        

이렇게 짤경우는 시간초과로 오답처리 되었다

* * *

***

*****

- - -

---------------------------------------


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



* * *

***

*****

- - -

---------------------------------------



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





