#@1
Data structure design

Implemented like a Trie, use a HashMap to store every character in the dictionary
```
private Map<Character, WordDictionary> children;
private boolean isWord = false;
public WordDictionary() {
    this.children = new HashMap<Character, WordDictionary>();
}

// Adds a word into the data structure.
public void addWord(String word) {
    if (word == null || word.length() == 0) return;
    char[] chars = word.toCharArray();
    WordDictionary current = this;
    for (char c: chars) {
        if (!current.children.containsKey(c)) 
            current.children.put(c, new WordDictionary());
        current = current.children.get(c);
    }
    current.isWord = true;
}

// Returns if the word is in the data structure. A word could
// contain the dot character '.' to represent any one letter.
public boolean search(String word) {
    if (word == null) return false;
    return search(word, 0);
}

public boolean search(String word, int start) {
    char[] chars = word.toCharArray();
    WordDictionary current = this;
    
    for (int i = start; i < chars.length; i++) {
        char c = chars[i];
        if (c == '.') {
            if (i == chars.length - 1) {
                for (char childKey: current.children.keySet()) 
                    if (current.children.get(childKey).isWord) 
                        return true;
            } else {
                for (char childKey: current.children.keySet()) 
                    if (current.children.get(childKey).search(word, i+1)) 
                        return true;
            }
            return false;
        } else {
            if (current.children.containsKey(c)) 
                current = current.children.get(c);
            else 
                return false;
        }
    }
    return current.isWord;
}
```

#@2
```
class TrieNode {
    TrieNode[] children;
    boolean isEndOfWord;
    public TrieNode() {
        this.children = new TrieNode[26];
        this.isEndOfWord = false;
    }
}

TrieNode root = new TrieNode();

// Adds a word into the data structure.
public void addWord(String word) {
    TrieNode runner = root;
    for (char c : word.toCharArray()) {
        if (runner.children[c - 'a'] == null) {
            runner.children[c - 'a'] = new TrieNode();
        }
        runner = runner.children[c - 'a'];
    }
    runner.isEndOfWord = true;
}

// Returns if the word is in the data structure. A word could
// contain the dot character '.' to represent any one letter.
public boolean search(String word) {
    return match(word.toCharArray(), 0, root);
}

public boolean match(char[] word, int k, TrieNode node) {
    if (k == word.length) return node.isEndOfWord;
    if (word[k] != '.') {
        return node.children[word[k] - 'a'] != null && match(word, k+1, node.children[word[k] - 'a']);
    }
    else {
        for (int i = 0; i < node.children.length; i++) {
            if (node.children[i] != null) {
                if (match(word, k+1, node.children[i])) return true;
            }
        }
    }
    return false;
}
```
