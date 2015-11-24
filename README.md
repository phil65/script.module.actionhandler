Usage:

1) import the module into the module containing your WindowXML class:

from ActionHandler import ActionHandler
ch = ActionHandler()


2) forward onClick / onAction / onfocus events to ActionHandler

    def onClick(self, control_id):
        ch.serve(control_id, self)

    def onFocus(self, control_id):
        ch.serve_focus(control_id, self)

    def onAction(self, action):
        ch.serve_action(action, self.getFocusId(), self)

3) you can now use decorators to map events to methods

Examples:

- for click events:

    @ch.click(1000)
    @ch.click(2000)
    def some_method(self):
        ...

    @ch.click([1000,2000])
    def some_method(self):
        ...


- for focus events:

    @ch.focus(1000)
    def some_method(self):
        ...


- for action events:

    @ch.action("number9", "*")
    def some_method(self):
        ...

    @ch.action("contextmenu", 150)
    def some_method(self):
        ...

--> first parameter is name of action id,
    second parameter is id of button ("*" = all controls)
