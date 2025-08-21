
## Creating an Array
```
import numpy as np
arr = [1,2,3,4,5]
myarr = np.array(arr)
print(myarr)
```

Shape and reshape 
```
myarr.shape

## Multinested array
my_lst1=[1,2,3,4,5]
my_lst2=[2,3,4,5,6]
my_lst3=[9,7,6,8,9]
arr=np.array([my_lst1,my_lst2,my_lst3])

arr.shape # o/p -> (3,5)

arr.reshape(5,3)

# o/p ->
array([[1, 2, 3],
       [4, 5, 2],
       [3, 4, 5],
       [6, 9, 7],
       [6, 8, 9]])
```

## Indexing
`arr[3]`
