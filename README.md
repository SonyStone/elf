<p align="center">
 <img width="20%" height="20%" src="elf.png">
</p>

# Elf

> A Reactive Store with Magical Powers

Elf is a reactive immutable state management solution built on top of RxJS. It uses custom RxJS operators to query the state and pure functions to update it.

Elf encourages simplicity. It saves you the hassle of creating boilerplate code and offers powerful tools with a moderate learning curve, suitable for experienced and inexperienced developers alike.

✅ &nbsp;Modular by design  
✅ &nbsp;Tree Shakeable & Fully Typed  
✅ &nbsp;CLI  
✅ &nbsp;First Class Entities Support  
✅ &nbsp;Requests Status & Cache  
✅ &nbsp;Persist State  
✅ &nbsp;State History  
✅ &nbsp;Pagination  
✅ &nbsp;Devtools


<hr />

<p align="center">

[![@ngneat/elf](https://github.com/ngneat/elf/actions/workflows/ci.yml/badge.svg)](https://github.com/ngneat/elf/actions/workflows/ci.yml)
[![commitizen](https://img.shields.io/badge/commitizen-friendly-brightgreen.svg?style=flat-square)]()
[![PRs](https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=flat-square)]()
[![coc-badge](https://img.shields.io/badge/codeof-conduct-ff69b4.svg?style=flat-square)]()
[![semantic-release](https://img.shields.io/badge/%20%20%F0%9F%93%A6%F0%9F%9A%80-semantic--release-e5079.svg?style=flat-square)](https://github.com/semantic-release/semantic-release)
[![styled with prettier](https://img.shields.io/badge/styled_with-prettier-ff69b4.svg?style=flat-square)](https://github.com/prettier/prettier)
</p>

## 🤓 Learn about it on the [docs site](https://ngneat.github.io/elf/)
## 👩‍🎓 Check out the React Todos [example](https://stackblitz.com/edit/react-ts-jidhej?file=todos/todos.tsx)
## 😋 Check out the Angular Todos [example](https://stackblitz.com/edit/angular-ivy-sky1gb?file=src/app/todos/state/todos.repository.ts) or Books [example](https://stackblitz.com/edit/angular-ivy-j9azue?file=src/app/state/books.repository.ts)

<br >

```ts
import { Store, createState, withProps, select } from '@ngneat/elf';
import { withEntities, selectAll, setEntities } from '@ngneat/elf-entities';

interface TodosProps {
  filter: 'ALL' | 'ACTIVE' | 'COMPLETED';
}

interface Todo {
  id: string;
  title: string;
  status: string;
}

const { state, config } = createState(
  withProps<TodosProps>({ filter: 'ALL' }),
  withEntities<Todo>()
);

const store = new Store({ name: 'todos', state, config });

export const filter$ = store.pipe(select(({ filter }) => filter));
export const todos$ = store.pipe(selectAll());

export function setTodos(todos: Todo[]) {
  store.update(setEntities(todos));
}

export function updateFilter(filter: TodosProps['filter']) {
  store.update(state => ({
    ...state,
    filter
  }));
}
```
