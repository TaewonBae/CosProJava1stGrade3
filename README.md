# COS PRO Java 1급 - 모의고사3

### 3차) 문제1 - 배열을 회전시켜보세요.
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

### 3차) 문제2 - 팰린드롬 문제
```Java
import java.util.*;

public class Main {
    public boolean func_a(ArrayList<String> list, String s) {
		for (int i = 0; i < list.size(); i++)
			if (s.equals(list.get(i)))
				return true;
		return false;
	}

    public boolean func_b(String s) {
		int length = s.length();
		for (int i = 0; i < length / 2; i++)
			if (s.charAt(i) != s.charAt(length - i - 1))
				return false;
		return true;
	}
    
    public String func_c(ArrayList<String> palindromes, int k) {
        Collections.sort(palindromes);
        if (palindromes.size() < k)
        	return "\"NULL\"";
        else
        	return palindromes.get(k-1);
    }

    public String solution(String s, int k) {
	//1. 팰린드롬 문자열을 저장할 palindromes를 선언
        ArrayList<String> palindromes = new ArrayList<String>();
	//받은 팰린드롬 문자열의 길이를 구한다.
        int length = s.length();
	//2. 주어진 문자열의 모든 부분 문자열을 찾아 다음을 수행
	// subStr : 부분 문자열, palindromes : 부분 문자열 중 팰린드롬
        for (int startIdx = 0; startIdx < length; startIdx++) {
            for (int cnt = 1; cnt < length - startIdx + 1; cnt++) {
                String subStr = s.substring(startIdx, startIdx + cnt);
		// 3. 부분 문자열이 팰린드롬 문자열인지 확인하고(func_b),
		// 팰린드롬 문자열이라면 배열 palindromes에 
		// 같은 문자열이 이미 들어 있는지 확인 (func_a)
                if (func_b(subStr)) {
                	if (func_a(palindromes, subStr) == false)
				// 배열 palindromes에 같은 문자열이 없으면, 현재 팰린드롬 문자열을 추가
                		palindromes.add(subStr);
                }
            }
        }
	// 4. palindromes를 정렬, 배열 길이가 k보다 작다면 "NULL"리턴, 
	// 그렇지 않으면 리스트의 k-1번째 원소를 리턴
        String answer = func_c(palindromes, k);
        return answer;
    }
    // 아래는 테스트케이스 출력을 해보기 위한 main 메소드입니다.
    public static void main(String[] args) {
    	Main sol = new Main();
        String s1 = new String("abcba");
        int k1 = 4;
        String ret1 = sol.solution(s1, k1);
        
        System.out.println("solution 메소드의 반환 값은 \"" + ret1 + "\" 입니다.");
        
        String s2 = new String("ccddcc");
        int k2 = 7;
        String ret2 = sol.solution(s2, k2);
        
        System.out.println("solution 메소드의 반환 값은 " + ret2 + " 입니다.");
    }
}
```

### 3차) 문제3 -
```Java

```

### 3차) 문제4 -
```Java

```

### 3차) 문제5 - 전광판 문구 출력
```Java
// 다음과 같이 import를 사용할 수 있습니다.
import java.util.*;

class Main {
    public String solution(String phrases, int second) {
        // 여기에 코드를 작성해주세요. phrases = "happy-birthday" & second = 3
	// 1. 문구 앞에 14개의 "_"를 붙인다.
        String answer = "";
	String display = "";
	display = "______________" + phrases; // "______________happy-birthday"
	// 2. 해당 초 수만큼 맨 앞의 글자를 맨 뒤로 옮기고 맨 앞을 삭제한다.
	for(int i=0; i<second;i++){
		display = display + display.charAt(0);
		display = display.substring(1);
	}
	// 3. 맨 앞에서부터 14개의 글자를 전광판에 보여준다.
	answer = display.substring(0,14);
        return answer;
    }
    // 아래는 테스트케이스 출력을 해보기 위한 main 메소드입니다.
    public static void main(String[] args) {
        Main sol = new Main();
        String phrases = new String("happy-birthday");
        int second = 3;
        String ret = sol.solution(phrases, second);
        // [실행] 버튼을 누르면 출력 값을 볼 수 있습니다.
        System.out.println("solution 메소드의 반환 값은 \"" + ret + "\" 입니다.");
    }
}
```

### 3차) 문제6 -
```Java

```

### 3차) 문제7 -
```Java

```

### 3차) 문제8 -
```Java

```

### 3차) 문제9 - 팝업 스토어를 열 최적의 날짜
```Java
class Main {
    public int solution(int[] revenue, int k) {
        int answer = 0;
        int n = revenue.length;
        int sum = 0;
	// 1. 처음부터 k번째까지 합을 구한다.
        for (int i = 0; i < k; i++) {
            sum += revenue[i];
        }
        answer = sum;
	// 2. 다음 윈도우의 시작점인 1번주터 돌면서 다음을 반복한다.
        for (int i = k; i < n; i++) {
	    // 2-1. (이전 합계 - 이전 윈도우의 맨 앞의 값 + 새로운 윈도우에 포함된 값)을 이용해
	    //현재 윈도우의 합계를 구한다.
            sum = sum - revenue[i - k] + revenue[i];
	    // 2-2. 합계 중 큰 값을 찾는다.
            if (answer < sum)
                answer = sum;
        }
        return answer;
    }
    
    public static void main(String[] args) {
        Main sol = new Main();
        int[] revenue1 = {1, 1, 9, 3, 7, 6, 5, 10};
        int k1 = 4;
        int ret1 = sol.solution(revenue1, k1);

        System.out.println("solution 메소드의 반환 값은 " + ret1 + " 입니다.");

        int[] revenue2 = {1, 1, 5, 1, 1};
        int k2 = 1;
        int ret2 = sol.solution(revenue2, k2);

        System.out.println("solution 메소드의 반환 값은 " + ret2 + " 입니다.");        
    }
}
```

### 3차) 문제10 - 밥먹고 머리자르고
```Java
import java.util.ArrayList;
import java.util.Iterator;

//Shop 인터페이스와 HairShop, Restaurant 클래스는 Inner Class로 작성되어있습니다. 아래 코드를 잘 읽고 빈칸을 채워주세요.
class Main {
    class Shop{
        protected ArrayList<Customer> reserveList;
        public Shop() {
			this.reserveList = new ArrayList<Customer>();
		}
        public boolean reserve(Customer customer){
            reserveList.add(customer);
            return true;
        }
    }
    class Customer{
        public int id;
        public int time;
        public int numOfPeople;
        public Customer(int id, int time, int numOfPeople){
            this.id = id;
            this.time = time;
            this.numOfPeople = numOfPeople;
        }
    }
    class HairShop extends Shop {
        public HairShop(){
            super();
        }
        
        public boolean reserve(Customer customer){
	    // 예약 기준 : 1명 & 동일한 시간 예약불가
            if(customer.numOfPeople != 1)
                return false;
            
            Iterator<Customer> iter = reserveList.iterator();
            while (iter.hasNext()) {
                Customer r = iter.next();
		// 동일한 시간에 예약불가니깐 r시간 == 커스토머시간이면 false리턴 
                if(r.time == customer.time)
                    return false;
            }
	    // 예약 인원이 1명이고, 동일한 시간대가 아닐경우에 추가한다.
            reserveList.add(customer);
            return true;
        }
    }
    class Restaurant extends Shop {
        public Restaurant(){
            super();
        }
        
        public boolean reserve(Customer customer){
	// 예약기준 : 2-8명 & 1팀-2팀까지 동시 예약 가능
            if(customer.numOfPeople<2 || customer.numOfPeople>8)
                return false;
            int count = 0;
                        
            Iterator<Customer> iter = reserveList.iterator();
            while (iter.hasNext()) {
                Customer r = iter.next();
		// 고객정보가 2팀까지 같은 시간대 동시예약가능하기에 시간이 같으면 count증가
                if(r.time == customer.time)
                    count += 1;
            }
	    // 2팀 이상일 경우 false 리턴
            if(count >= 2)
                return false;
            reserveList.add(customer);
            return true;
        }
    }

    public int solution(int[][] customers, String[] shops) {
        Shop hairshop = new HairShop();
        Shop restaurant = new Restaurant();
        int count = 0;
        for(int i = 0; i < shops.length; i++){
            if(shops[i].equals("hairshop")){
                if(hairshop.reserve(new Customer(customers[i][0], customers[i][1], customers[i][2])))
                    count += 1;
            }
            else if(shops[i].equals("restaurant")){
                if(restaurant.reserve(new Customer(customers[i][0], customers[i][1], customers[i][2])))
                    count += 1;
            }
        }
        return count;
    }

    public static void main(String[] args) {
        Main sol = new Main();
        int[][] customers = {{1000, 2, 1},{2000, 2, 4},{1234, 5, 1},{4321, 2, 1}, {1111, 3, 10}};
        String[] shops = {"hairshop", "restaurant", "hairshop", "hairshop", "restaurant"};
        int ret = sol.solution(customers, shops);

        // [실행] 버튼을 누르면 출력 값을 볼 수 있습니다.
        System.out.println("solution 메소드의 반환 값은 " + ret + " 입니다.");
    }
}
```
