## Django template 접근방법

**ForeingKey**

````python
class Time(models.Model):
	report = models.ForeignKey(
        Report,
        related_name = "report_time",
        on_delete = models.CASCADE,
    )
````

=> Template (related_name으로 접근)

````html
{% for time in report.report_time.all %}
	{{time.name}}
{% endfor %}
````

​	

**ManyToManyField**

````python
class Time(models.Model):
    activity = models.ManyToManyField('Activity', null=True, blank=True)
````

=>Template(ManyToManyField로 지정한 이름으로 접근)

````html
{% for act in time.activity.all%}
	<td>{{act.content}}</td>
{% endfor %}
````

