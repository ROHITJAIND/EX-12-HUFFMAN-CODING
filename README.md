# EX-12 Huffman-Coding
### Aim:
To implement Huffman coding to compress the data using Python. &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;**DATE:** 31.11.2023
### Software Required:
1. Anaconda - Python 3.7
### Algorithm:
- Step1: Get the input String. &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;Developed By: ROHIT JAIN D
- Step2: Create tree nodes.&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;Register No: 212222230120
- Step3: Main function to implement huffman coding.
- Step4: Calculate frequency of occurrence.
- Step5: Print the characters and its huffmancode.
### Program:
**Get the input String**
```Python
string = 'ROHIT JAIN D'
class NodeTree(object):
    def __init__(self, left=None, right=None):
        self.left = left
        self.right = right
    def children(self):
        return (self.left,self.right)
```
**Create tree nodes**
```Python
def huffman_tree(node, left=True,binString=''):
    if type(node) is str:
        return {node: binString}
    (l, r) = node.children()
    d = dict()
    d.update(huffman_tree(l, True, binString + '0'))
    d.update(huffman_tree(r, False, binString + '1'))
    return d
```
**Main function to implement huffman coding**
```Python
freq = {}
for c in string:
    if c in freq:
        freq[c] +=1
    else:
        freq[c] = 1
freq = sorted(freq.items(),key=lambda x: x[1], reverse=True)
nodes = freq
```
**Calculate frequency of occurrence**
```Python
while len(nodes) > 1:
    (key1, c1) = nodes[-1]
    (key2, c2) = nodes[-2]
    nodes = nodes[:-2]
    node = NodeTree(key1, key2)
    nodes.append((node, c1 + c2))
    nodes = sorted(nodes, key=lambda x: x[1], reverse=True)
```
**Print the characters and its huffmancode**
```Python
huffmanCode = huffman_tree(nodes[0][0])
print(' Char | Huffman code ')
print('----------------------')
for (char, frequency) in freq:
    print(' %-4r |%12s' % (char, huffmanCode[char]))
```
### Output:
**Print the characters and its huffmancode**
<table border=3>
<tr>
<td> 

 
```
 Char | Huffman code      
----------------------
 'I'  |         101
 ' '  |         100
 'R'  |         001
 'O'  |         000
 'H'  |         011
 'T'  |         010
 'J'  |        1101
 'A'  |        1100
 'N'  |        1111
 'D'  |        1110
```
</td>
</tr>
</table>

### Result:
Thus the huffman coding was implemented to compress the data using python programming.
