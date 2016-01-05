# LeetCodeOJAlgorithmsQ3
LeetCodeOJ Algorithms Question3

Question Name :
Longest Substring Without Repeating Characters

Given a string, find the length of the longest substring without repeating characters. For example, the longest substring without repeating letters for "abcabcbb" is "abc", which the length is 3. For "bbbbb" the longest substring is "b", with the length of 1.
	
thinking:

	遍历String字符串，将每个字符存入hashset中，获取hashset的长度值即为结果。
	
code:
	
	public class Solution {
    public int lengthOfLongestSubstring(String s) {
        int result = 0;
        Set set=new HashSet();
        for(int i=0; i<s.length();i++){
            set.add(s.charAt(i));
        }
        result = set.size();
        
        return result;
    }
	}
	
error:

	Input:
		"pwwkew"
	Output:
		4
	Expected:
		3
		
	I do not know why!
	
think：
	
	继续寻找规律，发现the longest substring without repeating letters for "abcabcbb" is "abc"，For "bbbbb" the longest substring is "b"，如果输入为"pwwkew"，那没有重复的子字符串为“kew”，之前没有理解substring的含义。打算用HashMap做，记得可以在map查key值比较快
	
code:
	
	public class Solution {
    public int lengthOfLongestSubstring(String s) {
        int result = 0;
        HashMap<String,String> map = new HashMap<String,String>();
        for(int i=0;i<s.length();i++){
            String strItem =  String.valueOf(s.charAt(i));
            if(map.get(strItem) != null){
                if(map.size()>result){
                    result = map.size();
                }
                map = new HashMap<String,String>();
            }
            map.put(strItem,strItem);
        }
        if(map.size()>result){
            result = map.size();
        }
        
        return result;
    }
	}
	
error:
	
	Input:
		"dvdf"
	Output:
		2
	Expected:
		3
		
think:
	
	根据之前写的算法，碰到这样的字符串确实不对，继续想。

