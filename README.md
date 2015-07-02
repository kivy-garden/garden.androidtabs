#AndroidTabs
Kivy widget that try to reproduce Android tabs behaviour.  
Video preview @ https://www.youtube.com/watch?v=0nlUIbQrf5k

##Usage summary
AndroidTabs allow you to create your own custom tabbed panel
with an animated tab indicator in a easy way.
Just create your tabs that must inherit from AndroidTabsBase
and add them to an AndroidTabs instance.

##Example
```
from kivy.app import App
from kivy.uix.boxlayout import BoxLayout
from kivy.uix.button import Button
from kivy.garden.androidtabs import *


class MyTab(BoxLayout, AndroidTabsBase):

    pass

class Example(App):

    def build(self):

        android_tabs = AndroidTabs()

        for n in range(1, 6):
            tab = MyTab(text='TAB %s' % n)
            android_tabs.add_widget(tab)

        return android_tabs

Example().run()
```
