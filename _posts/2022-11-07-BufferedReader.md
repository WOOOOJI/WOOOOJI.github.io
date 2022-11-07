---
layout: single
title:  "BufferedReader 사용해서 사친역산 프로그래밍"
---

```
try {
		ArrayList<Integer> list = new ArrayList<Integer>();
		BufferedReader bf = new BufferedReader(new InputStreamReader(System.in));
		
//			String s = bf.readLine();   // 문자열로 입력받은 값을 s변수에 담아준다.
		
			StringTokenizer st = new StringTokenizer(bf.readLine());
			
			while(st.hasMoreTokens()) {
				list.add(Integer.parseInt(st.nextToken()));
			}
			
			int hap=0;
			int avg=0;
			
			
			for(int i=0; i<list.size(); i++) {
				System.out.print(list.get(i)+" ");
				hap+=list.get(i);
			}
			
			avg=hap/list.size();	
			System.out.println();
			System.out.print(hap+" ");
			System.out.print(avg);
		
		} catch (IOException e) {
			// TODO Auto-generated catch block
			e.printStackTrace();
		}
```

## 완성본이다.  물론 처음부터 이렇게 짰다면 얼마나 좋았을까 ㅋ....

 

 

#### 일단 코드를 짜기전에 먼저 계획을 세웠다.

- Scanner 를 절대 사용하지 않고 짤것
  - **ArrayList배열을 사용하기.**
  - **split이 아닌 StringTokenizer 를 사용하기.**
  - **반복문은 최대 2번까지 허용.**

 

### 자 이제 코드를 짜기전에 기본적으로 BufferedReader에 대해 알아보고 가자.

 

 

 

#### **일단 BufferedReader을 왜 쓸까?**

처음에 자바를 배우게 되면 Scanner를 이용하여 입력받을 데이터값의 자료형을 설정하여 편하게 받고 그것을 썼다.

ex( 입력받은값을 연산으로 진행 할려면 .nextInt();  or 성적평균을 입력받기 위해 float,double => nextFloat();

 

이렇게 단순하고 편하게 입력을 받고 그것을 갔다 썼는데 왜 **BufferedReader를** 쓰는지에 대해 의문점이 매우 크게 생겼다.

왜냐하면 **Scanner 같은 경우에는** 별도로 자료형을 변환 해줄 필요도 없고, 개행문자와 공백을 기준으로 데이터 입력값을 인식을 한다.

하지만 **BufferedReader 같은 경우에는** 모든 데이터를 문자열로 입력받고 문자열로 가져와서 필요시에 무조건 자료형변환을 해줘야 하며, 개행문자만을 데이터입력값의 기준이 되기 때문에 데이터를 나눠줘야 한다.

 

검색해본 결과는 다음과 같다.

 

 

**BufferedReader를 사용하면 입력받은 데이터값을 버퍼에 담아뒀다가 버퍼의 크기를 넘어가거나 개행문자가 입력이 되면 한번에 데이터를 전송해준다.**

 

 

**그 외 버퍼를 사용하지 않는 입력문 (Input)은 모두 한 데이터(byte 한 글자) 를 입력 받을때마다 바로바로 데이터를 전송한다.**

 

 

 

 

 

 

 

#### **아니  그러면 당연히 바로바로 데이터를 빠르게 전송해주는게 좋은거 아냐??** 

#### **라고 생각했다.....**

####  

**하지만 알고있는것과 다르게 데이터의 입출력을 키보드로 입력받아 전송하는 시간이 꽤 걸린다는것이였고, 또한 하드디스크 속도 또한 처리하는게 상대적으로 느리기 때문에 차라리 버퍼에 내용을 담아 한번에 전송해주는것이 훨씬 빠르다는**

**결론이였다.**

 

 

 

 

 

##  

## **자 이제 왜 쓰는지 알았으니 이것으로 어떻게 해야지 연산을 할 수 있는 프로그래밍을 짤 수 있을지 고민해보고 만들어보겠다.**

 

 

 

 

 

 

 

 

 

### **일단 BufferedReader 를 사용하기 위해서는 선행문이 다음과 같아야 한다.**

```
BufferedReader bf = new BufferedReader(new InputStreamReader(System.in));
```

 

 

***\*BufferedReader\**** 클래스에서 인스턴스를 생성하여 사용할 준비를 해놓는다.

 

 

 

 

 

 

 

 

```
StringTokenizer st = new StringTokenizer(bf.readLine());
			
			while(st.hasMoreTokens()) {
				list.add(Integer.parseInt(st.nextToken()));
			}
```

 

저는 문자열을 토큰화 시켜서 나누고 그것을 ArrayList배열에 While문을 이용하여 토큰이 없을때까지 담아줬다.

 

좀더 쉽게 풀이 해보자면 :

일단

**StringTokenizer st = new StringTokenizer(bf.readLine());**

사용하여 토큰화 시킬 수 있게 **StringTokenizer를 인스턴스화 시켰다.**

그리고 나서 매개변수 값으로 **bf.readLine();** 을 받았는데, 여기서 **bf**는 위에서 **BufferedReader를 선언했을때 인스턴스의 명이다.**

그리고나서 인스턴스 bf 를 이용하여 **BufferedReader** 클래스의 메소드인 **readLine**을 호출한 것이다.

#### *( readLine을 사용하기 위해서는 무조건!!!!!  try-catch문을 사용하여 에러를 잡아줘야한다 필수이다...)*

 

readLine에서 입력받은 값이 토큰 단위로 **StringTokenizer 인스턴스 객체에 저장이 된 것이다.**

그 다음에 while문을 이용하여 st.hasmoreTokens ( 토큰이 남아있지 않을때 까지 반복) 하여 미리 만들어둔 ArrayList에 add를 사용하여 토큰 하나하나를 입력 받았다. 주의 해야할 점은 여기보면 Integer로 형변환을 해주었다. 앞서 말했듯이 모든 **BufferedReader는** 자료형을 문자열로만 받아오기 때문이다.

 

 

자 그러면 여기서 간단하게 먼저 BufferedReader의 메소드를 먼저 보고 가면 이해하기 쉬울거다.

 

 



![img](https://k.kakaocdn.net/dn/SUe6f/btrQq4EKakc/LXPr1eQ8NhBpJJuSfNnEX0/img.png)



**자바 API에서 그대로 가져온 것이다. 해석 가능할 것이라고 믿습니다 ><!!**

 

 

 

 

 

```
			int hap=0;
			int avg=0;
			
			
			for(int i=0; i<list.size(); i++) {
				System.out.print(list.get(i)+" ");
				hap+=list.get(i);
			}
```

 

그 다음!! hap이라는 총점을 할당할 변수와 avg라는 총점 평균을 담아줄 변수를 생성했다.

**이걸 바로 앞에 와있는 for문 뒤에 선언하면 총점을 받아줄 변수가 없기에 주의하자.**

 

 

**for문을** 활용하여 list에 넣어주었던 형변환이 되있는 숫자들을 **인덱스0 번부터 list.size만큼 반복해서 차례대로 호출**해서 

그 값을 hap변수에 계속 저장을 해주었다.

 

그 이후로는 간단하다.

```
			avg=hap/list.size();	
			System.out.println();
			System.out.print(hap+" ");
			System.out.print(avg);
```

 

평균을 구하고 총점이랑 각각 담겨져 있는 변수를 출력해주었다.

 

끗.

 

 

 

 

 

 

 

 

 

 

## 사실 이렇게만 생각하면 참 쉬운데 실제로 코드를 짜다보니 삽질이 발생했다....  :(

 

 

**ArrayList의 메소드중 add랑 set을 헷갈리지 않나**....( 최근에 게터세터 연습을 좀 한다고 지x 했다가 갑을 넣어준다는걸 계속 set을 썼다 )ㅋ.........

 

토큰이 없을때까지 반복문을 사용해서 값을 저장하는데 for문을 써서 범위값 선정에서 해매질 않나.....

또 하필 api를 잘 안읽어보고 **StringTokenizer의 메소드중 토큰의 개수를 숫자로 표현**하는게 있어서 범위로 사용했는데,

진짜 알고나서 너무 바보 같았던게, **토큰 하나씩 반복문을 이용해서 list에 add 해주는데 그러면 자연스럽게 반복문 할때 마다 토큰의**

**개수가 1개씩 줄어든다는것이닼ㅋㅋㅋㅋㅋㅋㅋㅋㅋㅋ**

 

 

### 에휴...그러다보니 반복문이 예상보다 1개씩 일찍 끝나서 어?????? 왜이러지?????

### 라고 생각을 한시간동안 했다.

###  

###  

###  

### 난 바보다><
