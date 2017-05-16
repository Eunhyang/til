## Django stuydy week4

#### 다대다 관계

[github](https://github.com/jyhwng/djangotube_m2m)

e.g. 포스트와 태그, 지하철 노선과 역

````python
class Post(models.Model):
	title = ...
	content = ...
	tag_set = models.ManyToManyField('Tag', blank = True)
	
class Tag(models.Model):
    name = ...
````

[sqlite : db관계를 gui형식으로 보여줌](http://sqlitebrowser.org/)

ManyToManyField 

- 필드 정의는 어느 쪽에?
  - ManyToManyField 필드 정의는 어느 쪽에 해도 상관없다!
  - 단, admin.py 에서 관리해줄 때 편한 쪽으로 설계하자!(Post 안에 Tag가 들어가 있는 것이 자연스러움)
- 형식
  - 다대다 필드명은 복수형으로 써주거나 related manager 형식(ex. tag_set)으로 쓰는게 일반적
- 왜 'Tag' 따옴표 안에?
  - Tag 클래스가 정의되기 전에 쓰였기 때문에. 문자열 Tag로 찾으라고 알려주는 것
  - `tag_set = models.ManyToManyField('Tag')` 
    - tag를 문자열로 찾는 이유 => tag class가 정의되어있지 않기 때문. 
    - 순환참조에러가 나는 경우가 있으므로 처음부터 string으로 써주는 게 권장됨
    - 물론 Tag클래스를 Post보다 먼저 선언해도 됨. 그러나 Post가 더 중요한 클래스이므로 위와 같은 방법 추천
- 어떤 column으로 연결되어야 할지도 정해줄 수 있음
- 두 개의 테이블을 id로 묶은 테이블이 향성됨



콘솔에서 shell 접속.

- ````python
  $ python maange.py shell
  ($ python manage.py shell_plus)
  >>> from video.models import Video, Tag
  >>> ...
  ````

- QuerySet 활용

- ````python
  >>> p = Video.objects.last() #id로 접근해도 상관 없음
  >>> p
  <Post: 파이썬 A to Z>
      >>> t = Tag.objects.frist()
      >>> p.tag_set.add(t)
      >>> p.tag_set.all()
      <QuerySet [<Tag: Python>]>
  ````

  ````python
  >>> t1 = Tag.objects.create(name = 'starbucks')
  >>> t1
  <Tag: starbucks>
      
  >>> p.tag_set.add(t1)
  >>> p.tag_set.all()
  <QuerySet [<Tag: Python>, <Tag: starbucks>]>

  >>> p.tag_set.create(name='sandwich')
  <Tag:sandwich>
  >>> p.tag_set.all()
  <QuerySet [<Tag: Python>, <Tag: starbucks>, <Tag: sandwich>]>
  ````

  ​

Through Field 

- 두 모델간의 관계가 추가적인 데이터를 가지는 경우 

  - ->다대다 관계를 가지는 두 개의 모델 이외에 추가 데이터를 저장할 또다른 모델 - 중간(intermediate)모델- 을 만들어 준다.
  - 예) `맴버`와 `그룹 `간의 다대다 관계에서 - 맴버가 그룹에 `가입한 날짜`나 `가입 이유`등을 저장해 주어야할 때

  ````python
  from django.db import models

  class Person(models.Model):
      name = models.CharField(max_length=128)
      
      def__str__(self):
          return self.name

  class Group(models.Model):
      name = models.CharField(max_length=128)
      members = models.ManyToManyField(Person, through = 'Membership')
      
      def __str__(self):
          return self.name
      
  class Membership(models.Model):
      person = models.ForeignKey(Person)
      group = models.ForeginKey(Group)
      date_joined = models.DateField()
      invite_reson = models.CharField(max_length=64)
  ````

- 1. m2m 필드 지정할 떄, through 속성을 명시
  2. 중간 모델을 각각의 M2M모델과 foreingKey로 연결

  ​

  ````python
  >>> ringo = Person.objects.create(name="Ringo Starr") 
  >>> paul = Person.objects.create(name="Paul McCartney") 
  >>> beatles = Group.objects.create(name="The Beatles") 

  >>> m1 = Membership(person=ringo, group=beatles, 
  ...     date_joined=date(1962, 8, 16), 
  ...     invite_reason="Needed a new drummer.") 
  >>> m1.save() #Memebership부터 생성

  >>> beatles.members.all() 
  [<Person: Ringo Starr>] 
  >>> ringo.group_set.all() 
  [<Group: The Beatles>] 

  >>> m2 = Membership.objects.create(person=paul, group=beatles, 
  ...     date_joined=date(1960, 8, 1), 
  ...     invite_reason="Wanted to form a band.") 
  >>> beatles.members.all() 
  [<Person: Ringo Starr>, <Person: Paul McCartney>]
  ````

  1. QuerySet에서 바로 멤버를 그룹에 add해주지 못하고 중간 모델을 정의해주어야 한다.

#### model 정의 유용한 기능

- `__gt=date(1961,1,1))` : `__lt`,`__lte` ,`__gte`
- `__icontains` : ignore약자 -> B와 b포함 검색
- __ : lookup 메소드라 명칭




#### polls 앱으로 Ajax 배우기!

[github](https://github.com/Leop0ld/djangopolls)

views.py 추가부분

````python
def vote_data(request, question_id):
    question = get_object_or_404(Question, pk=question_id)
    result = []

    for choice in question.choice_set.all():
        result.append({
            'choice_text': choice.choice_text,
            'votes': choice.votes,
        })
    result = json.dumps(result)

    return HttpResponse(result)
````

- list생성-> tuple(choice_text, votes)를 담아서 -> json으로 변환

  ​

urls.py 추가부분

````python
url(r'^(?P<question_id>[0-9]+)/votedata/$', views.vote_data, name='vote_data'),
````



templates/**polls**/result.html 

````html
<h1>{{ question.question_text }}</h1>

<ul id="choiceList">
{% for choice in question.choice_set.all %}
	<li>{{ choice.choice_text }} -- {{ choice.votes }} vote{{ choice.votes|pluralize }}</li>
{% endfor %}
</ul>
<p id="updatedCount">0</p>
<button id="updateBtn">Update</button>

<script src="https://code.jquery.com/jquery-3.2.1.min.js"></script>
<script>
	$("#updateBtn").click(function() {
		$.ajax({
			dataType: "json",
			url: "{% url 'polls:vote_data' question.id %}"
		}).done(function(data) {
			var choiceList = $("#choiceList"),
				updatedCount = $("#updatedCount");
			console.log(data);
			var dataList = '';
			var count = Number(updatedCount.text());
			count += 1;
			for(var i = 0; i < data.length; i++) {
				var pluralize = ' vote';
				if(data[i].votes > 1) {
					pluralize = ' votes';
				}
				dataList += '<li>' + data[i].choice_text + ' -- ' + data[i].votes + pluralize + '</li>';
			}
			choiceList.html(dataList);
			updatedCount.text(count);
		}).fail(function() {
			console.log("Failed fetching data");
		});
	})
</script>
````

- 버튼 클릭시 ajax처리

  - name이 votd_data인 url로 question.id와 함께 보냄

  - done하면

    - data에 json타입 받아옴. 

    - 다시 js변수로 받아서, html로 추가

      ​

templates/**polls**/detail.html 

````html
<h1>{{ question.question_text }} </h1>
<form id="questionForm" action="{% url 'polls:vote' question_id=question.id%}" method='post'>
{% csrf_token %}
{% for choice in question.choice_set.all %}
	<input type='radio' name='choice' value='{{ choice.id }}' id='choice{{ forloop.counter }}' />
	<label for='choice{{ forloop.counter }}'>{{ choice.choice_text }}</label><br />
{% endfor %}
<input type='submit' value='Vote' />
</form>

<button id="showVotes">Show Votes</button>

<script src="https://code.jquery.com/jquery-3.2.1.min.js"></script>
<script>
	var choiceList = $("#questionForm"),
        showVotes = $("#showVotes"),
        stop = $("<p>Stop!!!</p>"),
		    clicked = false,
        clickCount = 0;
	showVotes.click(function() {
	    if(clicked) {
	        console.log("Already clicked!", clickCount);
            clickCount += 1;
	        if(clickCount >= 5) {
	            showVotes.after(stop);
            }
		}
		else {
            $.ajax({
                dataType: "json",
                url: "{% url 'polls:vote_data' question.id %}"
            }).done(function (data) {
                console.log(data);
                var dataList = $('<ul></ul>');
                for (var i = 0; i < data.length; i++) {
                    var pluralize = " vote";
                    if (data[i].votes > 1) {
                        pluralize = " votes";
                    }
                    dataList.append("<li>" + data[i].choice_text + " -- " + data[i].votes + pluralize + "</li>");
                }
                choiceList.append(dataList);
                clicked = true;
                clickCount += 1;
            }).fail(function () {
                console.log("Failed fetching data");
            });
        }
	})
</script>

````

