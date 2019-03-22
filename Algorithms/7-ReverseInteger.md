Given a 32-bit signed integer, reverse digits of an integer.

Example 1:

Input: 123
Output: 321

Example 2:

Input: -123
Output: -321

Example 3:

Input: 120
Output: 21

Note:
Assume we are dealing with an environment which could only store integers within the 32-bit signed integer range: [−231,  231 − 1]. For the purpose of this problem, assume that your function returns 0 when the reversed integer overflows.

```go
const (                             
    MAX_INT = (1 << 31) - 1         
    MIN_INT = int32(-int64(1 << 31))
)                                   
                                    
func reverse(x int) int {           
    flag := 1                       
    if x < 0 {                      
        flag = -1                   
        x *= flag                   
    } else {                        
        flag = 1                    
    }                               
    xm := fun(x, 1)                 
    if xm > MAX_INT {               
        return 0                    
    }                               
    return flag * xm                
}                                   
                                 
func fun(x, base int) int {         
    if x < 10 {                     
        return x * base             
    }                               
    k, xb, mb := 1, x, base         
    for xb >= 10 {                  
        k *= 10                     
        xb = x / k                  
    }                               
    re := x - k*xb                  
    for re < (k/10) && re != 0 {    
        base *= 10                  
        k /= 10                     
    }                               
    return xb*mb + fun(re, base*10) 
}                                   

```
