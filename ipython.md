IPython (Notebook)
===

Output variables:

`_10 == Out[10]`

Input variables:

`In[10]`

Magic functions:

`%magic`


Last 5 lines of history:

`%history -n 1-5`

List all magic functions:

`%lsmagic`

Time execution of a statement or command:

`%timeit range(10)`

Magic block of code:

`%%magic  block of code`

Runs bash as it is, $etc run unmodified

`%%bash`

Eval it as it is:

`>>> while a < b:
...    print b
...    a += 1`

Exception trace contains information about local variables as well:

`%xmode verbose
0/0`

Run perl code:

`%%perl
@months = ("July", "August")
print $months[0];`

Run ruby code:

`%%ruby
name = "world"
puts "Hello #{name.capitalize}!"`

Load next cell input from a file:

`%load somedir/somefile`

Drop PDB for debugging

`%debug`

Make matploblib show inline instead of popping up a window

`%matplotlib inline`

### IPython Sessions 

Current connection session info:

`%connect_info`

Kernel/Client model: attach another client to same process:

`%qtconsole`

or from the terminal: 

`ipython <app> --existing kernel-id`

### Formatting

Markdown texts are possible. Just use the celltype a markdown.

Latex:
    
`$latex (inline equation)`

MathJs

`$$mathjs`

### Rich display system

Display is equivalent of print for rich data:

```
from IPython.display import display
from IPython.display import Image
i = Image(filename='blabla.png')
display(i)
i # or just evaluate it
```

Fetch Image from a remote network and display the image, which will be embedded as hot link and will only work when internet is available:

`Image(url='https://images.example.com/example.png')`

Embed YouTube:

```from IPython.display import YouTubeVideo
YouTubeVideo('vw9Vk2VIkD8')```

HTML embedding

`%%html
<table>
</table>`

Javascript:

```
%%javascript
// some javascript here
```

Other python libraries can provide special functions to dispplay their data in IPython notebook, for instance SymPy.

IFrame embedding:

`IFrame('http://us.pycon.org',700,350)`

### Interactive Widgets (Micro-GUIs in the browser)

```
from IPytohn.html.widgets import interact, fixed
interact(f, x=(0.0, 5.0), y="some string", z={'US': 'United States', 'PK': 'Pakistan'})

f.widget.children[0] # x
f.widget.children[1] # y
f.widget.children[2] # z
```

Interactive decorator:

```
@interact
def sorter(string='Hello', reverse=Flse):
    print ''.join(sorted(string, reverse=reverse)
```

### Profiles

Profile location:

`~/.ipython/profile_<name>`

To get current profile location:

`get_ipython().profile_dir.location`

```c = get_config()
c.InteractiveShellApp.ignore_old_config = True```

Profile startup directory contains files which run in lexographically sorted order upon startup:

`$profile/startup/`

Register line magic:

```
@register_line_magic
def somefunc(line)
    """ Some description """
    pass
```

