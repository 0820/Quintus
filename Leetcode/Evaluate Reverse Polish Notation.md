Create an interface called OPERATOR and map each operator string to an implementation of the Operator interface.

```
interface Operator {
    int eval(int x, int y);
}

private static final Map<String, Operator> OPERATORS = new HashMap<String, Operator>() {{
    put("+", new Operator() {
        public int eval(int x, int y) {return x + y;}
    });
    put("-", new Operator() {
        public int eval(int x, int y) {return x - y;}
    });
    put("*", new Operator() {
        public int eval(int x, int y) {return x * y;}
    });
    put("/", new Operator() {
        public int eval(int x, int y) {return x / y;}
    });
}};

public int evalRPN(String[] tokens) {
    Stack<Integer> s = new Stack<>();
    for (String token : tokens) {
        if (OPERATORS.containsKey(token)) {
            int y = s.pop();
            int x = s.pop();
            s.push(OPERATORS.get(token).eval(x, y));
        }
        else
            s.push(Integer.parseInt(token));
    }
    
    return s.pop();
}
```
