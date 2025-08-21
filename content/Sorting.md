
## Selection Sort
https://www.geeksforgeeks.org/problems/selection-sort/1

Approach: Select the minimum on the right of 'i' and swap.
```
class Solution {
    void selectionSort(int[] arr) {
        int n = arr.length;
        for(int i=0;i<n-1;i++)
        {
            int mini = i;
            for(int j=i;j<n;j++)
            {
                if(arr[j]<arr[mini]) mini = j;
            }
            
            int temp = arr[i];
            arr[i] = arr[mini];
            arr[mini] = temp;
        }
    }
}
```

## Bubble Sort
https://www.geeksforgeeks.org/problems/bubble-sort/1

Approach: Push the maximum till the end by using adjacent swaps.
```
class Solution {
    public void bubbleSort(int[] arr) {
        int n = arr.length;
        for(int i=n-1;i>=0;i--)
        {
            for(int j=0;j<i;j++)
            {
                if(arr[j]>arr[j+1])
                {
                    int temp = arr[j];
                    arr[j] = arr[j+1];
                    arr[j+1] = temp;
                }
            }
        }
    }
}
```

## Insertion Sort
https://www.geeksforgeeks.org/problems/insertion-sort/1

Approach: Take a window of increasing size, for each element on the right of the window, place it inside the window by swapping the elements and inserting it at the right place.
```
class Solution {
    public void insertionSort(int arr[]) {
        int n = arr.length;
        
        for(int i=0;i<n;i++)
        {
            int j=i;
            while(j>0 && arr[j-1]>arr[j])
            {
                int temp = arr[j-1];
                arr[j-1] = arr[j];
                arr[j] = temp;
                j--;
            }
        }
    }
}
```

## Merge Sort
https://leetcode.com/problems/sort-an-array/

```
class Solution {
    public void merge(int[] nums, int low, int high, int mid)
    {
        int left = low;
        int right = mid+1;
        ArrayList<Integer> temp = new ArrayList<>();

        while(left<= mid && right<= high)
        {
            if(nums[left]<nums[right])
            {
                temp.add(nums[left]);
                left++;
            }
            else
            {
                temp.add(nums[right]);
                right++;
            }
        }

        while(left <= mid)
        {
            temp.add(nums[left]);
            left++;
        }

        while(right <= high)
        {
            temp.add(nums[right]);
            right++;
        }

        for(int i=low;i<=high;i++)
        {
            nums[i] = temp.get(i-low);
        }
    }

    public void mergesort(int[] nums, int low, int high)
    {
        if(low >= high) return;
        int mid = (low+high)/2;
        mergesort(nums, low, mid);
        mergesort(nums, mid+1, high);
        merge(nums, low, high, mid);
    }

    public int[] sortArray(int[] nums) {
        mergesort(nums, 0, nums.length-1);
        return nums;
    }
}
```

