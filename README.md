Spidar is a library that makes it easy to scrape information
from web pages. It sits atop an HTML or XML parser, providing Pythonic
idioms for iterating, searching, and modifying the parse tree.

# Quick start

```
>>> from spidar import Spidar
html_content = '<html><body><p>Some<b>bad<i>HTML</i></b></p></body></html>'
>>> sp = Spidar(html_content, 'html.parser')
>>> print(sp.prettify())
<html>
    <body>
        <p>
            Some
            <b>
                bad
                <i>
                    HTML
                </i>
            </b>
        </p>
    </body>
</html>
>>> sp.find(text="bad")
'bad'
>>> sp.i
<i>HTML</i>
#
>>> sp = Spidar("<p>Some<b>bad<i>HTML")
#
>>> print(sp.prettify())
<html>
    <body>
        <p>
            Some
            <b>
                bad
                <i>
                    HTML
                </i>
            </b>
        </p>
    </body>
</html>
#
>>> sp = Spidar("<tag1>Some<tag2/>bad<tag3>XML", "xml")
#
>>> print(sp.prettify())
<?xml version="1.0" encoding="utf-8"?>
<tag1>
    Some
        <tag2/>
            bad
        <tag3>
        XML
    </tag3>
</tag1>
```


# Running the unit tests

Spidar supports unit test discovery using Pytest:

```
$ pytest
```

