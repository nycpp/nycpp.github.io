# Past events
Below is an index of every NYC++ event held so far. Links to speakers' slides and video recordings are included, where
available.

{% assign year = 0 %}
{% for meetup in site.meetups %}
  {% capture todayDate %}{{'now' | date: '%s'}}{% endcapture %}
  {% capture meetupDate %}{{meetup.date | date: '%s'}}{% endcapture %}

  {% if todayDate > meetupDate %}
    {% capture meetupYear %}{{meetup.date | date: '%Y'}}{% endcapture %}
    {% if year != meetupYear %}
## {{ meetupYear }}
    {% assign year = meetupYear %}
    {% endif %}

<ul><li><nobr>
{% if meetup.url %}
<span title="meetup.com event"><a
  target="_blank"
  rel="noopener noreferrer"
  href="{{ meetup.url }}">
{% endif %}

{{ meetup.date | date_to_long_string: "ordinal", "US" | remove: "," | truncatewords: 2, ""}}
    @ {{meetup.venue}} ft., {{ meetup.speaker }}
    {% if meetup.url %}<img width="12em" src="/redirect-icon.png"/>
{% if meetup.url %}
</a>
{% endif %}

{% if meetup.slides or meetup.video %}—
  {% if meetup.video %}
<span title="video recording"><a target="_blank" rel="noopener noreferrer" href="{{ meetup.video }}">📼</a></span>
  {% endif %}
  {% if meetup.slides %}
<span title="slides"><a target="_blank" rel="noopener noreferrer" href="{{ meetup.slides }}">📖</a></span>
  {% endif %}
{% endif %}

{% if meetup.url %}</span>{% endif %}
</nobr></li></ul>
    {% endif %}
  {% endif %}
{% endfor %}
