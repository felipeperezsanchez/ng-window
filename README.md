# ng-window
 
first of all : don't forget to copy fonts and css files to your web site assets folder , and import  windowStyle.css to your index.html 



angular-windows allow developer to open and full control multiple windows in single page applications in simple way.

Avilable Configration

- Maxmize window
- Minimize window
- Custom size,
- Custom posation
- the window is dragable 
- Block parent window or not
- Center the window or not
- Pass values to chield window 
- Pass values from chield window to parent window
- Listening to closing chield window in parent window
- Listen to resize event with your custom listener
- Open with maximum size or not
- Enable and disable window resizing
- Enable and disable maximization
- Enable and disable minimization






Examples

```
constructor(private myInjector: WindowsInjetor)
{ 

}

openForm1()
{ 
this.myInjector.openWindow(Form1);  // Form1 is a commponant that will pupup
}


//with some customization
openForm2()
{ 

var config = new WindowConfig()  //height, width
config.position=new CustomPosition(100, 200)//left,top
config.CenterInsideParent=false;
var temp={}
config.forAny=[temp];//here you can pass anything
config.openAsMaximize=true;
this.myInjector.openWindow( Form2,config).then((the_instance_of_form2:Form2) => {
this.DisabledButtonForm2 = true;//disable that button until From2 closed

the_instance_of_form2.addForm2ClosedListener(this);//by using event listener you can liseten to close window event, in the chiled window you should implements OnDestroy then notifaiy your parent window listener
});
}
```


the previce two examples the parent window was main wibsite page
if you wint to inject window into another window it's easy , pass the ViewContainerRef of your parent window when open new window like this
```
constructor(private myInjector: WindowsInjetor,private viewContainerRef:ViewContainerRef)
{ 

}
openform()
{ 
this.myInjector.openWindow( Form2,config,this.viewContainerRef)
}

```





