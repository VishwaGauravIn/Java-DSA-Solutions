# Solution for Arrays Quetions from Leetcode

### Easy
1. [Build Array from Permutation](https://leetcode.com/problems/build-array-from-permutation/) </br>
Solution: 
```java
class Solution {
public int[] buildArray(int[] nums) {
int size=nums.length;
int[] a=new int[size];
for (int i = 0; i < size; i++) {
int product = (nums[nums[i]] % size) * size + nums[i];
a[i]=product;
}
for (int i = 0; i < size; i++) {
int temp = a[i];
a[i]=temp/size;
}
return a;
}
}
```

2. [Concatenation of Array](https://leetcode.com/problems/concatenation-of-array/)</br>
Solution: 
```java
class Solution {
    public int[] getConcatenation(int[] nums) {
        int  n= nums.length;
        int []ans= new int[nums.length*2];
        
        for(int i= 0; i< nums.length; i++){
            ans[i]= nums[i];
            ans[i+n]= nums[i];
        }
        return ans;
    }
}
```
3. [Running Sum of 1d Array](https://leetcode.com/problems/running-sum-of-1d-array/) </br>
Solution: 
```java
class Solution {
    public int[] runningSum(int[] nums) {
        for (int i = 1; i < nums.length; i++) 
            nums[i] = nums[i] + nums[i-1];
        return nums;
    }
}
```
4. [Richest Customer Wealth](https://leetcode.com/problems/richest-customer-wealth/) </br>
Solution: 
```java
class Solution {
     public int maximumWealth(int[][] accounts) {
        int max = Integer.MIN_VALUE;
        for(int[] row:accounts){
            int curr = 0;
            for(int num: row){
                curr = curr + num;
            }
            max = Math.max(curr, max);
        }
        return max;
    }
}
```
5. [Shuffle the Array](https://leetcode.com/problems/shuffle-the-array/) </br>
Solution: 
```java
class Solution {
    public int[] shuffle(int[] nums, int n) {
        int ans[]=new int[2*n];
        int k=0; int i=0;
        while(i<nums.length){
            ans[i]=nums[k];
            ans[i+1]=nums[n];
            n++;
            k++;
            i+=2;
        }
        return ans;
        }
    }
  ```
6. [Kids With the Greatest Number of Candies](https://leetcode.com/problems/kids-with-the-greatest-number-of-candies/) </br>
Solution: 
```java
class Solution {
public List kidsWithCandies(int[] candies, int extraCandies) {
ArrayList array = new ArrayList<>();
int max = Integer.MIN_VALUE;
//find maximum
for(int i=0;i<candies.length;i++){
if(candies[i]>=max){
max = candies[i];
}
}
//add true if after adding extraCandies becomes greater than max.
for(int i=0;i<candies.length;i++){
array.add(candies[i]+extraCandies>=max);
}
return array;
}
}
```
7. [Number of Good Pairs](https://leetcode.com/problems/number-of-good-pairs/) </br>
Solution:
```java
class Solution {
    public int numIdenticalPairs(int[] nums) {
        int count=0;
        for(int i=0;i<nums.length;i++){
            for(int j=i+1;j<nums.length;j++){
                if(nums[i]==nums[j]){
                    count++;
                }
            }
        }
        return count;
    }
}
```
8. [How Many Numbers Are Smaller Than the Current Number](https://leetcode.com/problems/how-many-numbers-are-smaller-than-the-current-number/) </br>
Solution: 
```java
class Solution {
    public int[] smallerNumbersThanCurrent(int[] nums) {
        
        int[] ans= new int[nums.length];
        HashMap<Integer,Integer> map = new HashMap<>();
        int[] duplicate =new int[nums.length];
        
        for(int i=0;i<nums.length;i++){
            duplicate[i]=nums[i];
        }
        
        int p=0;int index=0;
        
        Arrays.sort(nums);
        System.out.println(Arrays.toString(nums));
        
        for(int i=0;i<nums.length;i++){
            if(i>0){
                if(nums[i]==nums[i-1]){
                    map.put(nums[i],index);
                    continue;
                }
            }
            index=i;
            map.put(nums[i],index);
        }
         for(int i=0;i<nums.length;i++){
              ans[i]= map.get(duplicate[i]);
         }
        return ans;
    }
}
```
9. [Create Target Array in the Given Order](https://leetcode.com/problems/create-target-array-in-the-given-order/) </br>
Solution:
```java
class Solution {
   public int[] createTargetArray(int[] nums, int[] index) {
		//1. Create an arraylist of type Integer
        List<Integer> list = new ArrayList<>();
		//2. Using ArrayList.add() so that we don't have to manually reorder array elements on each add operation.
        for(int i=0; i<index.length; i++){
            list.add(index[i], nums[i]);
        }
        int[] array = new int[list.size()];
		//3. Fill the array with the elements in our ArrayList
        for(int i = 0; i < list.size(); i++){
            array[i] = list.get(i);
        }
    return array;
    }
}
```
10. [Check if the Sentence Is Pangram](https://leetcode.com/problems/check-if-the-sentence-is-pangram/) </br>
Solution:
```java
class Solution {
  public boolean checkIfPangram(String sentence) {
    boolean[] Check=new boolean[26];
    int index=0;
    for(int i=0;i<sentence.length();i++){
      if('a'<=sentence.charAt(i)&&sentence.charAt(i)<='z'){
      index=sentence.charAt(i)-'a';
    }
    else{
        continue;
     }
    Check[index]=true;
    }
    for(int i=0;i<26;i++){
      if(Check[i]==false){
      return false;
    }
    }
    return true;
  }
}
```

11. [Count Items Matching a Rule](https://leetcode.com/problems/count-items-matching-a-rule/) </br>
Solution:
```java
class Solution {
    public int countMatches(List<List<String>> items, String ruleKey, String ruleValue) {
          int a = 0,in;
        if(ruleKey.equals("type"))
            in = 0;
        else if(ruleKey.equals("color"))
            in = 1;
        else
            in = 2;
        for(int i=0;i<items.size();i++)
            if(items.get(i).get(in).equals(ruleValue))
                a++;
        return a;
    }
}
```
12. [Find the Highest Altitude](https://leetcode.com/problems/find-the-highest-altitude/)</br>
Solution: 
```java
class Solution {
    public int largestAltitude(int[] gain) {
         int result=gain[0];
        for(int i=1; i<gain.length; i++){
            gain[i]+=gain[i-1];
            result=Math.max(result,gain[i]);
            }
        if(result<0){
            return 0;
            }
        return result;
    }
}
```
13. [Flipping an Image](https://leetcode.com/problems/flipping-an-image/)</br>
Solution:
```java
class Solution {
    public int[][] flipAndInvertImage(int[][] image) {
        int n = image.length;
        int temp =0 ;
        for(int i=0; i <n; i++){
            for(int j=0; j<n/2; j++ ){
                temp = image[i][j];
                image[i][j] = image[i][n-j-1];
                image[i][n-j-1] = temp;  
            }
        }
         for(int i=0; i <n; i++){
            for(int j=0; j<n; j++ ){
                if(image[i][j]==0){
                    image[i][j]=1;
                }
                else{
                    image[i][j]=0;
                }
            }
        }
        return image;
    }
}
```
14. [Cells with Odd Values in a Matrix](https://leetcode.com/problems/cells-with-odd-values-in-a-matrix/)</br>
Solution:
```java
class Solution {
    public int oddCells(int m, int n, int[][] indices) {
        int result = 0; 
        int[][] matrix = new int[m][n];
        for(int[] index : indices) {
    	    int row = index[0];
    	    int col = index[1];
    	    for(int i = 0; i< n; i++)
    		    matrix[row][i]++;
    	    for(int i=0; i< m; i++)
    		    matrix[i][col]++;
        }
        for(int i =0; i<m; i++)
    	    for(int j = 0; j < n; j++) {
    		    if(matrix[i][j] % 2 == 1)
    			    result++;
    	    }
        return result; 
    }
}
```
15. [Matrix Diagonal Sum](https://leetcode.com/problems/matrix-diagonal-sum/)</br>
Solution:
```java
class Solution {
   public int diagonalSum(int[][] mat) {
	int len = mat.length;
	int start = 0, end = len - 1;
	int sum = 0;
	while(start < len && end >=0){
		if(start == end){
			sum += mat[start][end];
		}
		else{
			sum += mat[start][start];
			sum += mat[start][end];
		}
		start++;
		end--;
	}
	return sum;
}
}
```


16. [Find Numbers with Even Number of Digits](https://leetcode.com/problems/find-numbers-with-even-number-of-digits/)</br>
Solution:
```java
class Solution {
    public int findNumbers(int[] nums) {
        int ans=0;
        for(int i=0;i<nums.length;++i){
            int count =0;
        while (nums[i]>0){
            ++count;
            nums[i]/=10;
        }
        if(count%2==0) ++ans;
        }
        return ans;
}
}
```


17. [Transpose Matrix](https://leetcode.com/problems/transpose-matrix/)</br>
Solution:
```java
class Solution {
    public int[][] transpose(int[][] matrix) {
        int[][] transpose=new int[matrix[0].length][matrix.length];
        for(int i=0;i<matrix[0].length;i++){
            for(int j=0;j<matrix.length;j++){
                transpose[i][j]=matrix[j][i];
            }
        }
        return transpose;
    }  
       }
```


18. [Add to Array-Form of Integer](https://leetcode.com/problems/add-to-array-form-of-integer/)</br>
Solution:
```java
class Solution {
    public List<Integer> addToArrayForm(int[] num, int k) {
    List<Integer> ll = new ArrayList<Integer>();
   for(int i=num.length-1; i>= 0; i--){
        
         ll.add((num[i]+k)%10);
         k = (num[i]+k)/10;                      
    }
    
    System.out.println(k); 
    //still if K>0,  value left to add in list
    
    while(k>0){
        ll.add(k%10);
        k = k/10;
    } 
    
    Collections.reverse(ll);
    
    return ll;
}
    }
```


19. [Maximum Population Year](https://leetcode.com/problems/maximum-population-year/)</br>
Solution:
```java
class Solution {
    public int maximumPopulation(int[][] logs) {
          int minYear = 1950;
    int[] years = new int[101];
    
    for(int [] log : logs){
        
        for(int i=log[0]-minYear; i<log[1]-minYear; i++){
             years[i]++;
        }
       
        
    }
    int earliestYear= 0;
    int population=0;
    
    System.out.println(Arrays.toString(years));
    
    for(int i=0; i<years.length; i++){
        
        if(years[i]> population) {
            
            population = years[i];
            earliestYear = i+1950;  
        }
    }
    
    return earliestYear;
    
    
}
    }

```

20. [Determine Whether Matrix Can Be Obtained By Rotation](https://leetcode.com/problems/determine-whether-matrix-can-be-obtained-by-rotation/)</br>
Solution:
```java
class Solution {  
    public boolean findRotation(int[][] mat, int[][] target) {
        int n = mat.length;
        int[] res[] = new int[n][n];
        for (int i = 0; i < n; i++) { //clockwise 90
            for (int j = 0; j < n; j++) {
                res[i][j] = mat[n - 1 - j][i];
            }
        }
        
        int[] res2[] = new int[n][n];
        for (int i = 0; i < n; i++) { //clockwise 180
            for (int j = 0; j < n; j++) {
                res2[i][j] = res[n - 1 - j][i];
            }
        }
       
        int[] res3[] = new int[n][n];
        for (int i = 0; i < n; i++) { //clockwise 270
            for (int j = 0; j < n; j++) {
                res3[i][j] = res2[n - 1 - j][i];
            }
        }
        
		//compare to 90,180,270 and itself
        if(Arrays.deepEquals(target, res) || Arrays.deepEquals(target, res2) || Arrays.deepEquals(target, res3) || Arrays.deepEquals(target, mat) ){ 
            return true;
        }
        return false;
    }
}
```


21. [Two Sum](https://leetcode.com/problems/two-sum/)</br>
Solution:
```java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        
        HashMap<Integer,Integer> map = new HashMap<>();
        for(int i=0;i<nums.length;i++){
            int complement = target-nums[i];
            if(map.containsKey(complement)){
                return new int[]{map.get(complement),i};
            }else{
                map.put(nums[i],i);
            }
        }
        return new int[]{};
    }
}
```


22. [Find N Unique Integers Sum up to Zero](https://leetcode.com/problems/find-n-unique-integers-sum-up-to-zero/)</br>
Solution:
```java
class Solution {
  public int[] sumZero(int n) {
    int[] res = new int[n];
    int sum = 1;

    for (int i = 0; i < n; i++) {
      if (i == n - 1) res[i] = -sum + 1;
      else {
        res[i] = i + 1;
        sum += i + 1;
      }
    }
    return res;
  }
}
```


23. [Saddle Point In Matrix](https://leetcode.com/problems/lucky-numbers-in-a-matrix/)</br>
Solution:
```java
class Solution {
    public List<Integer> luckyNumbers (int[][] matrix) {
        ArrayList<Integer> list1=new ArrayList<>();
        int r=matrix.length;
        int c=matrix[0].length;
        
        for(int i=0;i<r;i++){
            int SmallCol=0;
            for(int j=1;j<c;j++){
                if(matrix[i][j]<matrix[i][SmallCol]){
                    SmallCol=j;
                }
            }
            
//             checking in the respective column if the element is the greatest
            boolean flag=true;
            for(int k=0;k<r;k++){
                if(matrix[k][SmallCol]>matrix[i][SmallCol]){
                    flag=false;
                    break;
                }
            }
            if(flag==true){
                list1.add(matrix[i][SmallCol]);
                break;
            }
            
            
           
        }
        
        return list1;
    }
}
```

### Medium
1. [Spiral Matrix](https://leetcode.com/problems/spiral-matrix/)</br>
Solution:
```java
class Solution {
    public List<Integer> spiralOrder(int[][] matrix) {
        
        List<Integer> ans = new ArrayList<> ();
        
        int minr = 0, minc = 0, maxr = matrix.length-1, maxc = matrix[0].length-1;
        int t = matrix.length*matrix[0].length, count = 0 ;
        
        while(count<t){
            
            for(int r = minr, c = minc ; c<=maxc && count<t; c++){
                ans.add(matrix[r][c]);
                count++;
            }
            minr++;
            
            for(int r = minr, c = maxc ; r<=maxr && count<t ; r++){
                ans.add(matrix[r][c]);
                count++;
            }
            maxc--;
            
            for(int r = maxr, c=maxc ; c>=minc && count<t ; c--){
                ans.add(matrix[r][c]);
                count++;
            }
            maxr--;
            
            for(int r = maxr, c=minc ; r>=minr && count<t ; r--){
                ans.add(matrix[r][c]);
                count++;
            }
            minc++;
            
        }
        return ans;
    }
}
```


2. [Set Matrix Zeroes](https://leetcode.com/problems/set-matrix-zeroes/)</br>
Solution:
```java
class Solution {
    public void setZeroes(int[][] matrix) {
        HashSet<Integer>colSet=new HashSet<Integer>();
        HashSet<Integer>rowSet=new HashSet<Integer>();
        for(int i=0;i<matrix.length;i++){
            for(int j=0;j<matrix[0].length;j++){
                if(matrix[i][j]==0){
                    colSet.add(j);
                    rowSet.add(i);
                }
            }
        }
        for(int i=0;i<matrix.length;i++){
            boolean hasRow=rowSet.contains(i);
            for(int j=0;j<matrix[0].length;j++){
                if(hasRow || colSet.contains(j)){
                    matrix[i][j]=0;
                }
            }
        }
    }
}
```


3. [Product of Array Except Self](https://leetcode.com/problems/product-of-array-except-self/)</br>
Solution:
```java
class Solution {
    public int[] productExceptSelf(int[] nums) {
        int prod=1;
        int numZero=0;
        for(int i:nums){
            if(i!=0){
                prod*=i;
            }else{
                numZero++;
            }
        }
        for(int i=0;i<nums.length;i++){
            if(numZero>0){
                if(numZero==1 && nums[i]==0)
                    nums[i]=prod;
                else
                    nums[i]=0;
            }else{
                nums[i]=(int)prod/nums[i];
            }
        }
        return nums;
    }
}
```


4. [Find First and Last Position of Element in Sorted Array](https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array/)</br>
Solution:
```java
class Solution {
  public int[] searchRange(int[] nums, int target) {
    
    int[] ans = new int[2];
    int c = 0;
    ans[0]=-1; ans[1]=-1;
      
    for (int i = 0 ; i < nums.length ; i++) {
        
      if (nums[i] == target) {
          
          if (c == 0) {
              ans[0] = i ;
              ans[1] = i;
           } else {
              ans[1] = i;
           }
          
        c++;
      }
    }
    return ans;
  }
}
```


5. [Jump Game](https://leetcode.com/problems/jump-game/)</br>
Solution:
```java
class Solution {
    public boolean canJump(int[] nums) {
        int current=0,destination=0;
        boolean ans=false;
        if(nums.length==1){
            ans=true;
            }
        for(int i=0;i<nums.length-1;i++){
            destination=Math.max(destination,i+nums[i]);

        if(i==current){
            current=destination;
            if(current>=(nums.length-1)){
                ans=true;
                
            }
        }
    }
    return ans;
}
}
```


6. [Rotate Array](https://leetcode.com/problems/rotate-array/)</br>
Solution:
```java
class Solution {
    public void rotate(int[] nums, int k) {
    //if k > length of array for that case
    k = k % nums.length;
    
    //reverse 1st part
    reverse(nums, 0, nums.length-k-1);
    
    //reverse 2nd part
    reverse(nums, nums.length-k, nums.length-1);
    
    //now reverse the full arrary
    reverse(nums, 0, nums.length-1);
    
}


 public static void reverse(int[] nums, int s, int e){
    
    int i = s;
    int j = e;
    
    while(i < j){
        int t = nums[i];
        nums[i] = nums[j];
        nums[j] = t;
        
        i++;
        j--;
    } 
}
    }

```

### Hard
1. [Max Value of Equation](https://leetcode.com/problems/max-value-of-equation/)</br>
Solution:
```java
class Solution {
    public int findMaxValueOfEquation(int[][] points, int k) {
        Deque<Integer> q = new ArrayDeque<>();
        int ans = Integer.MIN_VALUE;
        for (int i = 0 ; i < points.length; i++) {
            while (!q.isEmpty() && points[i][0] - points[q.peek()][0] > k)
                q.poll();
            if (!q.isEmpty())
                ans = Math.max(ans, points[i][0] + points[i][1] + points[q.peek()][1] - points[q.peek()][0]);
            while (!q.isEmpty() && points[q.peekLast()][1] - points[q.peekLast()][0] < points[i][1] - points[i][0])
                q.pollLast();
            // add current index to the end of deque
            q.addLast(i);
        }
        return ans;
    }
}
```

2. [ First Missing Positive](https://leetcode.com/problems/first-missing-positive/)</br>
Solution:
```java
class Solution {
 public int firstMissingPositive(int[] nums) {
         int i = 0;
        while(i < nums.length){
            int correct = nums[i]-1;
            if(nums[i] > 0 && nums[i] <= nums.length && nums[i] != nums[correct]){
                swap(nums, i, correct);
                
            }else{
                i++;
            }
        }
                
        for(int j = 0; j < nums.length; j++){
            if(nums[j] != j+1){
                return j+1;
            }            
        }        
        return nums.length+1;       
    }
    static void swap(int[] arr, int i, int correct) {
        int temp = arr[i];
        arr[i] = arr[correct];
        arr[correct] = temp;
    }
}
```
