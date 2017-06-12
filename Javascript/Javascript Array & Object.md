## Javascript Array & Object

- 배열

  - 연관된 데이터를 모아서 통으로 관리하기 위해서 사용하는 데이터 타입
  - 배열의 진가는 반복문과 결합했을 때 나타남
  - 추가 
    - `li.push('f')`  f를 배열에 추가 
    - `li.concat(['f','g'])` f,g를 배열에 추가 => **복수**의 원소를 추가
    - `li.unshift('z')` 시작점에 원소를 추가
    - `li.splice(2, 0, 'B')` 두번째 인덱스 뒤에 대문자 B추가 => <u>첫 번째 인자</u>에 해당하는 원소부터 <u>두번째 인자</u>에 해당하는 원소의 숫자만큼의 값을 배열로부터 제거한 후에 return, 그리고 <u>세번째 인자</u>부터 전달된 인자들을 첫번째 인자의 원소 뒤에 추가
  - 제거
    - `li.shift()` 첫 번째 원소를 제거
    - `li.pop()` 배열 끝점의 원소를 제거
  - 정렬
    - `li.short()` 
    - `li.reverse()` 역순으로 정렬

- 객체

  - 배열에 대한 식별자 -> 숫자 / 문자로 사용하고 싶다면? 객체(dictionary)사용

  - 로직을 객체에 그룹핑

    - ```javascript
      var grades ={
        'list' : {'a':1, 'b':2, 'c':3},
        'show' : function(){
          for(var name in this.list){
            document.write(name+':'+this.list[name]+"<br/>");
          }
        }
      };
      grades.show();
      ```

  ​