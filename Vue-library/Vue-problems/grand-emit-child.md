# 父子孙双向绑定数据

```
// parent
<child :name.sync="xxx" />

// child
<component v-model="selfName" />
prop: {
	name: {
		type: String,
		default: 'test'
	}
}

computed: {
	selfName: {
		get() {
			return this.name;
		},
		set(newValue) {
			this.$emit('update:name', newValue);
		}
	}
}
```

