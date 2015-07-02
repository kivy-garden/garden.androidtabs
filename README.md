#AndroidTabs
Kivy widget that try to reproduce Android tabs behaviour.  
Video preview @ https://www.youtube.com/watch?v=0nlUIbQrf5k

##Usage summary
AndroidTabs allow you to create your own custom tabbed panel
with an animated tab indicator in a easy way.
Just create your tabs that must inherit from AndroidTabsBase
and add them to an AndroidTabs instance.

##How it works
To understand how it works just look at the structure in the Kivy language:
```
<AndroidTabs>:
    AndroidTabsMain:
        AndroidTabsCarousel:
            MyTab:                  # Tabs must inherit from AndroidTabsBase
                text: 'tab 1'
            MyTab:
                text: 'tab 2'

    AndroidTabsBar:
        AndroidTabsScrollView:
            Gridlayout:
                AndroidTabsLabel:   # Automatically added when you add a Tab to AndroidTabs
                AndroidTabsLabel:   # so you don't need add them manually
                
```
As you can see it contains two widgets, AndroidTabsMain that containing the Carousel, and AndroidTabsBar that contains the Scrollview.  
Each time you add a Tab to AndroidTabs, it adds the Tab to the carousel and creates and adds an AndroidTabsLabel instance to the GridLayout of the Scrollview.  

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
##Customization
With kivy language, or directly in Python you can customize each widget.
Below all the properties of AndroidTabs.
```
class AndroidTabs(AnchorLayout):
    '''
    The AndroidTabs class.
    You can use it to create your own custom tabbed panel.
    '''

    default_tab = NumericProperty(0)
    '''
    Index of the default tab. Default to 0.
    '''

    tab_bar_height = NumericProperty('48dp')
    '''
    Height of the tab bar.
    '''

    tab_indicator_anim = BooleanProperty(True)
    '''
    Tab indicator animation. Default to True.
    If you do not want animation set it to False.
    '''

    tab_indicator_height = NumericProperty('2dp')
    '''
    Height of the tab indicator.
    '''

    tab_indicator_color = VariableListProperty([1])
    '''
    Color of the tab indicator.
    '''

    anim_duration = NumericProperty(0.2)
    '''
    Duration of the slide animation. Default to 0.2.
    '''

    anim_threshold = BoundedNumericProperty(
        0.8, min=0.0, max=1.0,
        errorhandler=lambda x: 0.0 if x < 0.0 else 1.0)
    '''
    Animation threshold allow you to change
    the tab indicator animation effect.
    Default to 0.8.
    '''
```
