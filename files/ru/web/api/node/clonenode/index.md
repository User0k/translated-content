---
title: Node.cloneNode()
slug: Web/API/Node/cloneNode
---

{{APIRef("DOM")}}

Метод **`Node.cloneNode()`** возвращает дубликат узла, из которого этот метод был вызван.

## Синтаксис

```
var dupNode = node.cloneNode(deep);
```

- _node_
  - : Узел, который будет клонирован.
- _dupNode_
  - : Новый узел, который будет клоном `node`
- _deep {{optional_inline}}_
  - : `true,` если дети узла должны быть клонированы или `false` для того, чтобы был клонирован только указанный узел.

## Пример

```js
var p = document.getElementById("para1");
var p_prime = p.cloneNode(true);
```

## Примечание

Клонирование узлов копирует все атрибуты и их значения, в том числе собственных (в линию) перехватчиков. Это не копирует перехватчики событий, добавленных используя [`addEventListener()`](/ru/docs/Web/API/EventTarget/addEventListener) или тех что назначены через свойства элемента (т.е `node.onclick = fn`).

Дубликат узла, возвращённого `cloneNode()` не является частью документа, пока не будет добавлен в другой узел, который является частью документа, используя {{domxref("Node.appendChild()")}} или другой метод. Кроме того, не имеет родителя, пока не будет добавлен к другому узлу.

`Если deep` установлен как `false`, дочерние узлы не клонируются. Любой текст, который содержит узел также не клонируется, как и содержащийся в одном или более дочернем узле {{domxref("Text")}}.

Если `deep` установлено как `true`, все поддеревья (включая текст, который может быть потомком узла {{domxref("Text")}}) копируется тоже. Для пустых узлов (т.е {{HTMLElement("img")}} и {{HTMLElement("input")}} элементов) это не имеет значения установлен ли `deep` как `true` или `false`.

> **Предупреждение:** **Внимание:** `cloneNode()` может привести к дублированию идентификаторов элементов в документе.

Если исходный узел имеет идентификатор и клон размещён в том же документе, идентификатор должен быть изменён, для того что бы быть уникальным. Имя атрибута также может нуждаться в изменении, в зависимости от будущего имени дубликата.

Чтобы клонировать узел для добавления к другому документу используйте {{domxref("Document.importNode()")}} вместо этого.

## Спецификации

{{Specifications}}

## Совместимость с браузерами

{{Compat}}
