# lazyjson

JSON parser for golang;

It makes you can use JSON as you do in other Dynamic Programming Languages (like python);

# example
this is an example:
```
	data := `{
		"str_key": "hello",
		"int_key": 2333,
		"float_key": 23.33,
		"bool_key": true,
		"map": {
			"key1": "val1",
			"key2": "val2",
			"arr": [1, 2, 3, 4, 5, 6],
			"map": {
				"key1": "val1",
				"key2": "val2"
			}
		},
		"arr": [
			{
				"key1": "key1"
			},
			{
				"key2": "key2"
			}]
	}`

	j, _ := NewJSON([]byte(data))
	println(j.K("str_key").String(""))
	println(j.K("int_key").Int(0))
	println(j.K("float_key").Float(0))
	println(j.K("bool_key").Bool(false))
	println(j.K("map").K("key1").String(""))
	println(j.K("map").K("arr").I(0).Int(0))
	println(j.K("map").K("map").K("key1").String(""))
	println(j.K("arr").I(0).K("key1").String(""))
	println(j.K("unexisted_key").String("default"))
```

the output is:
```
hello
2333
+2.333000e+001
true
val1
1
val1
key1
default
```

# API
```
type JSON interface {
	K(key string) JSON
	I(index int) JSON
	Int(defaultV int) int
	Float(defaultV float64) float64
	String(defaultV string) string
	Bool(defaultV bool) bool

	json.Marshaler
}
```
