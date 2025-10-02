1. 통계 원소스 (CSV 형식)
제공된 자료의 표 1, 2, 3, 4에 있는 데이터를 컴퓨터가 읽기 쉬운 CSV 형식으로 재구성한 내용입니다. 이 데이터를 복사하여 파일로 저장하거나 코드에 직접 사용할 수 있습니다.
A. OTT 서비스 플랫폼의 애니메이션 작품 선호도 교차표
Platform,Short,Feature,TV_Series,OTT_Original
웨이브,5,5,4,0
넷플릭스,15,30,45,9
왓챠,8,6,14,0
라프텔,5,9,25,0
애니플러스,1,2,3,1
디즈니+,0,9,2,0
티빙,3,1,1,0
B. 서사적 가치 빈도분석표
Factor,Frequency,Percentage
캐릭터 성격 설정,32,15.8
기승전결의 구조,57,28.1
스토리의 주제,32,15.8
전달 메세지,17,8.4
사건의 인과성,15,7.4
소재의 참신성,31,15.3
캐릭터의 행동동기,19,9.4
C. 심미적 가치 빈도분석표
Factor,Frequency,Percentage
캐릭터의 디자인,57,28.1
배경 디자인,3,1.5
장면연출,67,33.0
사운드 활용,8,3.9
캐릭터의 움직임,4,2.0
그림체(작화),64,31.5
D. 오락적 가치 빈도분석표
Factor,Frequency,Percentage
즐거움과 재미,81,39.9
독특하고 자극적인 것,26,12.8
몰입감,86,42.4
공감성,4,2.0
여가적 욕구 충족,6,3.0

--------------------------------------------------------------------------------
2. Pandas를 이용한 ipynb 파일 생성 코드
아래 코드를 Jupyter Notebook의 셀에 복사하여 실행하면, 위에서 재구성한 통계 원소스를 바탕으로 Pandas 데이터프레임이 생성되고 표 형태로 출력됩니다.
# %% [markdown]
# # OTT 서비스 애니메이션 콘텐츠 이용 현황 분석 데이터
# 
# 이 노트북은 "Over The Top 서비스의 애니메이션 콘텐츠 이용 현황 분석" 자료에 수록된 통계 데이터를 Pandas DataFrame으로 변환하여 분석하는 것을 목표로 합니다.
# 
# 데이터 출처:
# - 박수경, 이태구. (2023). Over The Top 서비스의 애니메이션 콘텐츠 이용 현황 분석. JCCT, 9(2), 445-450.

# %%
# 필요한 라이브러리를 가져옵니다.
import pandas as pd
import io

# %% [markdown]
# ### 1. OTT 플랫폼별 애니메이션 작품 선호도
# 
# 자료의 [표 1]에 해당하는 데이터로, 각 OTT 플랫폼 이용자들이 선호하는 애니메이션 작품 유형(단편, 장편, TV 시리즈, OTT 오리지널)을 보여줍니다 [1].

# %%
# [표 1] 데이터를 CSV 형식의 문자열로 정의합니다.
ott_preference_data = """Platform,Short,Feature,TV_Series,OTT_Original
웨이브,5,5,4,0
넷플릭스,15,30,45,9
왓챠,8,6,14,0
라프텔,5,9,25,0
애니플러스,1,2,3,1
디즈니+,0,9,2,0
티빙,3,1,1,0
"""

# io.StringIO를 사용하여 문자열 데이터를 파일처럼 읽어 DataFrame을 생성합니다.
df_ott_preference = pd.read_csv(io.StringIO(ott_preference_data))

# 생성된 DataFrame을 출력합니다.
# Jupyter Notebook에서는 display() 함수를 사용하면 더 깔끔한 표 형태로 출력됩니다.
print("--- [표 1] OTT 플랫폼별 애니메이션 작품 선호도 [1] ---")
display(df_ott_preference)

# %% [markdown]
# ### 2. 애니메이션 선호유형별 특징 (빈도분석)
# 
# 자료의 [표 2, 3, 4]에 해당하는 데이터로, 시청자들이 애니메이션을 시청할 때 고려하는 요인을 서사적, 심미적, 오락적 가치로 나누어 빈도분석한 결과입니다 [2, 3].

# %%
# [표 2] 서사적 가치 빈도분석표 데이터 [2]
narrative_value_data = """Factor,Frequency,Percentage
캐릭터 성격 설정,32,15.8
기승전결의 구조,57,28.1
스토리의 주제,32,15.8
전달 메세지,17,8.4
사건의 인과성,15,7.4
소재의 참신성,31,15.3
캐릭터의 행동동기,19,9.4
"""
df_narrative_value = pd.read_csv(io.StringIO(narrative_value_data))

print("\n--- [표 2] 서사적 가치 고려 요인 [2] ---")
display(df_narrative_value)


# [표 3] 심미적 가치 빈도분석표 데이터 [2, 3]
aesthetic_value_data = """Factor,Frequency,Percentage
캐릭터의 디자인,57,28.1
배경 디자인,3,1.5
장면연출,67,33.0
사운드 활용,8,3.9
캐릭터의 움직임,4,2.0
그림체(작화),64,31.5
"""
df_aesthetic_value = pd.read_csv(io.StringIO(aesthetic_value_data))

print("\n--- [표 3] 심미적 가치 고려 요인 [2, 3] ---")
display(df_aesthetic_value)


# [표 4] 오락적 가치 빈도분석표 데이터 [3]
entertainment_value_data = """Factor,Frequency,Percentage
즐거움과 재미,81,39.9
독특하고 자극적인 것,26,12.8
몰입감,86,42.4
공감성,4,2.0
여가적 욕구 충족,6,3.0
"""
df_entertainment_value = pd.read_csv(io.StringIO(entertainment_value_data))

print("\n--- [표 4] 오락적 가치 고려 요인 [3] ---")
display(df_entertainment_value)
이 코드는 원본 자료에 나타난 통계표들을 디지털 데이터로 변환하여 추가적인 분석이나 시각화를 할 수 있는 기반을 마련해 줍니다. 예를 들어, 이 데이터프레임들을 이용해 막대그래프를 그리거나 플랫폼별 선호도 비율을 계산하는 등의 작업을 수행할 수 있습니다.