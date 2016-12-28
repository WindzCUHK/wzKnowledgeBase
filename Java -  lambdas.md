# Java-Lambdas-Self-Test
Personal learning repo for Java 8 Lambdas

# Some stream example

```java
List<T> tList = new ArrayList<T>();

T firstT = tList.stream().filter().findFirst();

List<T> listOfT = tList.stream().filter().collect(Collectors.toList());

Map<String, List<Article>> map = tList.stream().collect(Collectors.groupingBy(element -> element.getKey()));

Set<T> set = tList.stream().flatMap().collect(Collectors.toSet());
```

# Functional interface

1. Interface have only one method
2. parameters match between lambda expression and method parameters
3. return type match

```java
// functional interface (handler for event)
public interface StateChangeListener {
	public boolean onStateChange(State oldState, State newState);
}

// class will call listener method on event
public class StateOwner {
	public void addStateListener(StateChangeListener listener) { ... }
}

// Java8 way to add listener
public class Test {
	public static void main(String[] args) {
		StateOwner stateOwner = new StateOwner();
		stateOwner.addStateListener((oldState, newState) -> {
			System.out.println("StateChangeListener called");
			return oldState.equals(newState);
		});
	}
}
```

# Lambda Object

```java
// object class
public interface MyComparator {
	public boolean compare(int a1, int a2);
}

// declaring the lambda object
MyComparator myComparator = (a1, a2) -> return a1 > a2;
```
