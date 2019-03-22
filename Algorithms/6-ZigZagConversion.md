6. ZigZag Conversion

The string "PAYPALISHIRING" is written in a zigzag pattern on a given number of rows like this: (you may want to display this pattern in a fixed font for better legibility)

P   A   H   N
A P L S I I G
Y   I   R

And then read line by line: "PAHNAPLSIIGYIR"

Write the code that will take a string and make this conversion given a number of rows:

string convert(string s, int numRows);

##Example 1:

Input: s = "PAYPALISHIRING", numRows = 3
Output: "PAHNAPLSIIGYIR"

##Example 2:

Input: s = "PAYPALISHIRING", numRows = 4
Output: "PINALSIGYAHRPI"
Explanation:

P     I    N
A   L S  I G
Y A   H R
P     I

```go
class Solution {
public:
    string convert(string s, int numRows) 
    {
        if (s.size()<=numRows || numRows==1) return s;
        int luck=numRows+(numRows-2);
        int index,step=0,j=0,i=0,size=s.size(),g=s.size()/luck;
        char dest [size+1];
        for (;index<size;index++) dest[index]='\0';
        for (index=0;index<numRows;index++)
        {
            if (index==(numRows-1)) step=luck;
            else step=luck-(2*index);
            for (int gi=0;gi<=g;gi++)
            {
                i=index;
                int fl=2;
                while(fl--)
                {
                    if (i>=luck) break;
                    int finger=(gi*luck)+i; 
                    if (finger<size){
                        dest[j++]=s[finger];
                        i+=step;
                    }else
                        break;
                }
            }
        }
        dest[j]='\0';
        return string(dest);
    }
};

```
