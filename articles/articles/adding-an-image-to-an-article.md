<!-- Filename: Adding_an_image_to_an_article / Display title: Как добавить изображение в материал -->

## Introduction

How best to add images to an article depends on which version of Joomla
and which editor are in use. This article has illustrations for Joomla
4, with notes on differences in Joomla 3, and TinyMCE the Joomla default
editor. To get started, open an article for editing:

- **Select** **Content **→** Articles** in the Administrator menu.
- **Select** the title of the article you wish to edit

After inserting the article text, place the cursor at the location where
the image should appear.

## Adding a local image

If the image is located in the images folder of your Joomla installation
you should insert the image using the **CMS Content **→** Media** button
In the TinyMCE edit toolbar (In Joomla 3: Select the Image button):

<img
src="https://docs.joomla.org/images/5/5e/Adding-an-image-to-an-article-cms-content-media.png"
decoding="async" data-file-width="1000" data-file-height="508"
width="1000" height="508" alt="Adding an image" />

In the popup window, navigate to the image you want to use and click to
select it. On selection a form will appear prompting for additional
data. In Joomla 4 the form is to the left. In joomla 3 the form is at
the bottom (scroll down):

<img
src="https://docs.joomla.org/images/d/d4/Adding-an-image-to-an-article-selected-image.png"
decoding="async" data-file-width="1000" data-file-height="508"
width="1000" height="508" alt="Selecting an image" />

1.  Установите как Вам необходимо данные изображения:
1.  - **Описание изображения**: этот \[текст\] становится аттрибутом
      **alt** данного изображения, - важный аттрибут для соблюдения
      веб-стандартов и доступности \[сайта посетителям с ограниченными
      физическими способностями\].

- **Image Class**: If an image is used without a caption some custom
  classes may be applied here. For example, in Joomla 4, **float-end
  ms-2 mb-1** will align the image to the right and float text around it
  with margins to the left and below to prevent text touching the image.
  In Joomla 3 the equivalent style is **pull-right**.
- **Figure Class**: If a caption is set then an alignment class, if any,
  should be applied to the Figure. It is a html tag that encloses the
  img tag. Note that in Cassiopeia margins are applied by the template
  style sheet.

1.  - **Заголовок**: включает подпись, которая отображается под данным
      изображением.

**In Joomla 3**

1.  - **Выравнивание**: настраивает выравнивание данного изображения
      \[слева, справа или по центру\]. Если оставить этот параметр
      \[настроенным по умолчанию\], то аттрибут выравнивания примет
      значение *Не определено*.
1.  - **CSS класс заголовка**: применяет к элементу *figcaption* стиль
      введенного класса.
1.  Для вставки изображения щелкните по кнопке *Вставить*. Экран вставки
    изображения закроется и изображение появится в редакторе. Если Вы
    желаете закрыть экран вставки изображения, то щелкните на кнопку
    *Отменить*.

**Tip:** select the Toggle Editor button to see the applied Image and
Caption styles.

### Using Drag and Drop for Local images

In both Joomla 4 and Joomla 3 you can drag an image from the desktop or
a file browser directly into the article text and the image will be
uploaded to the media folder and placed in the article. The only snag is
that all such uploaded images will be placed in the same media folder.
The location of the Images Directory used for upload and whether this
feature is enabled (On by default) are set in the TinyMCE configuration
Options.

## Adding a remote image

If the image you wish to use is not in the images folder of your Joomla
installation a slightly different procedure is needed.

- **Select** **Insert **→** Image** from the TinyMCE toolbar to open a
  dialog box. In Jooml 3, use the Image icon and the same dialog as used
  for local images.
- **Insert** the image url in the Source field.
- **Fill out** the other fields as required.
- **Advanced** provides some formatting options applied as in-line
  styles. Experiment with 1rem, 2, groove. (This feature is incomplete)

<img
src="https://docs.joomla.org/images/3/39/Adding-an-image-to-an-article-insert-edit-image.png"
class="thumbborder" decoding="async" data-file-width="480"
data-file-height="477" width="480" height="477"
alt="Data for a remote image" />

### Using Drag and Drop for Remote images

You can drag and drop an image from a remote web site directly into your
article text. But be aware that this may also copy the image container
html with class statements not valid for your site.

## Загрузка изображений с помощью экрана вставки изображений

С помощью экрана вставки изображений Вы также можете загружать \[в свою
систему Joomla!\] новые изображения.

- First open the Media browser and navigate to the folder where you wish
  to store new images for the current article.

1.  Для того чтобы открыть обозреватель файлов, щелкните на кнопку
    *Загрузить файл*.
1.  Выберите файлы изображений, которые Вы желаете загрузить. В
    обозревателе файлов щелкните на кнопку *Открыть*, чтобы подтвердить
    свой выбор. Примечание: стиль и расположение элементов \[Вашего\]
    обозревателя файлов зависит от \[Ваших\] браузера и операционной
    системы.
1.  Выбранный файл(ы) появится в списке файлов внизу экрана вставки
    изображения. Для начала загрузки файлов щелкните на кнопку
    "Загрузить".
1.  - Как только загрузка закончена, рядом с файлом появится зеленая
      галочка.
1.  Теперь Вы можете выбирать и вставлять загруженные изображения как
    раньше.
