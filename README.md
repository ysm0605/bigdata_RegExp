정규 표현식(RegExp)에 대한 설명과 예제를 통한 학습.

<h3>정규 표현식</h3>
정규 표현식(Regular Expression, RegExp)은 문자열의 패턴을 표현하기 위한 형식 언어로 문자열 검색, 추출, 대체, 유효성 검사 등 다양한 문자열 처리 작업을 수행하는 데에 사용됩니다.

<h3>정규 표현식 특징</h3>
- 특정한 패턴을 나타내는 문자열을 일괄적으로 처리하거나, 특정한 패턴에 대한 검색 또는 추출을 쉽게 수행할 수 있습니다.<br>
- 다양한 프로그래밍 언어와 텍스트 편집기에서 지원되므로, 문자열 처리 작업에 유용하게 활용할 수 있습니다.
 
<h3>-정규표현식 매칭 패턴(문자, 숫자, 기호 등)</h3>

a-z : 영어알파벳 (소문자)(-으로 범위 지정)<br>
A-Z	: 영어알파벳 (대문자)(-으로 범위 지정)<br>
ㄱ-ㅎ	:한글 문자(-으로 범위 지정)<br>
0-9	: 숫자(-으로 범위 지정)<br>
. :	모든 문자열(숫자, 한글, 영어, 특수기호, 공백 모두! 단, 줄바꿈X)<br>
\d	: 숫자<br>
\D	: 숫자가 아닌 것<br>
\w	: 영어 알파벳, 숫자, 언더스코어(_)<br>
\W	: /w 가 아닌 것<br>
\s	: space 공백<br>
\S	: space 공백이 아닌 것<br>
\특수기호 :	특수기호<br>
<br>

<h3>- 정규표현식 검색 패턴</h3>
|	: OR<br>
[]	: 괄호안의 문자들 중 하나<br>
[^문자] :	괄호안의 문자를 제외한 것<br>
^문자열 :	특정 문자열로 시작(괄호 없음 주의!)<br>
문자열$ :	특정 문자열로 끝남<br>
() :	그룹 검색 및 분류(match메서드에서 그룹별로 묶어줌)<br>
(?: 패턴)	: 그룹 검색(분류X)<br>
\b	: 단어의 처음/끝<br>
\B	: 단어의 처음/끝이 아님<br>

<h3>-정규표현식 갯수(수량) 패턴</h3>
?	: 최대 한번(없음 || 한개)<br>
*	: 없거나 있거나 (없음 || 있음): 여러개 포함<br>
+	: 최소 한개(한개 || 여러개)<br>
{n}	: n개<br>
{Min,}	: 최소 Min개 이상<br>
{Min, Max} :	최소 Min개 이상, 최대 Max개 이하<br>

<h3><b>-정규 표현식 함수</h3></b>
re.search(pattern, string)<br>
 └문자열(string)에서 정규 표현식(pattern)과 일치하는 첫 번째 부분을 찾아서 MatchObject 객체를 반환합니다. 일치하는 부분이 없으면 None을 반환합니다.<br><br>
re.match(pattern, string)<br>
 └문자열(string)의 처음부터 정규 표현식(pattern)과 일치하는지 검사합니다. 일치하는 부분이 없으면 None을 반환합니다.<br><br>
re.findall(pattern, string)<br>
 └문자열(string)에서 정규 표현식(pattern)과 일치하는 모든 부분을 찾아서 리스트로 반환합니다. 일치하는 부분이 없으면 빈 리스트를 반환합니다.<br><br>
re.split(pattern, string)<br>
 └문자열(string)을 정규 표현식(pattern)에 따라 분할하여 리스트로 반환합니다.<br><br>
re.sub(pattern, repl, string)<br>
 └문자열(string)에서 정규 표현식(pattern)과 일치하는 모든 부분을 repl로 대체합니다. 결과 문자열을 반환합니다.<br><br>
re.compile(pattern)<br>
 └정규 표현식(pattern)을 컴파일하여 패턴 객체를 반환합니다. 패턴 객체를 사용하여 문자열에서 정규 표현식을 검색할 수 있습니다. 이 방법을 사용하면 정규 표현식을 여러 번 사용해야 하는 경우에 성능을 높일 수 있습니다.<br><br>
match.group()<br>
 └MatchObject 객체에서 일치하는 문자열을 반환합니다.<br><br>
match.start()<br>
 └MatchObject 객체에서 일치하는 문자열의 시작 인덱스를 반환합니다.<br><br>
match.end()<br>
 └MatchObject 객체에서 일치하는 문자열의 끝 인덱스를 반환합니다.<br><br>
match.span()<br>
 └MatchObject 객체에서 일치하는 문자열의 (시작 인덱스, 끝 인덱스) 튜플을 반환합니다.<br><br>
 
 <h3>Example</h3>
<i><code>import re</code></i><hr>
<b>문자열에서 패턴 찾기</b>
<code>
  pattern = r'apple'
  text = 'I like apple.'
  result = re.search(pattern, text)
  if result:
      print('찾은 패턴:', result.group())
  else:
      print('일치하는 패턴이 없습니다.')
</code>

<b>문자열에서 모든 패턴 찾기</b>
<code>
  pattern = r'apple'
  text = 'I like apple. I have an apple.'
  results = re.findall(pattern, text)
  if results:
      print('찾은 패턴:', results)
  else:
      print('일치하는 패턴이 없습니다.')
</code>
<b>패턴으로 문자열 대체하기</b>
<code>
  pattern = r'apple'
  replace = 'orange'
  text = 'I like apple. I have an apple.'
  result = re.sub(pattern, replace, text)
  print('바뀐 문자열:', result)
</code>
<b>패턴으로 문자열 분리하기</b>
<code>
  pattern = r'\s+'
  text = 'I like apple. I have an apple.'
  results = re.split(pattern, text)
  print('분리된 문자열:', results)
</code>

