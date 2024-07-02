#### question: 两个有序数组合并成一个数组，怎么实现？时间复杂度是？

#### answer:

```
function merge(arr, arr1) {
	if (!Array.isArray(arr) || !Array.isArray(arr1)) {
		return []
	}
	if (arr.length === 0) {
		return arr1
	}
	if (arr1.length === 0) {
		return arr
	}
	let firstIndex = 0
	let secondIndex = 0
	const data = []
	for (let i = 0; i < arr.length + arr1.length; i++) {
		if (arr[firstIndex] > arr1[secondIndex]) {
			data.push(arr1[secondIndex])
			secondIndex += 1
		} else if (arr[firstIndex] < arr1[secondIndex]) {
			data.push(arr[firstIndex])
			firstIndex += 1
		} else if (arr[firstIndex] === arr1[secondIndex]) {
			data.push(arr[firstIndex])
			data.push(arr1[secondIndex])
			secondIndex += 1
			firstIndex += 1	
		}
		if (secondIndex === arr1.length && firstIndex < arr.length) {
			data.push(...arr.slice(firstIndex))
			break
		}
		if (firstIndex === arr.length && secondIndex < arr1.length) {
			data.push(...arr1.slice(secondIndex))
			break
		}
		if (firstIndex === arr.length && secondIndex === arr1.length) {
			break
		}
	}
	return data
}

时间复杂度： O(n+m)
```