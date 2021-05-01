# hyrule_jobs

## Why use TypeScript 
- Type errors are caught at compile time
- Richer Editor Support (autocompletion)
- Easier to read & understand the code
- Better developer experience (debugging)
---

## TypeScript Vue Components
### Option API
Examples
- Type argument: `changeName(name: string) {}`, `changeName(age: number | string) {}`
- Type assertion: `age: 25 as number | string` 
---

## Composition API & TypeScript
### Working with reactive
Examples
- Type reactive
```
import { toRefs, reactive } from 'vue
setup() {
const state = reactive({
  name: 'Link',
  age: 25 as string | number
})
return { ...toRefs(State) }
}
```

- Type ref
```
const age = ref<number | string>(25)

age.value = 25, age.value = '25'
```

Create a Custom Job types
- create a type folder under src
- define Job type
```
interface Job {
  title: string,
  location: string,
  salary: number,
  id: string
}
export default Job
```

Use Job Type inside component
- import Job type
- apply Job inside ref
```
const jobs = ref<Job[]>([
  { title: '', location: '', salary: xxx, id: xx },
  { title: '', location: '', salary: xxx, id: xx },
  { title: '', location: '', salary: xxx, id: xx }
])
```
---

## Types & Props
### Type props
Examples
- `import { PropType } from 'vue'`
```
props: {
  jobs: {
    required: true,
    type: Array as PropType<Job[]>
  }
}
```
---

## Functions
### Type functions
create a new type for function argument

Example
- create a OrderTerm.ts under types folder
```
type OrderTerm = 'location' | 'title' | 'salary'

export default OrderTerm
```

import OrderTerm and apply it inside function argument
```
const handleClick = (term: OrderTerm) => {}
```

## Computed Values
Example - orderedJobs
- create a orderedJobs computed
```
setup(props) {
const orderedJobs = computed(() => {
  return [props.jobs].sort((a: Job, b: Job) => {
    return a[props.order] > b[props.order] > 1 : -1
  })
})
return { orderedJobs }
}
```
---

## Hylia Font & Final Styles
- download Hylia Font zip file, uncompress it and copy `.otf` file inside assets folder
- register Hylia Font in `global.css`
```
@font-face {
  font-family: HyliaSerif;
  src: url("HyliaSerifBeta-Regular.otf") format("opentype");
}
```
- wrap `<li>` with `＜transtion-group>`, notice `.move` is the built-in vue animation propery
```
<transition-group name="list" tag="li">
...
</transition-group>

<style scope>
.list-move {
  transition: all 1s;
}
</style>

```












