# Bigdata_Analysis(빅데이터 분석)
Factors of Local Population Decline ( 지방 인구 감소 요인 도출 )

## 프로젝트 명칭 : 데이터 분석, 시각화를 통한 지방의 인구 감소 요인 도출

### 주제 선정
인구 감소의 주요 요인으로 저출산, 고령화, 인구이동, 경제 중심의 변화 등으로 생각해냄.

경제 중심의 변화 중에서도 복지와 생계유지가 가장 중요한 요인으로 생각되어 일자리와 응급의료기관을 분석의 요인으로 설정함.

따라서 저출산과 고령화, 인구이동, 일자리, 응급의료기관 등의 데이터를 분석하기로 함.

####
1. 데이터 준비
   - 저출산과 고령화 : 지역별, 연령별 인구수 데이터를 활용하여 고령화에 포함된 나이의 인구와 유아기까지의 나이의 인구수 파악
   - 인구이동 : 지방 간 인구 이동 데이터를 분석하여 어느 지역으로 인구가 접입되고 전출되는지 파악
   - 일자리 : 지역별로 어떤 직업군이 존재하고 직업의 수, 일자리수는 어느 정도인지 파악
   - 응급의료기관 : 지역별 응급의료기관 현황을 조사하여 응급의료 서비스의 부족 지역 파악

2. 데이터 수집 (공공데이터포털, 국가통계포털 활용)
   - 저출산과 고령화 데이터 : 행정안전부_지역별(행정동) 성별 연령별 주민등록 인구수 데이터

     (https://www.data.go.kr/data/15097972/fileData.do#tab-layer-openapi)
   - 인구 이동 데이터 : 시군구별 이동자 수, 국내 인구 이동 통계 데이터

     (https://kosis.kr/statHtml/statHtml.do?orgId=101&tblId=DT_1B26001_A01&vw_cd=MT_ZTITLE&list_id=A_1&seqNo=&lang_mode=ko&language=kor&obj_var_id=&itm_id=&conn_path=MT_ZTITLE)
   - 일자리 데이터 : 시도별 직업별 취업자, 경제 활동 인구 조사 데이터

     (https://kosis.kr/statHtml/statHtml.do?orgId=101&tblId=DT_1DA7E34S&conn_path=I2)
   - 응급의료기관 데이터 : 보건복지부_시도별 응급의료기관 수 데이터  

     (https://www.data.go.kr/data/15044540/fileData.do#tab-layer-openapi)
   
3. 데이터보기
   - 데이터 유형 분석에 사용한 코드

     import pandas as pd (데이터 프레임을 사용하기 위한 판다스 라이브러리 불러오기)
     
     file_path = '~' (파일경로를 찾고 변수 file_path에 저장)
     
     df = pd.read_csv(file_path) (read_csv()함수로 데이터프레임 변환)
     
     df = pd.read_excel(file_path) (read_excel()함수로 데이터프레임 변환)
     
     df.dtypes (각 데이터의 항목의 데이터 타입 확인)

   - 저출산과 고령화 데이터
     
     : 데이터 유형은 이산형으로 기준 연월 시도명, 시군구명, 읍면동 명은 object 타입으로 문자나 날짜로 이루어져 있고 그 나머지 데이터 항목은 int 타입으로 해당하는 인구 수의 값으로 이루어져 있음.

   - 인구이동 데이터
     
     : 데이터 유형은 이산형으로 행정 구역별 데이터는 object 타입으로 문자이고 나머지 데이터는 int 타입으로 해당하는 인구 수의 값으로 이루어져 있음.

   - 일자리 데이터

     : 데이터 유형은 이산형으로 시도별, 직업별은 문자로 되어 있고 나머지 데이터는 int 타입으로 해당하는 일자리 수의 값으로 이루어져 있음. 

   - 응급의료기관 데이터
     
     : 데이터 유형은 이산형으로 지역별, 권역응급의료센터, 응급의료기관의 응급실 운영기관, 중앙응급의료센터는 obeject 타입이고 나머지 항목에 해당하는 수는 int타입으로 이루어져 있음.


4. 데이터 클린징
   - 데이터 클린징에 사용한 코드

     df.isnull().sum() (각 열의 결측치를 나타냄)

     df.dropna(axis=1) (열을 기준으로 결측치가 있는 항목을 삭제

   - 저출산과 고령화 데이터 : 결측치 24개 발생하여 결측치 열 제거
   - 인구이동 데이터 : 결측치 값 없음
   - 일자리 데이터 : 결측지 값 없음
   - 응급의료기관 데이터 : 결측치 값 없음

5. 데이터 탐색
   - 각각의 데이터에서 필요없는 열 삭제
   - 데이터 그룹화 진행 (시도명 기준)

     : 저출산(0세 ~ 6세), 고령(65세 ~ 110세)로 묶음

   - 각각의 데이터를 백분율로 표현

6. 데이터 시각화

   : 4개의 데이터를 한 그래프로 표현하였으나, 모든 데이터의 기준 수가 달라 각 데이터의 실제 값을 기준으로 지역 비교의 데이터 시각화 진행함.
<img width="1045" alt="스크린샷 2023-07-11 오전 12 16 40" src="https://github.com/Seong-A/Bigdata_Analysis/assets/83965377/019586b5-4cc9-4b32-a33a-6561a6bdbd1a">

7. 통계 분석 및 결론 -통계분석의 방법

   : 상관분석(두 변수 간에 어떤 선형적 관계를 가지는지 분석하는 기법)

   - 데이터들의 귀무가설, 대립가설
 
   |데이터|가설|내용|
   |:---:|:---:|:---:|
   |고령화|귀무가설|고령화 수와 지방인구 감소는 서로 독립적이다.|
   |고령화|대립가설|고령화 수와 지방인구 감소오는 관련성이 있다.|
   |저출산|귀무가설|출산 수와 지방인구 감소는 서로 독립적이다.|
   |저출산|대립가설|출산 수와 지방인구 감소는 관련성이 있다.|
   |인구이동|귀무가설|지역별 인구 이동 수와 지방인구 감소는 서로 독립적이다.|
   |인구이동|대립가설|지역별 인구 이동 수와 지방인구 감소는 관련성이 있다.|
   |일자리|귀무가설|일자리 수와 지방인구 감소는 서로 독립적이다.|
   |일자리|대립가설|일자리 수와 지방인구 감소는 관련성이 있다.|
   |응급의료기관|귀무가설|응급의료기관 수와 지방인구 감소는 서로 독립적이다.|
   |응급의료기관|대립가설|응급의료기관 수와 지방인구 감소는 관련성이 있다.|

   - 유의수준 설정    : 0.05로 설정

   ( 5% 이하의 유의확률을 가지면 귀무가설을 기각하고 대립가설을 채택하며, 5% 이상의 유의확률을 가지면 대립가설을 기각하고 귀무가설을 채택. )

   - 상관계수 계산 & 유의확률 구하기    : 피어슨 상관계수 사용 ( stats.pearsonr 함수 사용하여 각각 데이터들의 상관계수와 유의확률 계산
     
   - 결론
     
   ![Pasted Graphic](https://github.com/Seong-A/Bigdata_Analysis/assets/83965377/b7ff1f43-725a-4325-8891-1105bbe2463d)

   : 모든 데이터의 유의확률이 유의수준(0.05) 이하의 값을 가지므로 모든 귀무기설을 기가하고 대립가설 채택. 
