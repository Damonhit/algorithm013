# 学习笔记

## 排序

### 归并排序

```java
public static void mergeSort(int[] nums, int left, int right) {
    if (left >= right) return;
    int mid = left + (right - left) / 2;
    mergeSort(nums, left, mid);
    mergeSort(nums, mid + 1, right);
    merge(nums, left, mid, right);
}

private static void merge(int[] nums, int left, int mid, int right) {
    int[] temp = new int[right - left + 1];
    int i = left;
    int j = mid + 1;
    int k = 0;
    while (i <= mid && j <= right) {
        temp[k++] = nums[i] < nums[j] ? nums[i++] : nums[j++];
    }
    while (i <= mid) temp[k++] = nums[i++];
    while (j <= right) temp[k++] = nums[j++];
    for (int p = 0; p < temp.length; p++) {
        nums[left + p] = temp[p];
    }
}
```

### 快速排序

```java
public static void quickSort(int[] nums, int left, int right) {
        if (left >= right) return;
        int k = partition(nums, left, right);
        quickSort(nums, left, k - 1);
        quickSort(nums, k + 1, right);
    }

private static int partition(int[] nums, int left, int right) {
    int val = nums[left];
    int i = left;
    int j = right + 1;
    while (true) {
        while (i < right && nums[++i] < val) ;
        while (j > left && nums[--j] > val) ;
        if (i >= j) break;
        int temp = nums[i];
        nums[i] = nums[j];
        nums[j] = temp;
    }
    nums[left] = nums[j];
    nums[j] = val;
    return j;
}
```