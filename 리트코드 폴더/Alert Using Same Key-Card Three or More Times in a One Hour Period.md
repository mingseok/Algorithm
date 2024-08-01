## Alert Using Same Key-Card Three or More Times in a One Hour Period

```java
public List<String> alertNames(String[] keyName, String[] keyTime) {
    Map<String, List<Integer>> map = new HashMap<>();
    for (int i = 0; i < keyName.length; i++) {
        List<Integer> list = map.getOrDefault(keyName[i], new ArrayList<>());
        String[] t = keyTime[i].split(":");
        list.add(Integer.parseInt(t[0]) * 60 + Integer.parseInt(t[1]));
        map.put(keyName[i], list);
    }
    List<String> res = new ArrayList<>();
    for (String key : map.keySet()) {
        if (check(map.get(key))) {
            res.add(key);
        }
    }
    Collections.sort(res);
    return res;
}

boolean check(List<Integer> values) {
    if (values.size() < 3) return false;
    Collections.sort(values);
    LinkedList<Integer> list = new LinkedList<>();
    for (int v : values) {
        while (!list.isEmpty() && Math.abs(v - list.getFirst()) > 60) {
            list.removeFirst();
        }
        list.add(v);
        if (list.size() == 3) return true;
    }
    return false;
}
```
