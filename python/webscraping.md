# Web Scraping

> Request, Beautifulsoup 모듈을 이용한 스크래핑



### 1. 요청 보내기

```python
url = <>
req_header = {
    'user-agent' : <>
}

res = requests.get(url, headers=req_header)
print(res.status_code)
```



### 2. soup 파싱하기

```python
html = res.text
soup = BeautifulSoup(html, 'html.parser')
#print(soup)

#find() 함수 사용
title = soup.find('title')
print(type(title), title, title.string, title.text)
```



태그 `$=` 표시 

- 해당하는 태그이름으로 끝나는 것을 선택

- search로 정규표현식 패턴 검색 가능