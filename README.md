# 범죄유형과 범죄 특징에 대한 분석자료_230216

![img1](https://user-images.githubusercontent.com/122436389/219274089-cf052351-7d92-41f5-a000-aa1d530a3bab.png)
![img3](https://user-images.githubusercontent.com/122436389/219275719-7ff2a8e2-787b-40ab-8466-b9bde8ec6100.png)
![img2](https://user-images.githubusercontent.com/122436389/219276737-610afa05-d03f-46ba-9e24-c22bde75a61f.png)

``` pyton
for i in data:
    if '살인' in i[0]:
        for x in i[1:]:
            sal.append(int(x))
    if '성폭력' in i[0]:
        for j in i[1:]:
            sung.append(int(j))
    if '마약' in i[0]:
        for z in i[1:]:
            ma.append(int(z))


```
