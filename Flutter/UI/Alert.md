# Alert.md

## 예시 코드
![스크린샷 2023-10-04 오후 11 36 11](https://github.com/choijaegwon/choijaegwon.github.io/assets/68246962/ff1ca857-2d17-4330-a316-24e5fd20a10c)
~~~
showDialog(
    context: context,
    barrierDismissible: false,
    builder: (context) {
        return AlertDialog(
            title: Text('Are you sure?'),
            content: Text('Do you really want to delete?'),
            actions: [
                TextButton(
                    onPressed: () => Navigator.pop(context, false),
                    child: Text('No'),
                ),
                TextButton(
                    onPressed: () => Navigator.pop(context, true),
                    child: Text('YES'),
                ),
            ],
        );
    },
);
~~~
barrierDismissible: false, 속성을 주면 뒤에 터치를 막을 수 있다.    
Navigator.pop(context, false)에서 context뒤에 argument는 줘도 되고 안줘도 된다.  
위에 예제는 Dismissible위젯의 confirmDismiss함수의 콜백으로 사용해서 argument를 줬다.  

## 예시 코드2
~~~
class _TodoItemState extends State<TodoItem> {
  late final TextEditingController textController;
  @override
  void initState() {
    super.initState();
    textController = TextEditingController();
  }

  @override
  void dispose() {
    textController.dispose();
    super.dispose();
  }

  @override
  Widget build(BuildContext context) {
    return ListTile(
      onTap: () {
        showDialog(
          context: context,
          builder: (context) {
            bool _error = false;
            textController.text = widget.todo.desc;

            return StatefulBuilder(
              builder: (BuildContext context, StateSetter setState) {
                return AlertDialog(
                  title: Text('Edit Todo'),
                  content: TextField(
                    controller: textController,
                    autofocus: true,
                    decoration: InputDecoration(
                        errorText: _error ? 'Value cannot be empty' : null),
                  ),
                  actions: [
                    TextButton(
                      onPressed: () => Navigator.pop(context),
                      child: Text('CANCEL'),
                    ),
                    TextButton(
                      onPressed: () {
                        setState(() {
                          _error = textController.text.isEmpty ? true : false;
                          if (!_error) {
                            context
                                .read<TodoListCubit>()
                                .editTodo(widget.todo.id, textController.text);
                            Navigator.pop(context);
                          }
                        });
                      },
                      child: Text('EDIT'),
                    ),
                  ],
                );
              },
            );
          },
        );
      },
      leading: Checkbox(
        value: widget.todo.completed,
        onChanged: (bool? checked) {
          context.read<TodoListCubit>().toggleTodo(widget.todo.id);
        },
      ),
      title: Text(widget.todo.desc),
    );
  }
}
~~~
StatefulBuilder은 showDialog안에서 state를 handing 하려고 StatefulBuilder를 return 해준다.     
Dialog는 현재위치에 scope 된게 아니여서(TodoItemWidget에 childWidget이 아니기 때문에) 이렇게 작성한다.     

## 예시코드3
~~~
void errorDialog(BuildContext context, String errorMessage) {
  if (Platform.isIOS) {
    showCupertinoDialog(
      context: context,
      barrierDismissible: false,
      builder: (context) {
        return CupertinoAlertDialog(
          title: const Text('Error'),
          content: Text(errorMessage),
          actions: [
            CupertinoDialogAction(
              child: const Text('OK'),
              onPressed: () => Navigator.pop(context),
            ),
          ],
        );
      },
    );
  } else {
    showDialog(
      context: context,
      barrierDismissible: false,
      builder: (context) {
        return AlertDialog(
          title: const Text('Error'),
          content: Text(errorMessage),
          actions: [
            TextButton(
              onPressed: () => Navigator.pop(context),
              child: const Text('OK'),
            )
          ],
        );
      },
    );
  }
}
~~~