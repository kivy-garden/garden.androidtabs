#AndroidTabs
Kivy widget that try to reproduce Android tabs behaviour.
#
Video preview @ https://www.youtube.com/watch?v=0nlUIbQrf5k

###Usage summary
AndroidTabs allow you to create your own custom tabbed panel
with an animated tab indicator in a easy way.
Just create your tabs that must inherit from AndroidTabsBase
and add them to an AndroidTabs instance.

```
class MyTab(BoxLayout, AndroidTabsBase):

    pass

android_tabs = AndroidTabs()

for n in range(1,6):

    tab = MyTab(text='Tab %s' % n)
    tab.add_widget(Button(text='Button %s' % n))
    android_tabs.add_widget(tab)
```
