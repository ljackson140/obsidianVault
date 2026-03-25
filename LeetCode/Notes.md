- Strings:
	- When working with strings that have to be reversed or xyz, might be better to convert to another type i.e str.ToCharArray() which then allows you loop over and swap values using the 2 pointer method. 
	- - **Right-hand side** `(arr[right], arr[left])` creates a temporary tuple holding the _current_ values at those indices.
	- **Left-hand side** `(arr[left], arr[right])` then assigns those temporary values back in order.
	- Net effect: the values at `left` and `right` are **swapped**.
```
	if (string.IsNullOrEmpty(str)) return str;

      char[] arr = str.ToCharArray();
      int left = 0, right = arr.Length - 1;

      while (left < right)
      {
          (arr[left], arr[right]) = (arr[right], arr[left]);
          left++;
          right--;
      }

      return new string(arr);
      
    //Using Dictionary to calculate
	var dict = new Dictionary<int, char>
    {
        { 90, 'A' },
        { 80, 'B' },
        { 70, 'C' },
        { 60, 'D' },
        { 0, 'F' },
    };
    
    return dict.First(e => grades.Average() >= e.Key).Value;
```


var containNums = new HashSet<int>();
- Contains()
- Add()
- Remove()
- UnionWith
- IntersectWith
- ExceptWith
- SetEquals

var list = new List<int> { 3, 1, 2 };
- list.Add(4);
- list.AddRange(new[] { 5, 6 });
- list.Sort();          
- bool has2 = list.Contains(2);
- list.Remove(3);
- list.RemoveAt(0);       
- int idx = list.IndexOf(4);
- list.Reverse();

Convert from string to array (char array for manipulation)
` char[] myArr = str.ToCharArray() `



Convert number to array (char array for manipulation)
‘char[] myArr = num.ToString().ToCharArray()’


