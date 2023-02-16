# 범죄유형과 범죄 특징에 대한 분석자료_230216

![주제선정](https://user-images.githubusercontent.com/122436389/219285584-54176a6b-31ca-40aa-81d3-cd2900a2941a.PNG,width="550px" height="500px")   
![정보확인](https://user-images.githubusercontent.com/122436389/219286075-6bfd91da-d4d4-4601-9b94-0d172d2e7c86.PNG)
```
😲조사에 따른 2가지 사실
✔ 성범죄의 비율이 높고, 교육수준이 높을 수록 범죄 비율이 낮아진다는 분석을 토대로
  범죄자를 대상으로 하는 교육이 , 범죄율을 낮출 수 있으리라 기대할 수 있다.
✔ 이에 재소자들을 대상으로 하는 인문학 또는 심리상담 등을 제안할 수 있다.
```
![요일](https://user-images.githubusercontent.com/122436389/219280617-f59c34c4-ec08-4053-8981-55ce19ba89a8.png)
```
🌞자료 활용 방안(2)
1. 보안업체에서 CCTV 등 보안 상품을 판매하기 위한 참고 자료로 사용 가능
2. 시,도,군으로 세부 조사 할 경우, 지자체의 순찰 강화, 범죄 예방 캠패인 등 요청 시

✅추후 업데이트
- 범죄자 직업 취합자료를 바탕으로 원인이 될 만한 데이터와 연결시켜 좀 더 의미있는 자료로 활용.
- 원인 ex ) 근무자 스트레스, 학생 스트레스 등
```
``` python
import csv
f = open("C:\\Users\\a13\\Desktop\\web\\day33\\범죄발생_요일_2019.csv",encoding='euc-kr')
data = csv.reader(f)
sal = []
sung = []
ma = []
day = ['월요일','화요일','수요일','목요일','금요일','토요일','일요일']

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

import matplotlib.pyplot as plt
import numpy as np
from matplotlib import font_manager, rc
font_path = "C:\Windows\Fonts\H2GTRM.TTF"
font = font_manager.FontProperties(fname=font_path).get_name()
rc("font", family = font)

x = np.arange(0,7)

fig, (ax1, ax2) = plt.subplots(2,1)
fig.subplots_adjust(hspace=0.05)
ax1.set(title='요일별 범죄건수')
ax1.plot(x,sung,c ="red", label="성폭행")
ax2.plot(x,sal,label="살인")
ax2.plot(x,ma,label="마약")
ax1.legend()


plt.xticks(x, day)
plt.legend()
plt.show()
```
![교육](https://user-images.githubusercontent.com/122436389/219280628-72082b23-7422-4ca4-82d6-90eedc9614b1.png)
``` python
import matplotlib.pyplot as plt
import numpy as np
import csv
from matplotlib import font_manager, rc
font_path = "C:\Windows\Fonts\H2GTRM.TTF"
font = font_manager.FontProperties(fname=font_path).get_name()
rc("font", family = font)
with open(r"C:\Users\a13\Desktop\web\day33\범죄자_교육정도_2019.csv",encoding="cp949") as f:
    data = csv.reader(f)
    a = []
    sort_edu = []
    for i in data:
        # print(i)
        a.append(i)
    for i in range(len(a[0])):
        sort_edu.append(a[0][i])
# i[1] i[16]부터
kill = a[1][:]
kill1 = []
assult = a[2][:]
assult1 = []
drug = a[3][:]
drug1 = []
sort_edu.remove("범죄분류")
assult.remove("성폭력")
kill.remove("살인")
drug.remove("마약류관리에관한법률(마약)")
for i in kill:
    kill1.append(int(i))
for i in assult:
    assult1.append(int(i))
for i in drug:
    drug1.append(int(i))

print(type(kill))

x = np.arange(0,19,1)

fig, (ax1, ax2) = plt.subplots(2,1, sharex=True)
fig.subplots_adjust(hspace=0.05)
ax1.plot(x,assult1,c ="red", label="성폭행")
ax2.plot(x,kill1,label="살인")
ax2.plot(x,drug1, label="마약")


plt.xticks(x, sort_edu, rotation=45)
ax1.set(title='범죄자의 교육정도')
ax1.legend()
plt.legend()
plt.show()
```
![직업](https://user-images.githubusercontent.com/122436389/219279920-b2695a29-ece7-4799-9c22-8c6ebcb79a7f.png)
``` python
import csv
f = open("C:\\Users\\a13\\Desktop\\web\\day33\\범죄자_직업_2019.csv",encoding='euc-kr')
data = csv.reader(f)
import matplotlib.pyplot as plt
import numpy as np
from matplotlib import font_manager, rc
font_path = "C:\Windows\Fonts\H2GTRM.TTF"
font = font_manager.FontProperties(fname=font_path).get_name()
rc("font", family = font)

crime = ['살인','성폭행','마약']
job = []

results = np.array([
[3,0,12,2,2,28,1,1,0,58,1,3,12,66,54,1,0,2,5,0,5,13,4,0,16,13,0,1,395,
244],
[75,72,280,84,103,727,166,105,8,5525,39,90,288,904,1982,149,14,54,118,
23,124,869,420,4,4633,49,14,83,6961,5249],
[2,1,9,2,12,25,6,6,0,228,1,18,15,84,136,44,0,3,7,1,48,82,2,4,143,89,1,
6,1150,614]
])

for i in data:
    if '범죄분류' in i[0]:
        for x in i[1:]:
            job.append(x)
        print(job)

fig, ax = plt.subplots()
im = ax.imshow(results)

ax.set_xticks(np.arange(len(job)))
ax.set_xticklabels(job)
ax.set_yticks(np.arange(len(crime)))
ax.set_yticklabels(crime)

plt.setp(ax.get_xticklabels(), rotation=45, ha="right",
         rotation_mode="anchor")

for i in range(len(crime)):
    for j in range(len(job)):
        text = ax.text(j, i, results[i, j],
                       ha="center", va="center", color="w")

ax.set_title("범죄자 직업")

fig.tight_layout()
plt.show()
```
```
★참고 자료★
1. 범죄 관련 자료 수집
공공데이터포털 https://www.data.go.kr/
2. csv 파일 연결
https://formal.hknu.ac.kr/Gongsu-DataSci/notebooks/GongSu12_CSV_File_Data_Visualization.html
3. 다단 그래프 그리기
https://techreviewtips.blogspot.com/2017/10/subplot.html
```
