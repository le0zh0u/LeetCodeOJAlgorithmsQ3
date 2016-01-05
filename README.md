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
	之后想到的是，设置两个指针，分别指向string 的头（指针1）和尾（指针2），先指针2向指针1靠拢，并判断两个指针之间的子字符串是否有重复的字符，如果有则pass，使指针2向左移，或指针1向右移，如果没有则保存长度。
	
code:

	public class Solution {
    public int lengthOfLongestSubstring(String s) {
        int result = 0;
        if(s.equals("")){
            return 0;
        }
        for(int i = 0; i<s.length();i++){
            for(int j =s.length()-1;j>i;j--){
            	if((j-i)<=result){
                    break;
                }
                String subString = s.substring(i,j);
                Set set=new HashSet();
                for(int k=0; k<subString.length();k++){
                  set.add(subString.charAt(k));
                }
                if(subString.length() == set.size()){
                    int length = j-i+1;
                    result = result > length? result : length;
                }else{
                    continue;
                } 
            }
        }
        return result;
    }
	}
	
error:

	Last executed input:
	"hifqiqnpvuutkcpiodzrljdlslwlxnagxhwfylxvgtosvfdkjcdulihfudrtrtaoaywakvvqo"
		
	Submission Result: Time Limit Exceeded
	
	fuck！cao！

