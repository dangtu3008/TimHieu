## Prority Queue
- Là một loại `container adaptor`.
>- Containers chứa các class về cấu trúc dữ liệu.
>- Container adaptor là các container được sử dụng cho các cấu trúc lưu trữ đặc biệt

- Được thiết kế đặc biệt để phần tử ở đầu luôn luôn lớn nhất so với các phần tử khác.
- Nó giống như một heap, mà ở đây là heap max, tức là phần tử có độ ưu tiên lớn nhất có thể được lấy ra và các phần tử khác được chèn vào bất kì.

>Heap thực chất là một cây cân bằng thỏa mãn các điều kiện sau  
>1. Một nút có không quá 2 nút con.  
>2. Với Heap Max thì nút gốc là nút lớn nhất, mọi nút con đều không lớn hơn nút cha của nó. Với Heap Min thì ngược lại.  
>- Nguồn: [Heap](https://yeulaptrinh.pw/category/ctdl/heap/). 
- Để khai báo `Prority Queue` dùng  `#include <queue>`.
- Dạng 1 (sử dụng phép toán mặc định là less)
```
priority_queue <int> pq;
```
- Dạng 2 (sử dụng phép toán khác)
```
priority_queue <int,vector<int>,greater<int> > q; //phép toán greater
```
## Các hàm thành viên
- size: trả về kích thước hiện tại của priority queue. ĐPT O(1)
- empty: true nếu priority queue rỗng, và ngược lại. ĐPT O(1).
- push: đẩy vào priority queue. ĐPT O(logN).
- pop: loại bỏ phần tử ở đỉnh priority queue. ĐPT O(logN).
- top: trả về phần tử ở đỉnh priority queue. ĐPT O(1).
>ĐPT: Độ phức tạp O.
### Size
```
#include <iostream>
#include <queue>
using namespace std;
int main()
{
    priority_queue<int> myPriorityQueue;
    for(int i =0 ; i < 5; i++) {
        myPriorityQueue.push(100) ; // 100 100 100 100 100
    }
    cout << "The size of priority_queue is: " << myPriorityQueue.size()<< endl;
    return 0;
}
```
- Chú ý:
1. Prority Queue không cho phép khai báo phần tử rỗng.
2. Không thể khai báo như dưới để lấy 5 phần tử Prority Queue có 5 phần tử 100.
```
priority_queue <int> myPriorityQueue (5,100)
```
### Empty
```
#include <iostream>
#include <queue>
using namespace std;
int main()
{
    priority_queue<int> myPriorityQueue ;
   if( myPriorityQueue.empty()) {
        cout<<"priority_queue is empty! "<<endl ;
   }
   else {
        cout<<"priority_queue is not empty! "<<endl ;
   }
    return 0;
}
```
### Top
```
#include <iostream>
#include <queue>
using namespace std;
int main()
{
    priority_queue<int> myPriorityQueue ;
    // creat priority_queue
    myPriorityQueue.push(5) ;
    myPriorityQueue.push(3) ;
    myPriorityQueue.push(2) ;
    myPriorityQueue.push(4) ;
    myPriorityQueue.push(1) ;
    // print priority_queue
   while(!myPriorityQueue.empty()) {
    cout<<myPriorityQueue.top()<<" "  ;
    myPriorityQueue.pop() ;
   }
    return 0;
}
```
- Nhận xét: Mặc dù thứ tự ta cho vào priorty_queue là 5,3,2,4,1 không được sắp xếp, tuy nhiên, khi in ra kết quả, ta có thứ tự giảm dần 5,4,3,2,1(Độ ưu tiên là in số lớn nhất, vì độ ưu tiên mặc định là less).
### Push
```
#include <iostream>
#include <queue>
using namespace std;
int main()
{
    priority_queue<int> myPriorityQueue;
    int n;  // size of queue
    cout<<"Size: " ;
    cin>>n ;
    // create queue
    int tempNumber  ;
    for(int i = 0 ; i<n; i++) {
        cin>>tempNumber ;
        myPriorityQueue.push(tempNumber) ;
    }
    // print queue
    for(int i = 0 ; i<n; i++) {
        tempNumber = myPriorityQueue.top() ;
        myPriorityQueue.pop();
        cout<<tempNumber<<" " ;
    }
    return 0;
}
```
### Pop
```
#include <iostream>
#include <queue>
using namespace std;
int main()
{
    priority_queue<int> myPriorityQueue;
    int n; // size of priority_queue
    cout<<"Size: " ;
    cin>>n ;
    // create priority_queue
    int tempNumber  ;
    for(int i = 0 ; i<n; i++) {
        cin>>tempNumber ;
        myPriorityQueue.push(tempNumber ) ;
    }
    // delete element
     for(int i = 0 ; i<n/2; i++) {
        myPriorityQueue.pop() ;
    }
    // print priority_queue
    n = myPriorityQueue.size() ; // after using pop(), the size of priority_queue < n
    for(int i = 0 ; i<n; i++) {
        tempNumber = myPriorityQueue.top() ;
        myPriorityQueue.pop();
        cout<<tempNumber<<" " ;
    }
    return 0;
}
```
## Chương trình demo
```
#include <iostream>
 
#include <queue>
 
#include <vector>
 
using namespace std;
 
main() {
 
    priority_queue <int> p;	// p={}
 
    p.push(1);	// p={1}
 
    p.push(5);	// p={1,5}
 
    cout << p.top() << endl; // In ra 5
 
    p.pop();	// p={1}
 
    cout << p.top() << endl; // In ra 1
 
    p.push(9);	// p={1,9}
 
    cout << p.top() << endl; // In ra 9
 
    system("pause");
 
}
```