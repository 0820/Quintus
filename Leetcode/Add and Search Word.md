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
