## **Turing Test Quiz: Baseball Game using PHP**

<p>You are keeping score for a baseball game with strange rules. The game consists of several rounds. Where the scores of past rounds may affect future round scores.
At the beginning of the game, you start with an empty record. You are given a list of string ops, where ops[i] is the ith operation you must apply to the record and is one of the following:

-  An integer x - Record a new score of x.
- "+" - Record a new score that is the sum of the previous two scores. It is guaranteed there will always be two previous scores.
- "D" - Record a new score that is double the previous score. It is guaranteed there will always be a previous score
- "C" - Invalidate the previous score, removing it from the record. It is guaranteed there will always be a previous score.
Return the sum of all the scores on the record.

**Example 1:**

```php 
Input: ops = ["5","2","C","D","+"]
```

**Output: 30**

**Example 2:**
```php
Input: ops = ["5","-2","4","C","D","9","+","+"]
```
**Output: 27**

```php
TestCase: ["5","2","C","D","+"]
```
</p>


```php
class Solution{
	function calPoints($ops){
		$array = array();
		$score = 0;
		for ($i=0; $i < count($ops); $i++) { 
			$eachrec =  $ops[$i];
			if(is_numeric($eachrec)){
				array_push($array, $eachrec);
			}	
			elseif ($eachrec == "C") {
				array_pop($array);
			}elseif ($eachrec == "D") {
				$last = end($array);
				$mul = 2 * $last;
				array_push($array, $mul);
			}elseif ($eachrec == "+") {
				$last = end($array);
				$sl = $array[count($array)-2]; 
				$res = $last + $sl;
				array_push($array, $res);
			}
		}		
		for ($i=0; $i < count($array) ; $i++) { 
			$score = $score + $array[$i];
		}
		return $score;		
	}
}
$ops = ["5","2","C","D","+"];
$soluton = new Solution();
$output = $soluton->calPoints($ops);
echo $output;
```
