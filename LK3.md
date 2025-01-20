class Solution {
public:
    int lengthOfLongestSubstring(string s) 
    {
        int n=s.size();//循环次数
        int ans=0;//结果
        unordered_set<char> set;//保证数组不重复
        int right=0;//右边界
        int left=0;//左边界
        for(;right<n;right++)
        {
            char ch=s[right];//取右边界
            while(set.count(ch))//当set中存在右边界时
            {
                char c=s[left];//单独取左边界
                set.erase(c);//删除左边界
                left++;//左边界右推
            }
            set.insert(ch);//插入原本重复的
            ans=max(ans,right-left+1);//每次结束挑选最大距离
        }    
        return ans;        
    }
};
