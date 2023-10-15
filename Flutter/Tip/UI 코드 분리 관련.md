# UI 코드 분리 관련

## 예시 코드
~~~
Row(
    mainAxisAlignment: MainAxisAlignment.spaceBetween,
    children: [
        filterButton(context, Filter.all),
        filterButton(context, Filter.active),
        filterButton(context, Filter.completed),
    ],
)

Widget filterButton(BuildContext context, Filter filter) {
    return TextButton(
        onPressed: () {},
        child: Text(
            filter == Filter.all
                ? 'All'
                : filter == Filter.active
                    ? 'Active'
                    : 'Completed',
            style: TextStyle(fontSize: 18.0, color: textColor(context, filter)),
        ),
    );
}

Color textColor(BuildContext context, Filter filter) {
    final currentFilter = context.watch<TodoFilterCubit>().state.filter;
    return currentFilter == filter ? Colors.blue : Colors.grey;
}
~~~

혹은
~~~
itemBuilder: (context, index) {
    return Dismissible(
        key: ValueKey(todos[index].id),
        background: showBackground(0),
        secondaryBackground: showBackground(1),
        child: Text(
            todos[index].desc,
            style: TextStyle(fontSize: 20.0),
        ),
    );
},

Widget showBackground(int direction) {
    return Container(
        margin: const EdgeInsets.all(4.0),
        padding: const EdgeInsets.symmetric(horizontal: 10.0),
        color: Colors.red,
        alignment: direction == 0 ? Alignment.centerLeft : Alignment.centerRight,
        child: Icon(
            Icons.delete,
            size: 30.0,
            color: Colors.white,
        ),
    );
}
~~~
이런식으로도 사용할 수 있다.