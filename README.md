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

   - 저출산과 고령화 데이터 :
   
   





