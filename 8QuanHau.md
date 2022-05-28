# Đặt 8 quân hậu vào trong bàn cờ

### Ý tưởng.

Ta dùng các mảng (cột, đường chéo chính, đường chéo phụ) để lưu các giá trị 0,1. 1 tương ứng với cột hoặc đường chéo đó chưa được sử dụng, còn 0 thì ngược lại.

Với công thức để tính index của đường chéo chính là i-j+n 
còn với đường chéo phụ là i+j-1.
![index](https://ibb.co/PWTHxt4)

Ta sẽ kiểm tra theo từng hàng với biến i sau đó kiểm tra trên tất cả các cột của hàng đó xem vị trí đó có thỏa hay không nếu thỏa thì đặt quân hậu vào, gán các giá trị cho đường chéo và cột bằng 0 và gọi đệ quy lại hàm với i+1. Khi i=8 thì dừng và in ra kết quả. Sau đó gán lại các giá trị cột và đường chéo vừa thay đổi thành 1 để thực hiện trường hợp kế tiếp.
### code

```cpp
#include <iostream>
using namespace std;
int cot[100], d1[100], d2[100],n=8, x[100],count=0;
void print(){
    for(int i=1;i<=n;i++){
        cout<<x[i]<<" ";
    }
    cout<<endl;
    count++;
}

void dat_quan_hau(int i){
    for(int j=1;j<=n;j++){
        if(cot[j]==1 &&d1[i-j+n]==1 && d2[i+j-1]==1){
            x[i]=j;
            cot[j]=0; d1[i-j+n]=0;d2[i+j-1]=0;
            if(i==n){
                print();
            }
            else {
                dat_quan_hau(i+1);
            }
            cot[j]=1; d1[i-j+n]=1;d2[i+j-1]=1;

        }
    }
}
int main(){
    for(int i=1 ;i<=99;i++){
        cot[i]=1;
        d1[i]=1;
        d2[i]=1;
    }
    dat_quan_hau(1);
    cout<<endl<<count;
    return 0;
}
```