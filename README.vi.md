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

Đặt tên cho mọi thứ thật khó. Trang này cố gắng làm cho nó dễ dàng hơn.

Although these suggestions can be applied to any programming language, I will use JavaScript to illustrate them in practice.

Mặc dù những gợi ý này có thể được áp dụng cho bất kỳ ngôn ngữ lập trình nào, tôi sẽ sử dụng JavaScript để minh họa chúng trong thực tế.

## English language

Use English language when naming your variables and functions.

Sử dụng ngôn ngữ tiếng Anh khi đặt tên cho các biến và hàm của bạn.

```js
/* Bad */
const primerNombre = 'Gustavo'
const amigos = ['Kate', 'John']

/* Good */
const firstName = 'Gustavo'
const friends = ['Kate', 'John']
```

> Like it or not, English is the dominant language in programming: the syntax of all programming languages is written in English, as well as countless documentations and educational materials. By writing your code in English you dramatically increase its cohesiveness.

> Dù muốn hay không, tiếng Anh là ngôn ngữ chính trong lập trình: cú pháp của tất cả các ngôn ngữ lập trình đều được viết bằng tiếng Anh, cũng như vô số tài liệu và tài liệu học tập. Bằng cách viết code của bạn bằng tiếng Anh, bạn tăng đáng kể tính liên kết của nó.

## Naming convention

Pick **one** naming convention and follow it. It may be `camelCase`, `PascalCase`, `snake_case`, or anything else, as long as it remains consistent. Many programming languages have their own traditions regarding naming conventions; check the documentation for your language or study some popular repositories on Github!

Chọn **một** quy ước đặt tên và làm theo nó. Nó có thể là `camelCase`,` PascalCase`, `solid_case` hoặc bất cứ thứ gì khác, miễn là nó vẫn nhất quán. Nhiều ngôn ngữ lập trình có truyền thống riêng về quy ước đặt tên; kiểm tra tài liệu về ngôn ngữ của bạn hoặc nghiên cứu một số repository phổ biến trên Github!

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

Một cái tên phải _ngắn gọn_, _trực quan_, _mang tính mô tả_:

- **Ngắn gọn**. Tên phải không mất thời gian khi viết và do đó, hãy nhớ;

- **Trực quan**. Tên phải đọc một cách tự nhiên, càng gần với lời nói phổ thông càng tốt.

- **Môt tả**. Tên phải phản ánh những gì nó làm / sở hữu theo cách hiệu quả nhất.

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

**Không** sử dụng viết tắt. Chúng không đóng góp gì nhưng giảm tính đọc hiểu của code. Tìm một cái tên ngắn gọn, mang tính mô tả có thể khó, nhưng sự co lại không phải là cái cớ để không làm như vậy.

```js
/* Bad */
const onItmClk = () => {}

/* Good */
const onItemClick = () => {}
```

## Avoid context duplication

A name should not duplicate the context in which it is defined. Always remove the context from a name if that doesn't decrease its readability.

Tên không được trùng lặp với ngữ cảnh mà nó được xác định. Luôn xóa ngữ cảnh khỏi tên nếu điều đó không làm giảm khả năng đọc hiểu của nó.

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

Tên phải phản ánh kết quả mong đợi.

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

Có một mô hình hữu ích cần tuân theo khi đặt tên cho các hàm:

```
prefix? + action (A) + high context (HC) + low context? (LC)
```

Take a look at how this pattern may be applied in the table below.

Hãy xem cách mô hình này có thể được áp dụng trong bảng dưới đây.

| Name                   | Prefix   | Action (A) | High context (HC) | Low context (LC) |
| ---------------------- | -------- | ---------- | ----------------- | ---------------- |
| `getUser`              |          | `get`      | `User`            |                  |
| `getUserMessages`      |          | `get`      | `User`            | `Messages`       |
| `handleClickOutside`   |          | `handle`   | `Click`           | `Outside`        |
| `shouldDisplayMessage` | `should` | `Display`  | `Message`         |                  |

> **Note:** The order of context affects the meaning of a variable. For example, `shouldUpdateComponent` means _you_ are about to update a component, while `shouldComponentUpdate` tells you that _component_ will update on itself, and you are but controlling when it should be updated.
> In other words, **high context emphasizes the meaning of a variable**.

> **Lưu ý:** Thứ tự của ngữ cảnh ảnh hưởng đến ý nghĩa của một biến. Ví dụ: `shouldUpdateComponent` có nghĩa là _bạn_ sắp cập nhật một component, trong khi `shouldComponentUpdate` cho bạn biết rằng _component_ sẽ tự cập nhật và bạn đang kiểm soát khi nào nó nên được cập nhật.
> Nói cách khác, **hight context nhấn mạnh ý nghĩa của một biến**.

---

## Actions

The verb part of your function name. The most important part responsible for describing what the function _does_.

Phần động từ của tên hàm của bạn. Phần quan trọng nhất chịu trách nhiệm mô tả hàm _làm_ cái gì.

### `get`

Accesses data immediately (i.e. shorthand getter of internal data).

Truy cập dữ liệu ngay lập tức (tức là bộ lấy dữ liệu nội bộ viết tắt).

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

Gắn một biến trở lại với giá trị hoặc trạng thái ban đầu của nó.

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

Yêu cầu một số dữ liệu, mất một thời gian không xác định (tức là yêu cầu không đồng bộ).

```js
function fetchPosts(postCount) {
  return fetch('https://api.dev/posts', {...})
}
```

### `remove`

Removes something _from_ somewhere.

Loại bỏ một cái gì đó _từ_ một nơi nào đó.

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

Hoàn toàn xóa một cái gì đó khỏi các lĩnh vực tồn tại.

Imagine you are a content editor, and there is that notorious post you wish to get rid of. Once you clicked a shiny "Delete post" button, the CMS performed a `deletePost` action, **not** `removePost`.

Hãy tưởng tượng bạn là một biên tập nội dung và có một bài đăng khét tiếng mà bạn muốn loại bỏ. Sau khi bạn nhấp vào nút "Xóa bài đăng" sáng bóng, CMS thực hiện hành động `deletePost`, **không phải** ` removePost`.

```js
function deletePost(id) {
  return database.find({ id }).delete()
}
```

> See also [remove](#remove).

> Xeme thêm [remove](#remove).

### `compose`

Creates new data from the existing one. Mostly applicable to strings, objects, or functions.

Tạo dữ liệu mới từ dữ liệu hiện có. Hầu hết áp dụng cho chuỗi, đối tượng hoặc hàm.

```js
function composePageUrl(pageName, pageId) {
  return (pageName.toLowerCase() + '-' + pageId)
}
```

> See also [get](#get).

> Xem thêm [get](#get).

### `handle`

Handles an action. Often used when naming a callback method.

Xử lý một hành động. Thường được sử dụng khi đặt tên một callback method.

```js
function handleLinkClick() {
  console.log('Clicked a link!')
}

link.addEventListener('click', handleLinkClick)
```

---

## Context

A domain that a function operates on.

Một miền mà một chức năng hoạt động trên đó.

A function is often an action on _something_. It is important to state what its operable domain is, or at least an expected data type.

Một hàm thường là một hành động trên _something_. Điều quan trọng là phải nêu rõ miền có thể hoạt động của nó là gì, hoặc ít nhất là một kiểu dữ liệu mong đợi.

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

> Một số giả định theo ngôn ngữ cụ thể có thể cho phép bỏ qua ngữ cảnh. Ví dụ, trong JavaScript, thông thường `filter` hoạt động trên Array. Việc thêm `filterArray` rõ ràng là không cần thiết.

--

## Prefixes

Prefix enhances the meaning of a variable. It is rarely used in function names.

Tiền tố tăng ý nghĩa của một biến. Nó hiếm khi được sử dụng trong tên hàm.

### `is`

Describes a characteristic or state of the current context (usually `boolean`).

Mô tả một đặc điểm hoặc trạng thái của ngữ cảnh hiện tại (thường là `boolean`).

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

Mô tả liệu ngữ cảnh hiện tại có sở hữu một giá trị hoặc trạng thái nhất định hay không (thường là `boolean`).

```js
/* Bad */
const isProductsExist = productsCount > 0
const areProductsPresent = productsCount > 0

/* Good */
const hasProducts = productsCount > 0
```

### `should`

Reflects a positive conditional statement (usually `boolean`) coupled with a certain action.

Phản ánh một câu điều kiện khẳng định (thường là `boolean`) cùng với một hành động nhất định.

```js
function shouldUpdateUrl(url, expectedUrl) {
  return url !== expectedUrl
}
```

### `min`/`max`

Represents a minimum or maximum value. Used when describing boundaries or limits.

Đại diện cho một giá trị tối thiểu hoặc tối đa. Được sử dụng khi mô tả ranh giới hoặc giới hạn.

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

Cho biết trạng thái trước đó hoặc trạng thái tiếp theo của một biến trong ngữ cảnh hiện tại. Được sử dụng khi mô tả sự chuyển đổi trạng thái.

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

Giống như tiền tố, những tên biến có thể được đặt ở dạng số ít hoặc số nhiều tùy thuộc vào việc chúng chứa một giá trị duy nhất hoặc nhiều giá trị.

```js
/* Bad */
const friends = 'Bob'
const friend = ['Bob', 'Tony', 'Tanya']

/* Good */
const friend = 'Bob'
const friends = ['Bob', 'Tony', 'Tanya']
```
