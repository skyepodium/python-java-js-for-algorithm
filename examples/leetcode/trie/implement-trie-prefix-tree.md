# 1. 설명
- trie를 구현하세요.


[문제 링크](https://leetcode.com/problems/implement-trie-prefix-tree/)


# 2. 코드
### 1) python
```python
from collections import defaultdict


class Node:
    def __init__(self):
        self.is_end = False
        self.child = defaultdict(Node)


class Trie:
    def __init__(self):
        self.root = Node()

    def insert(self, word: str) -> None:
        c = self.root
        for w in word:
            c = c.child[w]
        c.is_end = True

    def search(self, word: str) -> bool:
        c = self.root
        for w in word:
            c = c.child.get(w)
            if not c: return False
        return c.is_end

    def startsWith(self, prefix: str) -> bool:
        c = self.root
        for w in prefix:
            c = c.child.get(w)
            if not c: return False
        return True
```

### 2) java
```java
import java.util.HashMap;
import java.util.Map;

class Node {
    public boolean isEnd;
    public Map<Character, Node> child;

    public Node() {
        this.isEnd = false;
        this.child = new HashMap<>();
    }
}

class Trie {
    private Node root;
    public Trie() {
        this.root = new Node();
    }

    public void insert(String word) {
        Node c = this.root;
        for(int i=0; i<word.length(); i++) {
            char w = word.charAt(i);

            if(!c.child.containsKey(w)) c.child.put(w, new Node());
            c = c.child.get(w);
        }
        c.isEnd = true;
    }

    public boolean search(String word) {
        Node c = this.root;
        for(int i=0; i<word.length(); i++) {
            char w = word.charAt(i);
            if(!c.child.containsKey(w)) return false;
            c = c.child.get(w);
        }
        return c.isEnd;
    }

    public boolean startsWith(String prefix) {
        Node c = this.root;
        for(int i=0; i<prefix.length(); i++) {
            char w = prefix.charAt(i);
            if(!c.child.containsKey(w)) return false;
            c = c.child.get(w);
        }
        return true;
    }
}
```

### 3) JavaScript
```js
class Node {
    constructor() {
        this.isEnd = false
        this.child = new Map()
    }
}

class Trie {
    constructor() {
        this.root = new Node()
    }

    insert (word) {
        let c = this.root
        for(let i=0; i<word.length; i++) {
            const w = word[i]
            if(!c.child.has(w)) c.child.set(w, new Node())
            c = c.child.get(w)
        }
        c.isEnd = true
    }

    search (word) {
        let c = this.root
        for(let i=0; i<word.length; i++) {
            const w = word[i]
            if(!c.child.has(w)) return false
            c = c.child.get(w)
        }
        return c.isEnd
    }

    startsWith(prefix) {
        let c = this.root
        for(let i=0; i<prefix.length; i++) {
            const w = prefix[i]
            if(!c.child.has(w)) return false
            c = c.child.get(w)
        }
        return true
    }
}
```