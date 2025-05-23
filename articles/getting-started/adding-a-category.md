<!-- Filename: J4.x:Getting_Started:_Adding_a_Category / Display title: Добавление категории -->

## Введение

Владельцы веб-сайтов с более чем несколькими статьями должны подумать о том, как лучше всего представить контент для удобства навигации. Например, если у вас есть зоопарк, музей, коллекция минералов или просто большой сад, у вас может быть около 1000 экземпляров для описания. Одна статья для каждого экземпляра, с фотографиями, нуждается в структурной организации. Если бы статьи были файлами, вы бы, вероятно, разместили их в иерархии файлов. В системе управления контентом (CMS) статьи не являются файлами, но категории обеспечивают подобную древовидную структуру. Пример:

| Категория  | Подкатегории                             |
|------------|------------------------------------------|
| Млекопитающие | Обезьяны, Приматы, Парнокопытные, Собаки, Кошки |
| Рептилии   | Змеи, Ящерицы, Крокодилы, Черепахи       |
| Амфибии    | Лягушки, Жабы                            |
| Птицы      | Хищники, Утки, Чайки, Вьюрки, Синицы     |
| Членистоногие | Пауки, Бабочки, Пчелы, Саранча         |
| Рыбы       | Акулы, Лосось, Треска, Сельдь, Скумбрия  |

Подкатегории могут иметь также дополнительные подкатегории. Максимальная управляемая глубина, кажется, составляет около семи. Для таблицы выше, музей может добавить больше родительских категорий:

```text
природа -> жизнь -> животные -> млекопитающие...
природа -> жизнь -> растения -> деревья...
природа -> минералы...
история -> египет...
наука -> астрономия...
наука -> химия...
```

Представьте, сколько экземпляров хранит национальный или небольшой городской музей!

## Типы элементов меню

Существуют несколько типов элементов меню, предназначенных для работы с категориями:

- **Блог категории** Это макет страницы, который содержит один или два ведущих
  обзора статей, часто на всю ширину страницы, затем несколько обзорных статей в
  двух или трех колонках, и, наконец, механизм пагинации для перехода к
  другим статьям в той же категории. Обзор - это содержимое перед
  разрывом страницы, часто это первые один или два абзаца. Домашняя страница сайта 
  часто является блогом категории, который включает *Все категории*. Макет *Избранные статьи* 
  похож на блог категории и часто также используется в качестве домашней страницы.
- **Список категорий** Это макет списка, который отображает список
  статей в категории. Он может быть отображен с фильтром поиска, что позволяет
  искать статьи по названию, автору, количеству просмотров, меткам или месяцу публикации.
- **Список всех категорий в дереве категорий статей** Этот макет отображает 
  дерево категорий, начиная с выбранного родителя. Каждая ветвь может сворачиваться, 
  что особенно полезно для больших, сложных структур деревьев категорий.

Элементы меню рассматриваются в следующей статье. 

## Создание категории

Следующий пример использует категорию «Млекопитающие», вдохновленную приведенным выше списком, чтобы продемонстрировать, как создать новую категорию:

![Форма редактирования категории](../../../en/images/getting-started/article-category-edit.png)

- Выберите элемент **Содержимое** в меню администратора, чтобы его развернуть.
- Выберите значок **+** рядом с пунктом меню *Категории*, чтобы открыть форму редактирования категории.
- Форма **Статьи: Новая категория** имеет только одно обязательное поле: *Название*, в данном случае *Млекопитающие*.
- Поле **Описание** является необязательным, но лучше его заполнить, так как оно используется в некоторых списках. Рекомендуемое описание:<br>
  *Млекопитающие — это теплокровные животные, которые рожают живых детенышей.*
- Поле **Родитель** указывает, является ли категория основной (-Без родителя-) или подкатегорией, выбранной из списка категорий.
- **Сохранить и закрыть**, чтобы вернуться на страницу списка **Статьи: Категории**.

Эта категория теперь доступна для использования в статьях.

*Переведено с помощью openai.com*

