## 编程题答案
### 回行数
- 方式一
```java
public class RectangleTest {
public static void main(String[] args) {
Scanner scanner = new Scanner(System.in);
System.out.println("输入一个数字");
int len = scanner.nextInt();
int[][] arr = new int[len][len];
int s = len * len;
/*
* k = 1:向右
* k = 2:向下
* k = 3:向左
* k = 4:向上
 */
int k = 1;
int i = 0,j = 0;
for(int m = 1;m <= s;m++){
if(k == 1){
if(j < len && arr[i][j] == 0){
arr[i][j++] = m;
}else{
k = 2;
i++;
j--;
m--;
}
}else if(k == 2){
if(i < len && arr[i][j] == 0){
arr[i++][j] = m;
}else{
k = 3;
i--;
j--;
m--;
}
}else if(k == 3){
if(j >= 0 && arr[i][j] == 0){
arr[i][j--] = m;
}else{
k = 4;
i--;
j++;
m--;
}
}else if(k == 4){
if(i >= 0 && arr[i][j] == 0){
arr[i--][j] = m;
}else{
k = 1;
i++;
j++;
m--;
}
}
}
//遍历
for(int m = 0;m < arr.length;m++){
for(int n = 0;n < arr[m].length;n++){
System.out.print(arr[m][n] + "\t");
}
System.out.println();
}
}
}
```
- 方式二
```java
//方式 2
/*
01 02 03 04 05 06 07
24 25 26 27 28 29 08
23 40 41 42 43 30 09
22 39 48 49 44 31 10
21 38 47 46 45 32 11
20 37 36 35 34 33 12
19 18 17 16 15 14 13
*/
public class RectangleTest1 {
public static void main(String[] args) {
int n = 7;
int[][] arr = new int[n][n];
int count = 0; //要显示的数据
int maxX = n-1; //x 轴的最大下标
int maxY = n-1; //Y 轴的最大下标
int minX = 0; //x 轴的最小下标
int minY = 0; //Y 轴的最小下标
while(minX<=maxX) {
for(int x=minX;x<=maxX;x++) {
arr[minY][x] = ++count;
}
minY++;
for(int y=minY;y<=maxY;y++) {
arr[y][maxX] = ++count;
}
maxX--;
for(int x=maxX;x>=minX;x--) {
arr[maxY][x] = ++count;
}
maxY--;
for(int y=maxY;y>=minY;y--) {
arr[y][minX] = ++count;
}
minX++;
}
for(int i=0;i<arr.length;i++) {
for(int j=0;j<arr.length;j++) {
String space = (arr[i][j]+"").length()==1 ? "0":"";
System.out.print(space+arr[i][j]+" ");
}
System.out.println();
}
}
}
```