Implemented with Trie, routine backtracking code
```
public List<String> findWords(char[][] board, String[] words) {
    Set<String> result = new HashSet<>();
    
    int a = board.length;
    int b = board[0].length;
    Trie t = new Trie();
    
    for (String w : words)
        t.insert(w);
    
    for (int i = 0; i < a; i++) {
        for (int j = 0; j < b; j++) {
            String word = "";
            helper(board, word, i, j, t, result);
        }
    }
    
    return new ArrayList<String>(result);
}

public void helper(char[][] board, String word, int i, int j, Trie t, Set<String> r) {
    
    if (i < 0 || j < 0 || i >= board.length || j >= board[0].length) return;
    
    word += board[i][j];
    if (!t.startsWith(word))
        return;
    else {
        if (t.search(word))
            r.add(word);
        char c = board[i][j];
        board[i][j] = '#';
        helper(board, word, i + 1, j, t, r);
        helper(board, word, i - 1, j, t, r);
        helper(board, word, i, j + 1, t, r);
        helper(board, word, i, j - 1, t, r);
        board[i][j] = c;
    }
}

public class Trie {
    private TrieNode root;

    public Trie() {
        root = new TrieNode();
        root.wordEnd = false;
    }

    public void insert(String word) {
        TrieNode node = root;
        for (int i = 0; i < word.length(); i++) {
            Character c = new Character(word.charAt(i));
            if (!node.childdren.containsKey(c)) {
                node.childdren.put(c, new TrieNode());
            }
            node = node.childdren.get(c);
        }
        node.wordEnd = true;
    }

    public boolean search(String word) {
        TrieNode node = root;
        boolean found = true;
        for (int i = 0; i < word.length(); i++) {
            Character c = new Character(word.charAt(i));
            if (!node.childdren.containsKey(c)) {
                return false;
            }
            node = node.childdren.get(c);
        }
        return found && node.wordEnd;
    }

    public boolean startsWith(String prefix) {
        TrieNode node = root;
        boolean found = true;
        for (int i = 0; i < prefix.length(); i++) {
            Character c = new Character(prefix.charAt(i));
            if (!node.childdren.containsKey(c)) {
                return false;
            }
            node = node.childdren.get(c);
        }
        return found;
    }

}

public class TrieNode {
    Map<Character, TrieNode> childdren;
    boolean wordEnd;

    public TrieNode() {
        childdren = new HashMap<Character, TrieNode>();
        wordEnd = false;
    }
}

// Your Trie object will be instantiated and called as such:
// Trie trie = new Trie();
// trie.insert("somestring");
// trie.search("key");
```
