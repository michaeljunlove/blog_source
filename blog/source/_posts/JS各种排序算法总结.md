clearReading: true
thumbnailImage: http://7xid80.com1.z0.glb.clouddn.com/工大向日葵.jpg
thumbnailImagePosition: right
autoThumbnailImage: yes
metaAlignment: center
coverImage: http://7xid80.com1.z0.glb.clouddn.com/工大向日葵.jpg
coverCaption: "工大的向日葵"
coverMeta: out
coverImage: http://7xid80.com1.z0.glb.clouddn.com/工大向日葵.jpg
comments: false
title: JS各种排序算法总结
date: 2015-03-24 18:38:44
tags: [排序算法]
categories: [数据结构与算法]

---
各种排序算法总结
<!-- more -->
***

* [JS排序算法总结](http://www.jianshu.com/p/1b4068ccd505?hmsr=toutiao.io&utm_medium=toutiao.io&utm_source=toutiao.io)

{% image  center clear  http://7xid80.com1.z0.glb.clouddn.com/%E5%90%84%E7%A7%8D%E6%8E%92%E5%BA%8F%E7%AE%97%E6%B3%95%E6%80%BB%E7%BB%93.png "各类排序算法复杂度" %}

数组的长度:n

# 冒泡排序
白话版描述：对于一个数组，从左到右遍历一遍，遍历的长度为n，在遍历的过程中，比较相邻的2个数，如果前一个数比后一个数大，则交换这2个数。这样一轮比较后，最后一个数一定是最大的。再来一次遍历，遍历的长度为n-1，以此类推，共执行n次遍历。
``` javascript
function bubbleSort(arr) {
    var len = arr.length;
    for (var i = 0; i < len; i++) {
        for (var j = 0; j < len - 1 - i; j++) {
            if (arr[j] > arr[j+1]) {       
                var temp = arr[j+1];       
                arr[j+1] = arr[j];
                arr[j] = temp;
            }
        }
    }
    return arr;
}
```

# 选择排序
白话版描述：对于一个数组，从左到右遍历一遍，每次遍历都以该初始遍历索引对应的值为基准值，在遍历的过程中，去寻找比这个基准值小的最小数，找到以后，交换这个基准值和最小数。一共遍历n次。
``` javascript
function selectionSort(arr) {
    var len = arr.length;
    var minIndex, temp;
    for (var i = 0; i < len - 1; i++) {
        minIndex = i;
        for (var j = i + 1; j < len; j++) {
            if (arr[j] < arr[minIndex]) {     //寻找最小的数
                minIndex = j;                 //将最小数的索引保存
            }
        }
        temp = arr[i];
        arr[i] = arr[minIndex];
        arr[minIndex] = temp;
    }
    return arr;
}
```
# 插入排序
白话版描述：将一个数组分为有序部分和无序部分，从无序部分取出一个数插入到有序部分。有序部分在遍历的过程中，建立起来。
``` javascript
function insertionSort(arr) {
    var len = arr.length;
    var preIndex, current;
    for (var i = 1; i < len; i++) {
        preIndex = i - 1;
        current = arr[i];
        while(preIndex >= 0 && arr[preIndex] > current) {
            arr[preIndex+1] = arr[preIndex];
            preIndex--;
        }
        arr[preIndex+1] = current;
    }
    return arr;
}
```

# 希尔排序

``` javascript
function shellSort(arr) {
    var len = arr.length,
        temp,
        gap = 1;
    while(gap < len/3) {          //动态定义间隔序列
        gap =gap*3+1;
    }
    for (gap; gap > 0; gap = Math.floor(gap/3)) {
        for (var i = gap; i < len; i++) {
            temp = arr[i];
            for (var j = i-gap; j >= 0 && arr[j] > temp; j-=gap) {
                arr[j+gap] = arr[j];
            }
            arr[j+gap] = temp;
        }
    }
    return arr;
}
```
# 归并排序
``` javascript
function mergeSort(arr) {  //采用自上而下的递归方法
    var len = arr.length;
    if(len < 2) {
        return arr;
    }
    var middle = Math.floor(len / 2),
        left = arr.slice(0, middle),
        right = arr.slice(middle);
    return merge(mergeSort(left), mergeSort(right));
}
function merge(left, right)
{
    var result = [];
    while (left.length && right.length) {
        if (left[0] <= right[0]) {
            result.push(left.shift());
        } else {
            result.push(right.shift());
        }
    }

    while (left.length)
        result.push(left.shift());

    while (right.length)
        result.push(right.shift());

    return result;
}
```

# 快速排序

白话版描述：首先在这个序列中随便找一个数作为基准数，指针left从数组左端出发，去寻找比这个基准值大的数,找到后，停下来。指针right从数组右端出发，去寻找比这个基准值小的数，找到后，停下来。将指针left和指针right所指向的数交换。当指针left与指针right相遇后，交换基准值和指针left,right所指向的数。如此往复，快速排序的每一轮处理其实就是将这一轮的基准数归位，直到所有的数都归位为止，排序就结束了。

``` javascript
function quickSort(arr,first,end){
	var left=first;
	var right=end;
	var temp=arr[first];//基准值
	while(left<right){
		 //指针right从右侧开始往左遍历，找比基准值小的数
                 while(left<right&&arr[right]>=temp){right--;}
                 arr[left]=arr[right];
                 //指针left从左侧开始往右遍历，找比基准值大的数
                 while(left<right&&arr[left]<=temp){left++;}
                 arr[right]=arr[left];
	}
	//说明left和right相遇了，交换left所指向的值和基准值
	arr[left]=temp;
	if(first<left-1){quickSort(arr,first,left-1);}
	if(end>left+1){quickSort(arr,left+1,end);}
	return arr;
}
```

# 堆排序
``` javascript

```
