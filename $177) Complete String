/*
    Time Complexity : O(Sum(A[i]))
    Space Complexity : O(Sum(A[i]))

    where 'Sum(A[i])' is the sum of size of all words 'A[i]'.
 */

// Trie data structure class.
struct trieNode 
{ 
    struct trieNode *child[26]; 
    bool isEnding;
}; 
struct trieNode *newTrieNode(void) 
{ 
    struct trieNode *newNode = new trieNode; 
    newNode->isEnding = false;
    for (int i = 0; i<26; i++) 
        newNode->child[i] = NULL; 
    return newNode; 
} 

// Functon to insert the word into the trie.
void insert(struct trieNode *root, string str) 
{ 
    int len = str.length(); 
    struct trieNode *pCrawl = root; 
  
    for (int level = 0; level<len; level++) 
    { 
        int index = str[level]-'a'; 
        if (!pCrawl->child[index]) 
            pCrawl->child[index] = newTrieNode(); 
        pCrawl = pCrawl->child[index]; 
    } 
    // Mark the ending of this word in trie.
    pCrawl ->isEnding = true;
}

  // Function to check if this word has all prefixes in array.
bool allPrefixed(struct trieNode *root, string word) {
    struct trieNode *pCrawl = root; 
    for (char c: word) {
      int i = c - 'a';
      pCrawl = pCrawl -> child[i];
      if(pCrawl == NULL || pCrawl->isEnding == false){
        return false;
      }
    }
    // We reach here if each prefix of word is present in array.
    return true;
}


string completeString(int n, vector<string> &a) {

    // Initialise answer as empty string.
    string ans = "";

    struct trieNode *root = newTrieNode();

    // Insert each element of array into Trie.
    for (string word: a)
      insert(root, word);

    // Traverse over strings and check which of them have all prefixes present in array.
    for (string word: a) {
      if (!allPrefixed(root, word))
        continue;
      // If current word is longer than 'ans'.
      if (ans.size() < word.size()) {
        ans = word;
      }
      // If current word is of same size as 'ans', but is lexicographically smaller than 'ans'.
      else if (ans.size() == word.size() && word < ans) {
        ans = word;
      }
    }

    // If no valid word is present, return "None".
    if (ans.size() == 0) {
      ans = "None";
    }

    // Return the result.
    return ans;
  }

