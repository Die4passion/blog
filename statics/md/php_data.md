1. 数据类型

   - 数组 array    

   - 链表 linked list

   - 双向链表 doubly linked list

   - 栈 stack

   - 队列 queue

   - 有序队列 priority queue

   - 集合 set

   - map

   - tree

   - graph

   - heap 堆



```php
<?php

# 计算斐波那契数列

# 第一版
$start_time = microtime();
$count = 0;

function fibonacci(int $n): int
{
    global $count;
    $count++;
    if ($n == 0) {
        return 1;
    } else if ($n == 1) {
        return 1;
    } else {
        return fibonacci($n - 1) + fibonacci($n - 2);
    }
}

echo fibonacci(30) . "\n";

# 因为每次需要重新计算，所以内存开销太大

# 第二版

$start_time = microtime();
$fib_cache = [];
$count = 0;

function fibonacciMemoized(int $n): int
{
    global $fib_cache;
    global $count;
    $count++;
    if ($n == 0 || $n == 1) {
        return 1;
    } else {
        if (isset($fib_cache[$n - 1])) {
            $tmp = $fib_cache[$n - 1];
        } else {
            $tmp = $fibonacciMemoized($n - 1);
            $fib_cache[$n - 1] = $tmp;
       }
       
        if (isset($fib_cache[$n - 2])) {
            $tmp1 = $fib_cache[$n - 2];
        } else {
            $tmp1 = $fibnacciMemorized($n - 2);
            $fib_cache[$n - 2] = $tmp1;
        }

        return $tmp + $tmp1;
    }
}

```



```php
function strFindAll(string $pattern, string $txt): array
{
    $M = strlen($pattern);
    $N = strlen($txt);
    $posstions = [];
    for ($i = 0; $i <= $N - $M; $i++) {
        for ($j = 0; $j < $M; $j++) {
            if ($txt[$i + $j] != $pattern[$j])
            break;
        }
        if ($j == $M)
        $positions[] = $i;
    }
    return $positions;
}

# KMP 算法 (此外还有时间复杂度更低的boyer-moore算法)

function ComputeLPS(string $pattern, array &$lps)
{
    $len = 0;  
    $i = 1;    
    $M = strlen($pattern); 
    
    $lps[0] = 0;  
    
    while ($i < $M) {
        if ($pattern[$i] == $pattern[$len]) {
            $len++;
            $lps[$i] = $len;
            $i++;
        } else {
            if ($len != 0) {
                $len = $lps[$len - 1];
            } else {
                $lps[$i] = 0;
                $i++;
            }
        }
    }
}


function KMPStringMatching(string $str, string $pattern): array
{
    $matched = [];
    $M = strlen($pattern);
    $N = strlen($str);
    $i = $j = 0;
    $lps = [];
    
    ComputeLPS($pattern, $lps);
    
     while ($i < $N) {
         if ($pattern[$j] == $str[$i]) {
             $j++;
             $i++;
         }
         
         if ($j == $M) {
             array_push($matches, $i - $j);
             $j = $lps [$j - 1];
         } else if ($i < $N && $pattern[$j] != $str[$i]) {
             if ($j != 0)
             $j = $lps[$j - 1];
             else
             $i = $i + 1;
         }
     }
     return $matches;
}
```



> 贪婪算法



```php

```








































































