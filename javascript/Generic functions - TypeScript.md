
```ts
export function genericSearch<T>(
object: T,
properties: Array<keyof T>,
query: string,
shouldBeCaseSensitive = false
) {
	if (query === "") {
		return true;
	}

	return properties.some((property) => {
		const value = object[property];
		if (typeof value === "string" || typeof value === "number") {
			if (shouldBeCaseSensitive) {
				return value.toString().includes(query);
			}
		return value.toString().toLowerCase().includes(query.toLowerCase());
		}
		return false;
	});
}
```

```ts
export function genericSort<T>(
a: T,
b: T,
propertyType: { property: keyof T; isDescending: boolean }
) {
	const { property, isDescending } = propertyType;
	const result = (): number => {
		if (a[property] > b[property]) {
			return 1;
		}

		if (a[property] < b[property]) {
			return -1;
		}
	
		return 0;
		};
	return isDescending ? result() * -1 : result();
}
```

