# django test

Python + Django

Steps to configure...

1 Install python 2.7 from https://www.python.org/downloads/

2 set env path in win in 
PATH C:\Python27\Scripts; and C:\Python27;

3 verify python and pip using command
Or download get-pip.py is placed in C:\Python27
And verify pip.py in C:\Python27\Scripts
If not download it

4 download django by cmd ref https://www.djangoproject.com/download/
https://docs.djangoproject.com/en/1.11/intro/install/
pip install Django==1.11.6

 
5 check django by following ref https://docs.djangoproject.com/en/1.11/intro/tutorial01/
python -m django --version
6 create django project
django-admin startproject mysite
7 run it
python manage.py runserver 8080

 
8 Goto C:\Python27\Lib
Edit functools.py if error comes 
  File "C:\Python27\lib\functools.py", line 56, in <lambda>
    '__lt__': [('__gt__', lambda self, other: other < self),
RuntimeError: maximum recursion depth exceeded in cmp
To fix the problem replace this (about line 56 in python\Lib\fuctools.py):
convert = { '__lt__': [('__gt__', lambda self, other: other < self), ('__le__', lambda self, other: not other < self), ('__ge__', lambda self, other: not self < other)], '__le__': [('__ge__', lambda self, other: other <= self), ('__lt__', lambda self, other: not other <= self), ('__gt__', lambda self, other: not self <= other)], '__gt__': [('__lt__', lambda self, other: other > self), ('__ge__', lambda self, other: not other > self), ('__le__', lambda self, other: not self > other)], '__ge__': [('__le__', lambda self, other: other >= self), ('__gt__', lambda self, other: not other >= self), ('__lt__', lambda self, other: not self >= other)] }
to that:
convert = { '__lt__': [('__gt__', lambda self, other: not (self < other or self == other)), ('__le__', lambda self, other: self < other or self == other), ('__ge__', lambda self, other: not self < other)], '__le__': [('__ge__', lambda self, other: not self <= other or self == other), ('__lt__', lambda self, other: self <= other and not self == other), ('__gt__', lambda self, other: not self <= other)], '__gt__': [('__lt__', lambda self, other: not (self > other or self == other)), ('__ge__', lambda self, other: self > other or self == other), ('__le__', lambda self, other: not self > other)], '__ge__': [('__le__', lambda self, other: (not self >= other) or self == other), ('__gt__', lambda self, other: self >= other and not self == other), ('__lt__', lambda self, other: not self >= other)] }

Ref https://stackoverflow.com/questions/16259729/django-python-manage-py-runserver-gives-runtimeerror-maximum-recursion-depth-e
Site will probably run after hit cmd like,
>python manage.py runserver localhost:8000
