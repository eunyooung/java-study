# Java I/O 개념
- 자바는 내부적으로 (메모리 상에서) 문자열이 UTF-16으로 인코딩
    - 자바는 인코딩할때 NULL문자가 나타나지 않기 위해서 UTF-16 사용
    - **UTF-8 과 UTF-16 의 차이**
    	- UTF-8: 영어는 **1Byte**, 한글은 **3Byte**
    	- UTF-16: 거의 모든 문자가 **2Byte**
- 문자열 송/수신시 직렬화가 필요할땐 UTF-8을 사용
- 문자열 입출력시 운영체제 기본 인코딩 값 또는 사용자가 지정한 인코딩 값으로 문자열을 인코딩
- java.io 구조

![img](https://user-images.githubusercontent.com/70963337/147564923-036d2c77-29bb-41f1-bd35-c0b4345c3ad8.png)

</br>

### 바이트기반(8bits)의 데이터 처리 : **_InputStream, OutputStream_**
### 캐릭터 기반(유니코드)의 문자열 데이터 처리 : **_Reader, Writer_**

</br>

### **InputStream**
- 2byte 이상으로 구성되어있는 인코딩은 1byte 값만 읽고 나머지는 스트림에 남아있기 때문에 출력할때는 1byte에 대한 인코딩 값을 10진수로 변환한 값만 출력되므로 한글이 깨짐

### **InputStreamReader**
- InputStream의 한글 깨짐의 원인인 바이트 단위로 읽어들이는 형식을 문자단위로 변환시키는 중개자 클래스

### **FileReader**
- 인코딩 지정은 Java11 버전 이후에서부터 제공
- java.io.InputStreamReader 클래스를 상속받기때문에 read()메소드를 사용 하여 char 단위로 읽어옴.
- 출력 예제

``` java
int ch;
while ((ch = reader.read()) != -1) {
    System.out.print((char) ch);
}
```

### **BufferedReader**
- 버퍼를 사용해서 FileReader보다 효율적임
- FileReader나 InputStreamReader 등 다른 Reader 객체 전달 가능
- readLine(0 메소드는 텍스트 파일을 할줄씩 읽어서 리턴. 읽을 내용이 없으면 null 리턴
- 출력 예제

``` java
String str;
while ((str = reader.readLine()) != null) {
    System.out.println(str);
}
```

