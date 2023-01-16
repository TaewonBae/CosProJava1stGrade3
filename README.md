# COS PRO Java 1급 - 모의고사3

### 3차) 문제1 -
```Java
class Main {
		// 3. arrA 배열을 두 번 이어 붙여 길이가 2배인 배열로 만든다.
    int[] func_a(int[] arr) {
        int length = arr.length;
        int[] ret = new int[length*2];
        for(int i = 0; i < length; i++)
            ret[i + length] = ret[i] = arr[i];
        return ret;
    }
    // 2. 두 배열의 구성 성분이 달라 회전했을 때 같아질 가능성이 없다면 false를 리턴
    boolean func_b(int[] first, int[] second){
        int[] counter = new int[1001];
        for(int i = 0; i < first.length; i++){
            counter[first[i]]++;
            counter[second[i]]--;
        }
        for(int i = 0; i < 1001; i++)
            if(counter[i] != 0)
                return false;
        return true;
    }
    // 4. arrA의 부분 배열 중 arrB와 같은 배열이 있으면 true, 그렇지 않으면 false를 리턴
    boolean func_c(int[] first, int[] second){
    int length = second.length;
    for(int i = 0; i < length; i++){
        int j;
        for(j = 0; j < length; j++)
            if(first[i + j] != second[j])
                break;
        if(j == length)
            return true;
    }
    return false;
}

    public boolean solution(int[] arrA, int[] arrB) {
			//1 . arrA와 arrB의 길이가 다르면 false를 리턴
        if(arrA.length != arrB.length)
            return false;
        if(func_b(arrA,arrB)) {
            int[] arrAtemp = func_a(arrA);
            if(func_c(arrAtemp, arrB))
                return true;
        }
        return false;
    }
    public static void main(String[] args) {
        Main sol = new Main();
        int[] arrA1 = {1, 2, 3, 4};
        int[] arrB1 = {3, 4, 1, 2};
        boolean ret1 = sol.solution(arrA1, arrB1);

        System.out.println("solution 메소드의 반환 값은 " + ret1 + " 입니다.");

        int[] arrA2 = {1, 2, 3, 4};
        int[] arrB2 = {1, 4, 2, 3};
        boolean ret2 = sol.solution(arrA2, arrB2);

        System.out.println("solution 메소드의 반환 값은 " + ret2 + " 입니다.");
    }
}
```

### 3차) 문제2 -
```Java

```

### 3차) 문제 -
```Java

```

### 3차) 문제 -
```Java

```

### 3차) 문제 -
```Java

```

### 3차) 문제 -
```Java

```

### 3차) 문제 -
```Java

```

### 3차) 문제 -
```Java

```

### 3차) 문제 -
```Java

```

### 3차) 문제 -
```Java

```
