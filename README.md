# Algorithmic Problems

### **Array**

- [**Two Sum](https://leetcode.com/problems/two-sum/):** Find two numbers in an array that add up to a specific target.

```jsx
 vector<int> ans;
        unordered_map<int, int> v;
        int n = nums.size();

        for (int i = 0; i < n; i++) {
            if (v.find(target - nums[i]) != v.end()) {
                ans.push_back(i);
                ans.push_back(v[target - nums[i]]);
                break;
            } else {
                v[nums[i]] = i;
            }
        }
        return ans;
```

- [**Remove Duplicates from Sorted Array](https://leetcode.com/problems/remove-duplicates-from-sorted-array/):** Remove duplicates from a sorted array in-place.

```jsx
  int j=1;    //j defines where we need to add unique elements
        for(int i=1;i<nums.size();i++){
            if(nums[i]==nums[i-1]){
                //duplicate
                continue;
            }
            else{
                //new element
                //override at j
                nums[j]=nums[i];
                j++;
            }
        }
        return j;
```

- [**Best Time to Buy and Sell Stock I](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/):** Find the maximum profit you can achieve from one transaction.

```jsx
 int profit = 0, MinPrice = INT_MAX;
        // buy in lower and sell in higher
        // ma profilet -> min lower and max higher
        for (auto price : prices) {
            MinPrice = min(MinPrice,price); // keep maintaining min element till current
            profit = max(profit, price - MinPrice);
        }
        return profit;
```

- [**Intersection of Two Arrays](https://leetcode.com/problems/intersection-of-two-arrays/):** Find the intersection of two arrays.

```jsx
use map

or

 vector<int>ans;
      sort(nums1.begin(),nums1.end());
      sort(nums2.begin(),nums2.end());  
      
      int n1=nums1.size(),n2=nums2.size();
     int t1=0,t2=0,k=0;
      while(t1<n1 && t2<n2)
      {
        if(nums1[t1]==nums2[t2])
        {
          if(k==0)    //used when we insert first element
          {
            ans.push_back(nums1[t1]);
            k++;
          }
          else if(ans[k-1]!=nums1[t1]) //used to check dulicates
          {
             ans.push_back(nums1[t1]);
             k++;
          }
          t1++;
          t2++;

        }
        else if(nums1[t1]>nums2[t2])
        {
          t2++;
        }
        else
        {
          t1++;
        }
      } 
      return ans;
```

- [**Move Zeroes](https://leetcode.com/problems/move-zeroes/):** Move all zeros in an array to the end without changing the relative order of non-zero elements.

```jsx
 int i=0,j=0;
        //i is for trversal and j is on 0th index
        for(int i=0;i<nums.size();i++)
        {
            //i -> traversal
            //j -> defines where zero element is present
            if(nums[i]!=0)
            {
                swap(nums[i],nums[j]);
                //now new possiblity of zero element is at j+1
                j++;
            }
            
        }
```

- [**Maximum Subarray](https://leetcode.com/problems/maximum-subarray/):** Find the maximum sum of a contiguous subarray.

```jsx
//let's use kadane first

        int maxSum=INT_MIN,curSum=0,maxEl=INT_MIN;
        for(int i=0;i<nums.size();i++){
            maxEl=max(maxEl,nums[i]);
            curSum+=nums[i];
            if(curSum<0)
            {
                curSum=0;
            }
            else{      
                if(curSum>maxSum)
                maxSum=curSum;
            }
        }
        if(maxSum!=INT_MIN)
        return maxSum;
        else
        return maxEl;
```

---

### **String**

- [**Valid Anagram](https://leetcode.com/problems/valid-anagram/):** Check if two strings are anagrams of each other.

```jsx
 sort(s.begin(),s.end());
  sort(t.begin(),t.end());
    return s==t;
```

- [**Implement strStr()](https://leetcode.com/problems/implement-strstr/):** Find the first occurrence of a substring in a string.

```jsx
int strStr(string haystack, string needle) {
        for(int i=0;i<haystack.size();i++){
            string temp=haystack.substr(i,needle.size());
            if(temp==needle)
            return i;
        }
        return -1;
    }
```

- [**Reverse String](https://leetcode.com/problems/reverse-string/):** Reverse a string in place.

```jsx
 stack<char>st;
      
      for(int i=0;i<s.size();i++)
      {
        st.push(s[i]);
      }
      
      for(int i=0;i<s.size();i++)
      {
          if(!st.empty())
          {
            s[i]=st.top();
            st.pop();
          }
          else
          {
            break;
          } 
      }
```

- [**First Unique Character in a String](https://leetcode.com/problems/first-unique-character-in-a-string/):** Find the first non-repeating character in a string.

```jsx
 unordered_map<char, int> frequency;
        int ans = 0;
        for (int i = 0; i < s.size(); i++) {
            frequency[s[i]]++;
        }
        for (int i = 0; i < s.size(); i++) {
            if (frequency[s[i]] == 1) {
                return i;
            }
        }

        return -1;
```

- [**Valid Palindrome](https://leetcode.com/problems/valid-palindrome/):** Check if a string is a palindrome considering only alphanumeric characters.

```jsx
 int i=0,j=s.size()-1;   //start and end

        while(i<j){
            //check for special characters
            //remove all special char from start and 
            //move i to alpha numberic value
            while(i<j && !isalnum(s[i])){
                i++;
            }
            
            //remove all special char from end and 
            //move j to alpha numberic value
            while(i<j && !isalnum(s[j])){
                j--;
            }

            //now check for palindrome
            if(tolower(s[i])!=tolower(s[j])){
                return false;
            }else{
                i++;
                j--;
            }
        }
        return true;
```

---

### **Linked List**

- [**Reverse Linked List](https://leetcode.com/problems/reverse-linked-list/):** Reverse a singly linked list.

```jsx
 if(head==NULL)
        {
            return head;
        }
        ListNode* prev=NULL;
        ListNode* curr=head;
        ListNode* nextptr=head->next;
        
        while(curr!=NULL)
        {
            //We assign curr next to prevptr
            curr->next=prev;
            
            //move all forword
            
            prev=curr;
            curr=nextptr;
            if(nextptr!=NULL)
            nextptr=nextptr->next;
        }
        return prev;
```

- [**Merge Two Sorted Lists](https://leetcode.com/problems/merge-two-sorted-lists/):** Merge two sorted linked lists into one sorted list.

```jsx
      			//Create base conditions
            //Use 2 pointer 'l1' 'l2' for 2 list traversal and
            //create new node 'ans' and pointer 'l3' for merged list
            //point smaller node in next of 'l3->next=l1' and increase pointers
            //Now insert pending elemnts of list if one of list reached to end

            //Base conditions

            if(list1==NULL && list2==NULL)
            {
              return {};
            }
            else if(list1==NULL && list2!=NULL)
            {
              return list2;
            }
            else if(list1!=NULL && list2==NULL)
            {
              return list1;
            }
            else
            {
            ListNode* ans=new ListNode(); //Wil store sorted & merged list
            ans->val=-1;  //Dummy node

            ListNode* l1=list1;   //used to travesal in list1
            ListNode* l2=list2;   //used to travesal in list2
            ListNode* l3=ans;    //used for traversal in ans

            while(l1!=NULL && l2!=NULL)
            {
              if(l1->val==l2->val)
              {
                //No need of creation of new node and insertion
                //Just point l3 to smaller noded
                l3->next=l1;
                l1=l1->next;
                l3=l3->next;

                l3->next=l2;
                l2=l2->next;
                l3=l3->next;
              }
              else if((l1->val)<(l2->val))
              {
                l3->next=l1;
                l1=l1->next;
                l3=l3->next;
              }
              else
              {
                l3->next=l2;
                l2=l2->next;
                l3=l3->next;
              }
            }

              //Now what if any one linked list is reached to end
              //and another is still left

              //So we have to make insert rest of elements in l3 in case
              //of any one linked list reached to end early

              //Some elemet still left in l1
              while(l1!=NULL)
              {
                l3->next=l1;
                l1=l1->next;
                l3=l3->next;
              }
              //Some elemet still left in l2
               while(l2!=NULL)
              {
                l3->next=l2;
                l2=l2->next;
                l3=l3->next;
              }
              return ans->next;   //As we first inserted -1 as dummy node
            }
            
```

```jsx
 // Recursive way
        ListNode* ans;

        // In the case if 1 list reached to end and
        // 1 is still left to insert in merges list
        if (list1 == NULL) {
            return list2;
        }
        if (list2 == NULL) {
            return list1;
        }

        // Now compare values
        if (list1->val <= list2->val) {
            ans = list1; // Directly assign smaller values
            ans->next = mergeTwoLists(list1->next, list2);
            // and for next value put recursive call
        } else {
            ans = list2;
            ans->next = mergeTwoLists(list1, list2->next);
        }
```

- [**Linked List Cycle](https://leetcode.com/problems/linked-list-cycle/):** Detect if a linked list has a cycle.

```jsx
ListNode* slow=head;    //1 move
        ListNode* fast=head;    //2 move
        if(head==NULL || head->next==NULL || head->next->next==NULL)
        {
            return false;
        }
        while(slow!=NULL && fast!=NULL && fast->next!=NULL)
        {
            slow=slow->next;
            fast=fast->next->next;
            //if it contains cycle at any given point both slow and fast
            //will colide
            if(slow==fast)
            {
                return true;
            }
        }
        return false;
```

- [**Palindrome Linked List](https://leetcode.com/problems/palindrome-linked-list/):** Check if a linked list is a palindrome.

```jsx
//TC : 3*O(n/2)
      //For all 3 steps

      //3 steps

      //1 find middle and put slow on middle
      //2 reverse right half
      //2 compare slow with begining usin dummy node step by step
      
        ListNode* dummy=head;
        ListNode* slow=head;
        ListNode* fast=head;

        //edge case
        if(head==NULL || head->next==NULL)
        {
          return true;
        }
        //1

        //fast 2 step and slow 1 step

        while(fast->next!=NULL && fast->next->next!=NULL)
        {
            slow=slow->next;
            fast=fast->next->next;
        }

        //now slow is middle node

        //2 reverse right half
        
        slow->next=reverse(slow->next);
      slow=slow->next;  //as we have to compare with right half
        //3
        //compare with dummy

        while(slow!=NULL)
        {
            if(slow->val!=dummy->val)
            {
                return false;
            }
            slow=slow->next;
            dummy=dummy->next;
        } 
        return true; 
    }
};
```

- [**Delete Node in a Linked List](https://leetcode.com/problems/delete-node-in-a-linked-list/):** Delete a node in a singly linked list, given only access to that node.

```jsx
 //Trick is just to update node with current next
        //ex : [4,5,1,9] and node=1
        //simpley -> update 1 is node 
        //simpley change node to 9 and move next pointer to
        //next of 9
        
      ListNode* nxt=node->next;
      
      node->val=nxt->val;       //Vale is updated
      node->next=nxt->next; //next pointer also updated
      
      delete nxt;
```

---

### **Recursion**

- [**Climbing Stairs](https://leetcode.com/problems/climbing-stairs/):** Count ways to climb a staircase with 1 or 2 steps at a time.

```jsx
 int findSteps(vector<int>&memoizedArray,int  n){
        if(n==0 || n==1 || n==2)
        {
            return memoizedArray[n]=n;
        }

        if(memoizedArray[n]!=0)
        return memoizedArray[n];

        int take1=findSteps(memoizedArray,n-1);
        int take2=findSteps(memoizedArray,n-2);
        return memoizedArray[n]=take1+take2;
        
    }
    
    int climbStairs(int n) 
    {
        //Observations

        //total n steps to climb
        //each time we can climb 1 or 2 step -> choice
        //Goal  dnumber of distinct ways to climb the top

        //Approach 

        //recursion TC  exponenstial
        //TLE : 31/45

        //base case
        // if(n==0 || n==1 || n==2)
        // {
        //     return n;
        // }

        // int take1=climbStairs(n-1);
        // int take2=climbStairs(n-2);
        // return take1+take2;

        //Approach 2

        //memoize TC O(n)

        //base case
        vector<int>memoizedArray(n+1,0);

        return findSteps(memoizedArray,n);
    }
```

- [**Fibonacci Number](https://leetcode.com/problems/fibonacci-number/):** Find the nth Fibonacci number.

```jsx
class Solution {
public:
int solve(vector<int>&dp,int n){
     if(n==0 || n==1)
        {
            return dp[n]=n;
        }
        if(dp[n]!=0)
        return dp[n];

        return dp[n]=solve(dp,n-1)+solve(dp,n-2);
}
    int fib(int n) 
    {
        // TC  eponential
        // if(n==0 || n==1)
        // {
        //     return n;
        // }

        // return fib(n-1)+fib(n-2);

        //Approach 2 memoize

        vector<int>dp(n+1,0);

        return solve(dp,n);
        
    }
};
```

- [**Reverse String](https://leetcode.com/problems/reverse-string/):** Reverse a string using recursion.

```jsx
 int i=0,j=s.size()-1;

    while(i<j){
        swap(s[i],s[j]);
        i++;
        j--;
    }
```

- [**Power of Three](https://leetcode.com/problems/power-of-three/):** Check if a number is a power of three.

```jsx
if (n <= 0)
            return false;
        while (n % 3 == 0) {
            n /= 3;
        }
        return n == 1;
```

- [**Factorial Trailing Zeroes](https://leetcode.com/problems/factorial-trailing-zeroes/):** Count trailing zeroes in the factorial of a number.

```jsx
  // Approach TC log(n)

        // return n / 3125 + n / 625 + n / 125 + n / 25 + n / 5;
        //or
        int totalzeros = 0;
        while (n >= 5) {
            totalzeros += n / 5; // Count the multiples of 5
            n /= 5;         // Reduce n to account for higher powers of 5
        }
        return totalzeros;
    }
```

---

### **Dynamic Programming (DP)**

- [**Climbing Stairs](https://leetcode.com/problems/climbing-stairs/):** Count ways to climb a staircase using DP.

Repeated

- [**House Robber](https://leetcode.com/problems/house-robber/):** Maximize loot from houses without robbing two adjacent ones.

```jsx
int solve(vector<int>&nums, vector<int>&dp,int ind){
        if(ind>=nums.size())
        return 0;
        if(dp[ind]!=-1)
        return dp[ind];

        int robCurr=nums[ind]+solve(nums,dp,ind+2);
        int skipCurr=solve(nums,dp,ind+1);
        return dp[ind]=max(robCurr,skipCurr);
    }
    int rob(vector<int>& nums) {
        //Choices

        //either rob and skip next one
        //dont rob and rob next one
        vector<int>dp(nums.size()+1,-1);
        return solve(nums,dp,0);
    }
```

- [**Pascal's Triangle](https://leetcode.com/problems/pascals-triangle/):** Generate Pascal's triangle up to a given number of rows.

```jsx
 vector<vector<int>>ans; 

        ans.push_back({1});
        for(int i=1;i<numRows;i++){
            vector<int>prevRow=ans[i-1];
            vector<int>currRow(prevRow.size()+1,0);
            //for corner
            //1st and last will be same
            currRow[0]=prevRow[0];
            currRow[currRow.size()-1]=prevRow[prevRow.size()-1];

            //for rest
            for(int i=1;i<prevRow.size();i++){
                currRow[i]=prevRow[i-1]+prevRow[i];
            }
            ans.push_back(currRow);
        }
        return ans;
```

---

### **Stack/Queue**

- [**Valid Parentheses](https://leetcode.com/problems/valid-parentheses/):** Check if parentheses are balanced in a string.

```jsx
 //Contine pushing  opning brackets 
      //If  found closing than check top 
      //if its not same type than return false
      
      stack<char>st;
      for(int i=0;i<s.length();i++)
      {
        
        if(s[i]=='(' || s[i]=='{' || s[i]=='[')
        {
           st.push(s[i]);   
        }
        else
        {
          if(st.empty())
          {
            return false;
          }
          if(s[i]==')' && st.top()!='(')
          {
            return false;
          }
          if(s[i]=='}' && st.top()!='{')
          {
            return false;
          }
          if(s[i]==']' && st.top()!='[')
          {
            return false;
          }
          else
          {
             st.pop(); 
          }
                   
        }
            
      }
      if(st.empty())
      {
          return true;
      }
      else
      {
          return false;   
      }
      
      
      
```

- [**Min Stack](https://leetcode.com/problems/min-stack/):** Design a stack that supports push, pop, and retrieving the minimum element in constant time.

```jsx
  //use vector of pair
    //store {value, min element til current}
    vector<pair<int,int>>vec;

    MinStack() {
    }

    void push(int val) {
        if(vec.empty())
      vec.push_back({val,val});
      else
      vec.push_back({val,min(val,vec.back().second)});

      //if empty vector -> puhs valaues
      //if not empty store -> value and min of top and value
    }

    void pop() { 
        vec.pop_back();
    }

    int top() { 
        return vec.back().first;
     }

    int getMin() {
       return vec.back().second;
    }
```

- [**Implement Queue Using Stacks](https://leetcode.com/problems/implement-queue-using-stacks/):** Implement a queue using two stacks.

```jsx
 stack<int>primary;
  stack<int> temp;
    MyQueue() 
    {
        
    }
    
    void push(int x) 
    {
        //Here we push elements in primary bit as its follow FIFO
      
        //step 1 remove all from primary and push in temp
        //step 2 Than push x in primary
        //step 3 Than pop all from temp and push in primary
    
       
      if(primary.empty())
      {
        primary.push(x);
      }
      else
      {
        
         //step 1
        while(!primary.empty())
        {
          int tem=primary.top();
          temp.push(tem);
          primary.pop();
        }
      //step 2
        primary.push(x);
      //step 3
        while(!temp.empty())
        {
          int tem2=temp.top();
          primary.push(tem2);
          temp.pop();
        }
        
        
      }
    }
    
    int pop() //This is tricky but intresting
    {
      //But check that we have alreafy pushed elements in reverse order
      //So in ordinary stack push 1 than 2 than 3 will be 1 2 3
      //But in our case it will be 3 2 1
      //so when we pop it first removes 1 which looks like front
        
      int poped=primary.top();
      primary.pop();
      return poped;
    }
    
    int peek() 
    {
        return primary.top();
    }
    
    bool empty() 
    {
        return primary.empty();
    }
```

- [**Implement Stack Using Queues](https://leetcode.com/problems/implement-stack-using-queues/):** Implement a stack using two queues.

```jsx
 queue<int>q1;
    queue<int>q2;
    MyStack() 
    {
        
    }
    
    void push(int x) 
    {
        q1.push(x);
    }
    
    int pop() 
    {
        if(q1.empty())
        return -1;
        else
        {
            while(q1.size()>1)
            {
                q2.push(q1.front());
                q1.pop();
            }
            int topel=q1.front();
            q1.pop();   //imp
           
            while(!q2.empty())
            {
                q1.push(q2.front());
                q2.pop();
            }    
        return topel;
        }
        
    }
    
    int top() 
    {
        if(q1.empty())
        return -1;
        else
        return q1.back();
    }
    
    bool empty() {
        return q1.empty();
    }
```

- [**Baseball Game](https://leetcode.com/problems/baseball-game/):** Simulate a baseball game using a stack.

```jsx
stack<int> st;
        for (auto str : operations) {

            if (str == "C") {
                st.pop();
            } else if (str == "+") {
                int first = st.top();
                st.pop();
                int second = st.top();
                st.push(first);
                st.push(first + second);
            } else if (str == "D") {
                int first = st.top();
                st.push(first * 2);
            }else{
                st.push(stoi(str));
            }
        }
        int sum = 0;
        while (!st.empty()) {
            sum += st.top();
            st.pop();
        }
        return sum;
```

---

### **Trees**

- [**Maximum Depth of Binary Tree](https://leetcode.com/problems/maximum-depth-of-binary-tree/):** Find the maximum depth of a binary tree.

```jsx
 //base condition
        if(root==NULL)
        return 0;
        if(root->left==NULL && root->right==NULL){
            return 1;
        }

        //return max from both side
        int leftSide=maxDepth(root->left);
        int rightSide=maxDepth(root->right);
        //basically current + recursively find max from both side
        return 1+max(leftSide,rightSide);
```

- [**Symmetric Tree](https://leetcode.com/problems/symmetric-tree/):** Check if a binary tree is symmetric.

```jsx
 bool compare(TreeNode* p, TreeNode* q) {
        // Base case
        if ((p == NULL && q != NULL) || (p != NULL && q == NULL)) {
            return false;
        }
        if (p == NULL && q == NULL) {
            return true;
        }
        if (p->val != q->val) {
            return false;
        }

        bool first = compare(p->left, q->right);
        bool second = compare(p->right, q->left);
        if (first && second) {
            return true;
        } else {
            return false;
        }
    }
    bool isSymmetric(TreeNode* root) {
        // Same as traverse both part but compare left with right
        // Just divide tree into 2 parts and than compare
        // Base case

        return compare(root->left, root->right);
    }
```

- [**Path Sum](https://leetcode.com/problems/path-sum/):** Check if a binary tree has a root-to-leaf path with a given sum.

```jsx
 if(root==NULL){
            return false;
        }
        if(root->left==NULL && root->right==NULL){
            if(targetSum-root->val==0){
                //has a path
                return true;
            }
            else{
                return false;
            }
        }

        bool leftSide=hasPathSum(root->left,targetSum-root->val);
        bool rightSide=hasPathSum(root->right,targetSum-root->val);
        return leftSide||rightSide;
```

- [**Invert Binary Tree](https://leetcode.com/problems/invert-binary-tree/):** Invert a binary tree (mirror image).

```jsx
 void traverse(TreeNode* &root)
  {
    if(root==NULL)
    {
      return;
    }
    TreeNode* temp=NULL;  //used for swapping
    
    //Apply swapping
    
    temp=root->left;
    root->left=root->right;
    root->right=temp;
   
    traverse(root->left);
    traverse(root->right);   
  }
    TreeNode* invertTree(TreeNode* root) 
    {   
      //Apply simple travesal in root
      //Use temp node to swap
      traverse(root);
      return root;
    }
```

- [**Same Tree](https://leetcode.com/problems/same-tree/):** Check if two binary trees are identical.

```jsx
 if((p==NULL && q!=NULL) || (p!=NULL && q==NULL)){
            return false;
        }
        if(p==NULL && q==NULL){
            return true;
        }
        if(p->val!=q->val)
        {
            return false;
        }

        if(isSameTree(p->left,q->left)==false || isSameTree(p->right,q->right)==false){
            return false;
        }else{
            return true;
        }
```

---

### **Graph**

- [**Find Center of Star Graph](https://leetcode.com/problems/find-center-of-star-graph/):** Find the center node of a star graph.

```jsx
 unordered_map<int,int>mp;
       int count=0;
       for(int i=0;i<edges.size();i++){
            mp[edges[i][0]]++;
            mp[edges[i][1]]++;
       }

       for(auto n:mp){
            if(n.second==edges.size()){
                return n.first;
            }
       }
       return -1;
```

- [**Flood Fill](https://leetcode.com/problems/flood-fill/):** Perform a "paint fill" operation on a 2D grid.

```jsx
void dfs(int i,int j,vector<vector<int>>& image,int initialColor, 
         int newColor)
    {
        //Lets check boudry of our matrix
    int n=image.size();
    int m=image[0].size();
    
    //Now erase all conition where we have to return
    
    if(i<0 || j<0 || i>=n || j>=m)
    {
        return;
    }
    
    if(image[i][j]!=initialColor)
    {
        //Its a invalid cell
        //Thats why we dont need to use visited vector
        return;
    }
    
    //Now update value
    image[i][j]=newColor;
    
    //Now put recurive dfs call for all 4 directions
    
    dfs(i+1,j,image,initialColor,newColor);
    dfs(i,j+1,image,initialColor,newColor);
    dfs(i-1,j,image,initialColor,newColor);
    dfs(i,j-1,image,initialColor,newColor);     
    }
    vector<vector<int>> floodFill(vector<vector<int>>& image, int sr, int sc, int color) {
            //Lets solve using DFS
        
        //image -->given matrix
        //sr --> row
        //sc --> colum
        //new colo--> color

        // we only have to go if it has same color as current color
        //ex current initial Color is 3 and we update it to 6
        //but we only go next if it has color 3
        
        int initialColor=image[sr][sc];
        int newColor=color;
        //if current initial color is same as new color we dont need to put ewcursive call
        if(initialColor!=newColor)
        {
            dfs(sr,sc,image,initialColor,newColor);
        }
        return image;
    }
```

- [**Island Perimeter](https://leetcode.com/problems/island-perimeter/):** Calculate the perimeter of an island in a grid.

```jsx
 int dfs(vector<vector<int>>& grid, int i, int j, vector<vector<int>>& vis) {
        // boundires
        int n = grid.size();
        int m = grid[0].size();
        if (i < 0 || j < 0 || i >= n || j >= m) {
            //boundry cell also gives 1
            return 1;
        }

        if (grid[i][j] == 0) {
            // that means it's water which will add 1 parimeter
            return 1;
        }

        if (vis[i][j] != -1) {
            return 0;
        }
        // mark visited
        vis[i][j] = 0;

        // check permiter

        int leftSide = 0, rightSide = 0, upperSide = 0, lowerSide = 0;
        // left side

        leftSide = dfs(grid, i, j - 1, vis);
        upperSide = dfs(grid, i - 1, j, vis);
        rightSide = dfs(grid, i, j + 1, vis);
        lowerSide = dfs(grid, i + 1, j, vis);

        return leftSide + upperSide + rightSide + lowerSide;
    }
    int islandPerimeter(vector<vector<int>>& grid) {
        // 1 -> land
        // 0 -> water

        // exactly 1 island
        // goal : determinde permeter of island
        // if null -> 1
        // if land ->0
        // if water -> 1

        // dfs -> each time found 1 check it's all 4 directions and calculate
        // parimerter
        int n = grid.size();
        int m = grid[0].size();
        vector<vector<int>> vis(n, vector<int>(m, -1));
        for (int i = 0; i < n; i++) {
            for (int j = 0; j < m; j++) {
                if (grid[i][j] == 1) {
                    return dfs(grid, i, j, vis);
                }
            }
        }
        return -1;
    }
```

- [**Find the Town Judge](https://leetcode.com/problems/find-the-town-judge/):** Find the judge in a graph representing trust relationships.

```jsx
//count indegree and outdegree vectors
        //if any node that have indegree n-1 and outdegree 0
        //that is our answer

        //code

        //corner case
        if(n==1)
        {
            return 1;
        }

       int res=0;
       unordered_map<int,int>indeg;
       unordered_map<int,int>outdeg;
       for(auto vec:trust)
       {
           indeg[vec[1]]++;
           outdeg[vec[0]]++;
       }
       for(auto it:indeg)
       {
           if(it.second==n-1 && outdeg[it.first]==0)
           {
               return it.first;
           }
       }
       return -1;
```

---
