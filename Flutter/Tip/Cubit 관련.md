# Cubit 관련
Cubit에서 Cubit을 사용해야할때

## 예시코드1
Cubit에서 DI받은 후 BlocBuilder를 사용 
### 생성
~~~
class ActiveTodoCountCubit extends Cubit<ActiveTodoCountState> {
  late final StreamSubscription todoListSubscription;

  final int initialActiveTodoCount;
  final TodoListCubit todoListCubit;
  ActiveTodoCountCubit({
    required this.initialActiveTodoCount,
    required this.todoListCubit,
  }) : super(ActiveTodoCountState(activeTodoCount: initialActiveTodoCount)) {
    todoListSubscription =
        todoListCubit.stream.listen((TodoListState todoListState) {
      print('TodoListState: $todoListState');

      final int currentActiveTodoCount = todoListState.todos
          .where((Todo todo) => !todo.completed)
          .toList()
          .length;

      emit(state.copyWith(activeTodoCount: currentActiveTodoCount));
    });
  }

  @override
  Future<void> close() {
    todoListSubscription.cancel();
    return super.close();
  }
}
~~~

### 선언
~~~
MultiBlocProvider(
    providers: [
        BlocProvider<TodoListCubit>(
            create: (context) => TodoListCubit()
        ),
        BlocProvider<ActiveTodoCountCubit>(
            create: (context) => ActiveTodoCountCubit(
                initialActiveTodoCount: context.read<TodoListCubit>().state.todos.length,
                todoListCubit: BlocProvider.of<TodoListCubit>(context),
                // context.read<TodoListCubit>(), 도 가능하다
            ),
        ),
    ]
)
~~~

### 사용
~~~
BlocBuilder<ActiveTodoCountCubit, ActiveTodoCountState>(
    builder: (context, state) {
        return Text('${state.activeTodoCount} items left',
            style: TextStyle(fontSize: 20.0, color: Colors.redAccent));
    },
),
~~~
## 예시코드2
BlocListener 사용후 state 사용
### 생성
~~~
class ActiveTodoCountCubit extends Cubit<ActiveTodoCountState> {
  final int initialActiveTodoCount;
  ActiveTodoCountCubit({
    required this.initialActiveTodoCount,
  }) : super(ActiveTodoCountState(activeTodoCount: initialActiveTodoCount));

  void calculateActiveTodoCount(int activeTodoCount) {
    emit(state.copyWith(activeTodoCount: activeTodoCount));
  }
}
~~~
### 선언
~~~
BlocProvider<ActiveTodoCountCubit>(
    create: (context) => ActiveTodoCountCubit(
    initialActiveTodoCount:
        context.read<TodoListCubit>().state.todos.length,
        // context.read<TodoListCubit>(), 도 가능하다
    ),
),
~~~
### 사용
~~~
BlocListener<TodoListCubit, TodoListState>(
    listener: (context, state) {
        final int activeTodoCount = state.todos
          .where((Todo todo) => !todo.completed)
          .toList()
          .length;
        context
            .read<ActiveTodoCountCubit>()
            .calculateActiveTodoCount(activeTodoCount);
    },
    child: BlocBuilder<ActiveTodoCountCubit, ActiveTodoCountState>(
        builder: (context, state) {
            return Text('${state.activeTodoCount} items left',
                style: TextStyle(fontSize: 20.0, color: Colors.redAccent));
        },
    ),
),
~~~