*Problem1: https://leetcode.com/problems/valid-anagram/description/*

```go
func isAnagram(s string, t string) bool {
    if len(s) != len(t) {
        return false
    }
    
    counter := make([]int, 26)
    
    for i, _ := range s {
        counter[s[i] - 'a']++
        counter[t[i] - 'a']--
    }
    
    for i, _ := range counter {
        if counter[i] != 0 {
            return false
        }
    }
    
    return true
}
```

*Problem 2: https://leetcode.com/problems/encode-and-decode-tinyurl/description/*

```java
import java.security.*;
import java.util.Base64;

public class Codec {

    HashMap<Character,Character> runes;
    HashMap<String,String> urls;
    String host;
    
    Codec() {
        this.urls = new HashMap<String,String>(); 
        this.runes = new HashMap<Character,Character>(); 
        this.initRuneMap();
        this.host = "http://thuc.com.vn/";
        
    }
        
    // Encodes a URL to a shortened URL.
    public String encode(String longUrl)  {
        try {
            MessageDigest md = MessageDigest.getInstance("MD5");
            String shortPart = new String(Base64.getEncoder().encode(md.digest(longUrl.getBytes("UTF-8"))), "UTF-8");
            String magicWords = this.runize(shortPart);
            this.urls.put(magicWords, longUrl);
            return this.host + magicWords;
        } catch(Exception e){
            
        }
        
        return longUrl;
    }

    // Decodes a shortened URL to its original URL.
    public String decode(String shortUrl) {
        String shortPart = shortUrl.substring(this.host.length());
        if (!this.urls.containsKey(shortPart)) {
            return "";
        }
        
        return this.urls.get(shortPart);
    }
    
    private String runize(String origin) {
        String magicWords = "";
        for (char ch: origin.toCharArray()) {
            if (this.runes.containsKey(ch)) {
                magicWords += this.runes.get(ch);
            } else {
                magicWords += ch;
            }
        }
        return magicWords;
    }
    
    private void initRuneMap() {
        // abcdefghijklmnopqrstuvwxyz
        // ??????????????????????????????????????????????????????????????????????????????
        this.runes.put('a', '???');
        this.runes.put('b', '???');
        this.runes.put('c', '???');
        this.runes.put('d', '???');
        this.runes.put('e', '???');
        this.runes.put('f', '???');
        this.runes.put('g', '???');
        this.runes.put('h', '???');
        this.runes.put('i', '???');
        this.runes.put('j', '???');
        this.runes.put('k', '???');
        this.runes.put('l', '???');
        this.runes.put('m', '???');
        this.runes.put('n', '???');
        this.runes.put('o', '???');
        this.runes.put('p', '???');
        this.runes.put('q', '???');
        this.runes.put('r', '???');
        this.runes.put('s', '???');
        this.runes.put('t', '???');
        this.runes.put('u', '???');
        this.runes.put('v', '???');
        this.runes.put('w', '???');
        this.runes.put('x', '???');
        this.runes.put('y', '???');
        this.runes.put('z', '???');
        this.runes.put('A', '???');
        this.runes.put('B', '???');
        this.runes.put('C', '???');
        this.runes.put('D', '???');
        this.runes.put('E', '???');
        this.runes.put('F', '???');
        this.runes.put('G', '???');
        this.runes.put('H', '???');
        this.runes.put('I', '???');
        this.runes.put('J', '???');
        this.runes.put('K', '???');
        this.runes.put('L', '???');
        this.runes.put('M', '???');
        this.runes.put('N', '???');
        this.runes.put('O', '???');
        this.runes.put('P', '???');
        this.runes.put('Q', '???');
        this.runes.put('R', '???');
        this.runes.put('S', '???');
        this.runes.put('T', '???');
        this.runes.put('U', '???');
        this.runes.put('V', '???');
        this.runes.put('W', '???');
        this.runes.put('X', '???');
        this.runes.put('Y', '???');
        this.runes.put('Z', '???');
    }
}

// Your Codec object will be instantiated and called as such:
// Codec codec = new Codec();
// codec.decode(codec.encode(url));
```
