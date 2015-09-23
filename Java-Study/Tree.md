## Implement a function to check if a tree is balanced.

This code runs in O(n) time and O(h) space.

```
public static int checkHeight(TreeNode root) {
  if (root == null) {
    return 0; // Height of 0
  }

  /* Check if left is balanced */
  int leftHeight = checkHeight(root.left);
  if (leftHeight == -1) {
    return -1; // Not balanced
  }
  /* Check if right is balance */
  int rightHeight = checkHeight(root.right);
  if (rightHeight == -1) {
    return -1; // Not balanced
  }

  /* Check if current node is balance */
  int heightDiff = leftHeight - rightHeight;
  if (Math.abs(heightDiff) > 1) {
    return -1;
  } else {
    /* Return height */
    return Math.max(leftHeight, rightHeight) + 1;
  }
}

public static boolean isBalanced(TreeNode root) {
  if (checkHeight(root) == -1) {
    return  false;
  } else {
    return  true;
  }
}
```

## Trie

```
class TrieNode {
    // Initialize your data structure here.
    char c;
    boolean end;
    LinkedList<TrieNode> child;
    
    public TrieNode() {
        this.c = ' ';
        this.end = false;
        this.child = new LinkedList<TrieNode>();
    }
    
    public TrieNode(char content) {
        this.c = content;
        this.end = false;
        this.child = new LinkedList<TrieNode>();
    }
    
    public TrieNode subNode(char content) {
        if (child != null) {
            for (TrieNode t : child) {
                if (t.c == content)
                    return t;
            }
        }
        return null;
    }
}

public class Trie {
    private TrieNode root;

    public Trie() {
        root = new TrieNode();
    }

    // Inserts a word into the trie.
    public void insert(String word) {
        if (search(word) == true) return;
        TrieNode t = root;
        
        for (int i = 0; i < word.length(); i++) {
            TrieNode node = t.subNode(word.charAt(i));
            if (node == null) {
                t.child.add(new TrieNode(word.charAt(i)));
                node = t.subNode(word.charAt(i));
            }
            t = node;
        }
        t.end = true;
    }

    // Returns if the word is in the trie.
    public boolean search(String word) {
        TrieNode t = root;
        
        for (int i = 0; i < word.length(); i++) {
            TrieNode node = t.subNode(word.charAt(i));
            if (node == null) {
                return false;
            }
            t = node;
        }
        if (t.end == false) return false;
        else 
            return true;
    }

    // Returns if there is any word in the trie
    // that starts with the given prefix.
    public boolean startsWith(String prefix) {
        TrieNode t = root;
        for (int i = 0; i < prefix.length(); i++)
        {
            TrieNode node = t.subNode(prefix.charAt(i));
            if (node == null)
                return false;
            t = node;
        }
        return true;
    }
}

// Your Trie object will be instantiated and called as such:
// Trie trie = new Trie();
// trie.insert("somestring");
// trie.search("key");
```
