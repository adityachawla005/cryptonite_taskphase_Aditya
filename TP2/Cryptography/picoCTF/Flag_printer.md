# Flag_printer

**Flag:** ``

Approach

- step 1<br>

We were given the following code:
```
import galois
import numpy as np
MOD = 7514777789

points = []

for line in open('encoded.txt', 'r').read().strip().split('\n'):
    x, y = line.split(' ')
    points.append((int(x), int(y)))

GF = galois.GF(MOD)

matrix = []
solution = []
for point in points:
    x, y = point
    solution.append(GF(y % MOD))

    row = []
    for i in range(len(points)):
        row.append(GF((x ** i) % MOD))
    
    matrix.append(GF(row))

open('output.bmp', 'wb').write(bytearray(np.linalg.solve(GF(matrix), GF(solution)).tolist()[:-1]))

```

- step 2<br>




What you learned through solving this challenge:
<br>
- Galois Fields,Vandermonde Matrix and divide and conquer recursive algorithm approach.


Other incorrect methods you tried:
<br>
- Using sage to solve large interpolation.


References
<br>
- [Modern Computer Algebra](http://lib.ysu.am/open_books/416283.pdf)
- [Galois Fields](https://www.youtube.com/watch?app=desktop&v=c6FlpordfDk)
