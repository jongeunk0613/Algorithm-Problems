### 📖 Problem Description

- [문제 풀러 가기](https://app.codility.com/programmers/lessons/4-counting_elements/frog_river_one/)
- 개구리가 강의 한쪽에서 다른 쪽으로 건너는데 걸리는 최소의 시간을 구하기
<br/>

### 💡 Facts

#### Inputs
- 낙엽이 떨어지는 위치와 시간을 나타내는 N 길이의 배열 A가 주어진다.
- 강의 길이 X가 주어진다.

#### Details
- A[K]는 초로 나타낸 K시간에 낙엽이 떨어지는 위치를 의미한다.
- 개구리가 강을 건너려면 1에서 X까지의 모든 낙엽이 떨어져야 한다.
<br/>

### 🚎 Approach

- 각가 다른 위치에 떨어진 낙엽의 개수를 센다.
- 해당 개수가 강의 길이와 같을 경우, 강을 건너기 위해 필요한 모든 위치에 낙엽이 떨어졌다는 것을 의미한다.
- 특정 위치에 낙엽이 떨어진 유무를 체크할 배열을 추가로 사용한다.
<br/>

### 🧭 Complexity

- Space Complexity : O(N)
- Time Complexity : O(N)
<br/>

### 📝 Source Code

```javascript
function solution(X, A) {
    let countFallingLeaves = 0;
    let fallingLeaves = new Array(X).fill(0);

    for(let i = 0; i < A.length; i++){

        if (fallingLeaves[A[i]-1] == 0){
            countFallingLeaves += 1;
        }
        fallingLeaves[A[i]-1] = 1;

        if (countFallingLeaves == X){
            return i;
        }
    }

    return -1;
}
```
<br/>

### Other solutions
<details>
<summary>Set 사용하기 [Python]</summary>
<div markdown="1">

```Python
def solution(X, A):
    leafSet = set()
  
    for i in range(X):
        leafSet.add(i+1)

    for i in range(len(A)):
        leafSet.discard(A[i])
        
        if len(leafSet) == 0:
            return i

    return -1
```
set을 이용해서 1-X까지 모든 낙엽의 위치를 넣고 배열의 요소를 만날 때마다 제외해준다. 
set이 비어있을 경우 모든 위치에 낙엽이 떨어졌다는 뜻이기 때문에 i를 반환한다.

</div>
</details>
