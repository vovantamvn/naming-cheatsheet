<p align="center">
  <a href="https://github.com/kettanaito/naming-cheatsheet">
    <img src="./naming-cheatsheet.png" alt="Naming cheatsheet" />
  </a>
</p>

# Naming cheatsheet

- [English language](#english-language)
- [Naming convention](#naming-convention)
- [S-I-D](#s-i-d)
- [Avoid contractions](#avoid-contractions)
- [Avoid context duplication](#avoid-context-duplication)
- [Reflect the expected result](#reflect-the-expected-result)
- [Naming functions](#naming-functions)
  - [A/HC/LC pattern](#ahclc-pattern)
    - [Actions](#actions)
    - [Context](#context)
    - [Prefixes](#prefixes)
- [Singular and Plurals](#singular-and-plurals)

---

Naming things is hard. This sheet attempts to make it easier.

Đặt tên cho sự vật thì khó. Trang này sẽ cố gắp làm cho nó dễ hơn.

Although these suggestions can be applied to any programming language, I will use JavaScript to illustrate them in practice.

Mặc dù những gợi ý này có thể áp dụng cho bất kì ngôn ngữ lập trình nào, Tôi sẽ sử dụng JavaScript để minh họa chúng trong thực hành.

## English language

Use English language when naming your variables and functions.

Sử dụng ngôn ngữ tiếng Anh khi đặt tên các biến và phương thức của bạn.

```js
/* Bad */
const primerNombre = 'Gustavo'
const amigos = ['Kate', 'John']

/* Good */
const firstName = 'Gustavo'
const friends = ['Kate', 'John']
```

> Like it or not, English is the dominant language in programming: the syntax of all programming languages is written in English, as well as countless documentations and educational materials. By writing your code in English you dramatically increase its cohesiveness.

> Thích hay không, tiếng Anh là ngôn ngữ chính trong lập trình: cú pháp của tất cả ngôn ngữ lập trình được viết bằng tiếng Anh, cũng như vô số tài liệu và tài liệu học tập. Viết code của bạn bằng tiếng Anh tăng sự gắn kết của nó đáng kể.

## Naming convention

Pick **one** naming convention and follow it. It may be `camelCase`, `PascalCase`, `snake_case`, or anything else, as long as it remains consistent. Many programming languages have their own traditions regarding naming conventions; check the documentation for your language or study some popular repositories on Github!

Chọn **một** quy tắc đặt tên và làm theo nó. Nó có thể là `camelCase`, `PascalCase`, `snake_case`, hoặc quy tắc nào khác, miễn là nó vẫn thích hợp. Nhiều ngôn ngữ lập trình có truyền thống về quy ước đặt tên của nó; kiểm tra tài liệu cho ngôn ngữ của bạn hoặc học một vài repository nổi tiếng trên Github!

```js
/* Bad */
const page_count = 5
const shouldUpdate = true

/* Good */
const pageCount = 5
const shouldUpdate = true

/* Good as well */
const page_count = 5
const should_update = true
```

## S-I-D

A name must be _short_, _intuitive_ and _descriptive_:

- **Short**. A name must not take long to type and, therefore, remember;
- **Intuitive**. A name must read naturally, as close to the common speech as possible;
- **Descriptive**. A name must reflect what it does/possesses in the most efficient way.

Một cái tên phải _ngắn_, _trực quan_, _mô tả_:

- **Ngắn**. Một cái tên phải không mất thời gian khi viết và do đó, hãy nhớ;

- **Trực quan**. Một cái tên phải đọc một cách tự nhiên, càng gần với lời nói phổ thông càng tốt.

- **Môt tả**. Một cái tên phải phản ánh nó làm gì/sở hữu gì một cách hiệu quả.

```js
/* Bad */
const a = 5 // "a" could mean anything
const isPaginatable = a > 10 // "Paginatable" sounds extremely unnatural
const shouldPaginatize = a > 10 // Made up verbs are so much fun!

/* Good */
const postCount = 5
const hasPagination = postCount > 10
const shouldPaginate = postCount > 10 // alternatively
```

## Avoid contractions

Do **not** use contractions. They contribute to nothing but decreased readability of the code. Finding a short, descriptive name may be hard, but contraction is not an excuse for not doing so.

**Không** sử dụng viết tắt. Chúng không đóng góp gì nhưng giảm tính đọc hiểu của code. Tìm kiếm một từ viết tắt, mô tả tên có thể khó, nhưng sự rút gọn không phải là cái cớ để làm vậy.

```js
/* Bad */
const onItmClk = () => {}

/* Good */
const onItemClick = () => {}
```

## Avoid context duplication

A name should not duplicate the context in which it is defined. Always remove the context from a name if that doesn't decrease its readability.

Một cái tên không nên trùng lặp với bối cảnh trong định nghĩa của nó. Luôn luôn xóa bối cảnh từ một cái tên nếu không làm giảm tính đọc hiểu của nó.

```js
class MenuItem {
  /* Method name duplicates the context (which is "MenuItem") */
  handleMenuItemClick = (event) => { ... }

  /* Reads nicely as `MenuItem.handleClick()` */
  handleClick = (event) => { ... }
}
```

## Reflect the expected result

A name should reflect the expected result.

Một cái tên nên phản ánh kết quả mong đợi.

```jsx
/* Bad */
const isEnabled = itemCount > 3
return <Button disabled={!isEnabled} />

/* Good */
const isDisabled = itemCount <= 3
return <Button disabled={isDisabled} />
```

---

# Naming functions

## A/HC/LC Pattern

There is a useful pattern to follow when naming functions:

Dưới đây là một mẫu hữu ích để khi đặt tên các phương thức:

```
prefix? + action (A) + high context (HC) + low context? (LC)
```

Take a look at how this pattern may be applied in the table below.

Nhìn xem làm thế nào mẫu có thể được áp dụng ở bảng phía dưới.

| Name                   | Prefix   | Action (A) | High context (HC) | Low context (LC) |
| ---------------------- | -------- | ---------- | ----------------- | ---------------- |
| `getUser`              |          | `get`      | `User`            |                  |
| `getUserMessages`      |          | `get`      | `User`            | `Messages`       |
| `handleClickOutside`   |          | `handle`   | `Click`           | `Outside`        |
| `shouldDisplayMessage` | `should` | `Display`  | `Message`         |                  |

> **Note:** The order of context affects the meaning of a variable. For example, `shouldUpdateComponent` means _you_ are about to update a component, while `shouldComponentUpdate` tells you that _component_ will update on itself, and you are but controlling when it should be updated.
> In other words, **high context emphasizes the meaning of a variable**.

> **Chú ý:** Thứ tự của ngữ cảnh ảnh hưởng đến ý nghĩa của một biến. Ví dụ, `shouldUpdateComponent` có ý nghĩa _bạn_ sắp cập nhật một component, trong khi `shouldComponentUpdate` nói bạn rằng _component_ sẽ tự cập nhật bởi chính nó, và bạn đang kiểm soát khi nào nó nên được cập nhật.
> Nói cách khác, **hight context nhấn mạnh ý nghĩa của một biến**

---

## Actions

The verb part of your function name. The most important part responsible for describing what the function _does_.

Động từ là một phần của tên phương thức. Trách nhiệm quan trọng nhất cho mô tả phương thức _làm_ cái gì.

### `get`

Accesses data immediately (i.e. shorthand getter of internal data).

Truy cập dữ liệu ngay lập tức (i.e viết ngắn lấy của dữ liệu nội bộ)

```js
function getFruitCount() {
  return this.fruits.length
}
```

> See also [compose](#compose).

> Xem thêm [compose](#compose).

### `set`

Sets a variable in a declarative way, with value `A` to value `B`.

Gắn một biến trong một cách khai báo, với giá trị `A` đến giá trị `B`.

```js
let fruits = 0

function setFruits(nextFruits) {
  fruits = nextFruits
}

setFruits(5)
console.log(fruits) // 5
```

### `reset`

Sets a variable back to its initial value or state.

Gắn một biến trở lại với giá trị hoặc trạng thái khởi tạo của nó.

```js
const initialFruits = 5
let fruits = initialFruits
setFruits(10)
console.log(fruits) // 10

function resetFruits() {
  fruits = initialFruits
}

resetFruits()
console.log(fruits) // 5
```

### `fetch`

Request for some data, which takes some indeterminate time (i.e. async request).

Request một số dữ liệu, mất một thời gian không xác định (i.e. async request).

```js
function fetchPosts(postCount) {
  return fetch('https://api.dev/posts', {...})
}
```

### `remove`

Removes something _from_ somewhere.

Xóa một cái gì đó _từ_ một nơi nào đó.

For example, if you have a collection of selected filters on a search page, removing one of them from the collection is `removeFilter`, **not** `deleteFilter` (and this is how you would naturally say it in English as well):

Ví dụ, nếu bạn có một danh sách của bộ lọc được chọn trên một trang tìm kiếm, xóa một trong số chúng từ danh sách là `removeFilter`, **không phải** `deleteFilter` (và đây cũng là cách bạn nói nó một cách tự nhiên trong tiếng Anh):

```js
function removeFilter(filterName, filters) {
  return filters.filter((name) => name !== filterName)
}

const selectedFilters = ['price', 'availability', 'size']
removeFilter('price', selectedFilters)
```

> See also [delete](#delete).

> Xem thêm [delete](#delete).

### `delete`

Completely erases something from the realms of existence.

Imagine you are a content editor, and there is that notorious post you wish to get rid of. Once you clicked a shiny "Delete post" button, the CMS performed a `deletePost` action, **not** `removePost`.

```js
function deletePost(id) {
  return database.find({ id }).delete()
}
```

> See also [remove](#remove).

### `compose`

Creates new data from the existing one. Mostly applicable to strings, objects, or functions.

```js
function composePageUrl(pageName, pageId) {
  return (pageName.toLowerCase() + '-' + pageId)
}
```

> See also [get](#get).

### `handle`

Handles an action. Often used when naming a callback method.

```js
function handleLinkClick() {
  console.log('Clicked a link!')
}

link.addEventListener('click', handleLinkClick)
```

---

## Context

A domain that a function operates on.

A function is often an action on _something_. It is important to state what its operable domain is, or at least an expected data type.

```js
/* A pure function operating with primitives */
function filter(list, predicate) {
  return list.filter(predicate)
}

/* Function operating exactly on posts */
function getRecentPosts(posts) {
  return filter(posts, (post) => post.date === Date.now())
}
```

> Some language-specific assumptions may allow omitting the context. For example, in JavaScript, it's common that `filter` operates on Array. Adding explicit `filterArray` would be unnecessary.

--

## Prefixes

Prefix enhances the meaning of a variable. It is rarely used in function names.

### `is`

Describes a characteristic or state of the current context (usually `boolean`).

```js
const color = 'blue'
const isBlue = color === 'blue' // characteristic
const isPresent = true // state

if (isBlue && isPresent) {
  console.log('Blue is present!')
}
```

### `has`

Describes whether the current context possesses a certain value or state (usually `boolean`).

```js
/* Bad */
const isProductsExist = productsCount > 0
const areProductsPresent = productsCount > 0

/* Good */
const hasProducts = productsCount > 0
```

### `should`

Reflects a positive conditional statement (usually `boolean`) coupled with a certain action.

```js
function shouldUpdateUrl(url, expectedUrl) {
  return url !== expectedUrl
}
```

### `min`/`max`

Represents a minimum or maximum value. Used when describing boundaries or limits.

```js
/**
 * Renders a random amount of posts within
 * the given min/max boundaries.
 */
function renderPosts(posts, minPosts, maxPosts) {
  return posts.slice(0, randomBetween(minPosts, maxPosts))
}
```

### `prev`/`next`

Indicate the previous or the next state of a variable in the current context. Used when describing state transitions.

```jsx
function fetchPosts() {
  const prevPosts = this.state.posts

  const fetchedPosts = fetch('...')
  const nextPosts = concat(prevPosts, fetchedPosts)

  this.setState({ posts: nextPosts })
}
```

## Singular and Plurals

Like a prefix, variable names can be made singular or plural depending on whether they hold a single value or multiple values.

```js
/* Bad */
const friends = 'Bob'
const friend = ['Bob', 'Tony', 'Tanya']

/* Good */
const friend = 'Bob'
const friends = ['Bob', 'Tony', 'Tanya']
```
