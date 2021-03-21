[![npm](https://img.shields.io/npm/v/react-calendar.svg)](https://www.npmjs.com/package/react-calendar) ![downloads](https://img.shields.io/npm/dt/react-calendar.svg) [![CI](https://github.com/wojtekmaj/react-calendar/workflows/CI/badge.svg)](https://github.com/wojtekmaj/react-calendar/actions) ![dependencies](https://img.shields.io/david/wojtekmaj/react-calendar.svg) ![dev dependencies](https://img.shields.io/david/dev/wojtekmaj/react-calendar.svg) [![tested with jest](https://img.shields.io/badge/tested_with-jest-99424f.svg)](https://github.com/facebook/jest)

# React-Calendar

<div align="center">
  <img width="436" heigth="398" src="https://projects.wojtekmaj.pl/react-calendar/react-calendar.jpg">
</div>

## React应用程序的终极日历

* 选择几天、几个月、几年甚至几十年
* 支持范围选择
* 几乎支持任何语言
* 不需要moment.js

## tl;dr
* Install by executing `npm install react-calendar` or `yarn add react-calendar`.
* Import by adding `import Calendar from 'react-calendar'`.
* Use by adding `<Calendar />`. Use `onChange` prop for getting new values.

## Demo

在sample目录中可以找到一个最小的演示页面。

[Online demo](http://projects.wojtekmaj.pl/react-calendar/) is also available!

## Before you continue

React-Calendar正在不断发展。本文档是为React-Calendar 3编写的。x分支。如果你想查看React-Calendar的其他版本的文档，使用GitHub页面顶部的下拉菜单切换到合适的标签。以下是每个分支最新文档的快速链接:

* [v2.x](https://github.com/wojtekmaj/react-calendar/blob/v2.x/README.md)

## Getting started

### Compatibility

你的项目需要使用React 16.3或更高版本。

React-Calendar使用了现代的web技术。这就是为什么它如此快速，轻巧，易于设计。然而，这是有代价的
[supporting only modern browsers](https://caniuse.com/#feat=internationalization).

#### Legacy browsers

果你需要支持像Internet Explorer 10这样的传统浏览器，你将需要使用[Intl.js](https://github.com/andyearnshaw/Intl.js/)或另一个Intl腻子配合React-Calendar。

### Installation

通过执行将React-Calendar添加到项目中 `npm install react-calendar` or `yarn add react-calendar`.

### Usage

下面是一个基本用法的例子:

```js
import React, { useState } from 'react';
import Calendar from 'react-calendar';

function MyApp() {
  const [value, onChange] = useState(new Date());

  return (
    <div>
      <Calendar
        onChange={onChange}
        value={value}
      />
    </div>
  );
}
```

查看该存储库中的[sample directory](https://github.com/wojtekmaj/react-calendar/tree/master/sample)以获得完整的工作示例。更多示例和更高级的用例，请查看[React-Calendar Wiki](https://github.com/wojtekmaj/react-calendar/wiki)中的[Recipes](https://github.com/wojtekmaj/react-calendar/wiki/Recipes)。

### Custom styling

如果你想使用默认的React-Calendar样式来构建它，你可以通过以下方式导入React-Calendar样式:

```js
import 'react-calendar/dist/Calendar.css';
```

## User guide

### Calendar

显示一个完整的交互式日历。

#### Props

| Prop name               | Description                                                                                                                                                                                                            | Default value                                         | Example values                                                                                                                                                                                                                                                                                       |
|-------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| activeStartDate         | 应显示的时期的开始。如果您希望以不受控制的方式使用React-Calendar，请使用defaultActiveStartDate代替。                                                                                                                   |                                                       |                                                                                                                                                                                                                                                                                                      |
| allowPartialRange       | 是否只调用部分结果的selectRange prop。                                                                                                                                                                                 | `false`                                               | `true`                                                                                                                                                                                                                                                                                               |
| calendarType            | 应该使用的日历类型。可以是“ISO 8601”、“US”、“Arabic”或“Hebrew”。设置为“我们”或“希伯来语”将改变一周的第一天为星期日。设置为“阿拉伯语”将把一周的第一天改为星期六。设置为“阿拉伯语”或“希伯来语”将使周末出现在周五到周六。 | Type of calendar most commonly used in a given locale | `"ISO 8601"`                                                                                                                                                                                                                                                                                         |
| className               | 将与“react-calendar”一起添加到主react-calendar <div>元素的类名。                                                                                                                                                       | n/a                                                   | <ul><li>String: `"class1 class2"`</li><li>Array of strings: `["class1", "class2 class3"]`</li></ul>                                                                                                                                                                                                  |
| defaultActiveStartDate  | 默认情况下应显示的时间段的开始。如果您希望以受控方式使用React-Calendar，请activeStartDate改为使用。                                                                                                                    | (today)                                               | `new Date(2017, 0, 1)`                                                                                                                                                                                                                                                                               |
| defaultValue            | 最初应选择的日历值。可以是一个值或两个值的数组。如果您希望以受控方式使用React-Calendar，请value改为使用。                                                                                                              | n/a                                                   | <ul><li>Date: `new Date()`</li><li>An array of dates: `[new Date(2017, 0, 1), new Date(2017, 7, 1)]`                                                                                                                                                                                                 |
| defaultView             | 确定最初应打开哪个日历视图。不禁用导航。可以"month"，"year"，"decade"或"century"。如果您希望以受控方式使用React-Calendar，请view改为使用。                                                                             | The most detailed view allowed                        | `"year"`                                                                                                                                                                                                                                                                                             |
| formatLongDate          | 调用此函数以覆盖默认日期格格式。可用于使用您自己的格式化功能。                                                                                                                                                         | (default formatter)                                   | `(locale, date) => formatDate(date, 'dd MMM YYYY')`                                                                                                                                                                                                                                                  |
| formatMonth             | 调用该函数以覆盖月份名称的默认格式。可用于使用您自己的格式化功能。                                                                                                                                                     | (default formatter)                                   | `(locale, date) => formatDate(date, 'MMM')`                                                                                                                                                                                                                                                          |
| formatMonthYear         | 调用该函数以覆盖月份和年份的默认格式。可用于使用您自己的格式化功能。                                                                                                                                                   | (default formatter)                                   | `(locale, date) => formatDate(date, 'MMMM YYYY')`                                                                                                                                                                                                                                                    |
| formatShortWeekday      | 调用该函数以覆盖工作日名称的默认格式。可用于使用您自己的格式化功能。                                                                                                                                                   | (default formatter)                                   | `(locale, date) => formatDate(date, 'dd')`                                                                                                                                                                                                                                                           |
| formatYear              | 调用该函数以覆盖顶部导航部分中年份的默认格式。可用于使用您自己的格式化功能。                                                                                                                                           | (default formatter)                                   | `(locale, date) => formatDate(date, 'YYYY')`                                                                                                                                                                                                                                                         |
| inputRef                | 一个行为类似于ref的道具，但已传递给<div>由<Calendar>component渲染的main 。                                                                                                                                             | n/a                                                   | <ul><li>Function:<br />`(ref) => { this.myCalendar = ref; }`</li><li>Ref created using `React.createRef`:<br />`this.ref = React.createRef();`<br />…<br />`inputRef={this.ref}`</li><li>Ref created using `React.useRef`:<br />`const ref = React.useRef();`<br />…<br />`inputRef={ref}`</li></ul> |
| locale                  | 日历应使用的语言环境。 Can be any [IETF language tag](https://en.wikipedia.org/wiki/IETF_language_tag).                                                                                                                | User's browser settings                               | `"hu-HU"`                                                                                                                                                                                                                                                                                            |
| maxDate                 | 用户可以选择的最大日期。maxDate部分重叠的时间段也是可以选择的，尽管React-Calendar可以确保不选择以后的日期。                                                                                                            | n/a                                                   | Date: `new Date()`                                                                                                                                                                                                                                                                                   |
| maxDetail               | 用户应看到的最详细的视图。此处定义的视图也将成为单击该项目将选择日期并将其传递给onChange的视图。可以"month"，"year"，"decade"或"century"。                                                                             | `"month"`                                             | `"year"`                                                                                                                                                                                                                                                                                             |
| minDate                 | 用户可以选择的最短日期。minDate部分重叠的时间段也是可以选择的，尽管React-Calendar会确保没有选择任何较早的日期。                                                                                                        | n/a                                                   | Date: `new Date()`                                                                                                                                                                                                                                                                                   |
| minDetail               | 用户应看到的最不详细的视图。可以"month"，"year"，"decade"或"century"。                                                                                                                                                 | `"century"`                                           | `"decade"`                                                                                                                                                                                                                                                                                           |
| navigationAriaLabel     | aria-label 在日历导航栏上呈现的标签的属性。                                                                                                                                                                            | n/a                                                   | `"Go up"`                                                                                                                                                                                                                                                                                            |
| navigationLabel         | 在日历导航栏上呈现的标签的内容。                                                                                                                                                                                       | (default label)                                       | ``({ date, label, locale, view }) => `Current view: ${view}, date: ${date.toLocaleDateString(locale)}` ``                                                                                                                                                                                            |
| nextAriaLabel           | aria-label 导航窗格上“下一个”按钮的属性。                                                                                                                                                                              | n/a                                                   | `"Next"`                                                                                                                                                                                                                                                                                             |
| nextLabel               | 导航窗格中“下一个”按钮的内容。将值显式设置为null将隐藏该图标。                                                                                                                                                         | `"›"`                                                 | <ul><li>String: `"›"`</li><li>React element: `<NextIcon />`</li></ul>                                                                                                                                                                                                                                |
| next2AriaLabel          | aria-label 导航窗格上的“更高级别的下一个”按钮的属性。                                                                                                                                                                  | n/a                                                   | `"Jump forwards"`                                                                                                                                                                                                                                                                                    |
| next2Label              | 导航窗格上“下一个更高级别”按钮的内容。将值显式设置为null将隐藏该图标。                                                                                                                                                 | `"»"`                                                 | <ul><li>String: `"»"`</li><li>React element: `<DoubleNextIcon />`</li></ul>                                                                                                                                                                                                                          |
| onActiveStartDateChange | 当用户使用上一个/下一个按钮从一个视图导航到另一个视图时调用的函数。                                                                                                                                                    | n/a                                                   | `({ activeStartDate, value, view }) => alert('Changed view to: ', activeStartDate, view)`                                                                                                                                                                                                            |
| onChange                | 当用户单击可用的最详细视图上的项目（按月查看，按月查看等）时调用的函数。                                                                                                                                               | n/a                                                   | `(value, event) => alert('New date is: ', value)`                                                                                                                                                                                                                                                    |
| onViewChange            | 当用户使用向上钻取按钮或单击磁贴从一个视图导航到另一个视图时调用的函数。                                                                                                                                               | n/a                                                   | `({ activeStartDate, value, view }) => alert('New view is: ', view)`                                                                                                                                                                                                                                 |
| onClickDay              | 用户单击天时调用的函数。                                                                                                                                                                                               | n/a                                                   | `(value, event) => alert('Clicked day: ', value)`                                                                                                                                                                                                                                                    |
| onClickDecade           | 用户单击年后调用的函数。                                                                                                                                                                                               | n/a                                                   | `(value, event) => alert('Clicked decade: ', value)`                                                                                                                                                                                                                                                 |
| onClickMonth            | 用户单击月时调用的函数。                                                                                                                                                                                               | n/a                                                   | `(value, event) => alert('Clicked month: ', value)`                                                                                                                                                                                                                                                  |
| onClickWeekNumber       | 函数在用户单击星期时调用。                                                                                                                                                                                             | n/a                                                   | `(weekNumber, date, event) => alert('Clicked week: ', weekNumber, 'that starts on: ', date)`                                                                                                                                                                                                         |
| onClickYear             | 用户单击年份时调用的函数。                                                                                                                                                                                             | n/a                                                   | `(value, event) => alert('Clicked year: ', value)`                                                                                                                                                                                                                                                   |
| onDrillDown             | 当用户通过单击图块向下钻取时调用的函数。                                                                                                                                                                               | n/a                                                   | `({ activeStartDate, view }) => alert('Drilled down to: ', activeStartDate, view)`                                                                                                                                                                                                                   |
| onDrillUp               | 用户单击向上钻取按钮向上钻取时调用的函数。                                                                                                                                                                             | n/a                                                   | `({ activeStartDate, view }) => alert('Drilled up to: ', activeStartDate, view)`                                                                                                                                                                                                                     |
| prevAriaLabel           | aria-label 导航窗格上“上一个”按钮的属性。                                                                                                                                                                              | n/a                                                   | `"Previous"`                                                                                                                                                                                                                                                                                         |
| prevLabel               | 导航窗格中“上一个”按钮的内容。将值显式设置为null将隐藏该图标。                                                                                                                                                         | `"‹"`                                                 | <ul><li>String: `"‹"`</li><li>React element: `<PreviousIcon />`</li></ul>                                                                                                                                                                                                                            |
| prev2AriaLabel          | aria-label 导航窗格中“上一级的上一个”按钮的属性。                                                                                                                                                                      | n/a                                                   | `"Jump backwards"`                                                                                                                                                                                                                                                                                   |
| prev2Label              | 导航窗格中“更高级别上一个”按钮的内容。将值显式设置为null将隐藏该图标。                                                                                                                                                 | `"«"`                                                 | <ul><li>String: `"«"`</li><li>React element: `<DoublePreviousIcon />`</li></ul>                                                                                                                                                                                                                      |
| returnValue             | 日历应将哪些日期传递给onChange函数和onClick {Period}函数。可能是"start"，"end"或"range"。后者将导致带有开始和结束值的数组被传递。                                                                                      | `"start"`                                             | `"range"`                                                                                                                                                                                                                                                                                            |
| showDoubleView          | 是否一次显示两个月/年/…，而不是一次。强制showFixedNumberOfWeeks支柱true。                                                                                                                                              | `false`                                               | `true`                                                                                                                                                                                                                                                                                               |
| showFixedNumberOfWeeks  | 是否始终显示固定周数（6）。强制showNeighboringMonth支柱true。                                                                                                                                                          | `false`                                               | `true`                                                                                                                                                                                                                                                                                               |
| showNavigation          | 是否应渲染带有箭头和标题的导航栏。                                                                                                                                                                                     | `true`                                                | `false`                                                                                                                                                                                                                                                                                              |
| showNeighboringMonth    | 如果月份不是在一周的第一天开始还是在一周的最后一天没有结束，则应呈现上个月还是下个月的天。                                                                                                                             | `true`                                                | `false`                                                                                                                                                                                                                                                                                              |
| selectRange             | 用户是否应选择两个日期而不是一个日期来构成一个范围。注意：无论returnValue设置如何，此功能都会使React-Calendar返回带有两个日期的数组。                                                                                  | `false`                                               | `true`                                                                                                                                                                                                                                                                                               |
| showWeekNumbers         | 周数是否应显示在MonthView的左侧。                                                                                                                                                                                      | `false`                                               | `true`                                                                                                                                                                                                                                                                                               |
| tileClassName           | 将应用于给定日历项目的类名称（按月查看，按月查看等）。                                                                                                                                                                 | n/a                                                   | <ul><li>String: `"class1 class2"`</li><li>Array of strings: `["class1", "class2 class3"]`</li><li>Function: `({ activeStartDate, date, view }) => view === 'month' && date.getDay() === 3 ? 'wednesday' : null`</li></ul>                                                                            |
| tileContent             | 允许在给定的日历项（月日视图，年月视图等）中呈现自定义内容。                                                                                                                                                           | n/a                                                   | <ul><li>String: `"Sample"`</li><li>React element: `<TileContent />`</li><li>Function: `({ activeStartDate, date, view }) => view === 'month' && date.getDay() === 0 ? <p>It's Sunday!</p> : null`</li></ul>                                                                                          |
| tileDisabled            | 传递函数以确定是否应将某天显示为禁用状态。                                                                                                                                                                             | n/a                                                   | <ul><li>Function: `({activeStartDate, date, view }) => date.getDay() === 0`</li></ul>                                                                                                                                                                                                                |
| value                   | 日历值。可以是一个值或两个值的数组。如果您希望以不受控制的方式使用React-Calendar，请defaultValue改为使用。                                                                                                             | n/a                                                   | <ul><li>Date: `new Date()`</li><li>An array of dates: `[new Date(2017, 0, 1), new Date(2017, 7, 1)]`                                                                                                                                                                                                 |
| view                    | 确定应打开哪个日历视图。不禁用导航。可以"month"，"year"，"decade"或"century"。如果您希望以不受控制的方式使用React-Calendar，请defaultView改为使用。                                                                    | The most detailed view allowed                        | `"year"`                                                                                                                                                                                                                                                                                             |

### MonthView, YearView, DecadeView, CenturyView

分别显示给定的月、年、十年和世纪。

#### Props

| Prop name       | Description                                                                                                                                           | Default value | Example values                                                                                                                                                                                          |
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------|---------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| activeStartDate | 应显示的日期的开始。                                                                                                                                  | n/a           | `new Date(2017, 0, 1)`                                                                                                                                                                                  |
| hover           | 用户悬停的日期。                                                                                                                                      | n/a           | `new Date(2017, 0, 1)`                                                                                                                                                                                  |
| maxDate         | 用户可选择的最大日期。maxDate部分重叠的时间段也可以选择，尽管react-calendar将确保没有选择以后的日期。                                                 | n/a           | Date: `new Date()`                                                                                                                                                                                      |
| minDate         | 用户可选择的最小日期。minDate部分重叠的时间段也可以选择，尽管react-calendar将确保没有更早的日期被选择。                                               | n/a           | Date: `new Date()`                                                                                                                                                                                      |
| onClick         | 函数在用户单击一个项时调用(按月排列的日视图、按年排列的月视图等等)。                                                                                  | n/a           | `(value) => alert('New date is: ', value)`                                                                                                                                                              |
| tileClassName   | 将应用于给定日历项(月日视图、年月视图等等)的类名。                                                                                                    | n/a           | <ul><li>String: `"class1 class2"`</li><li>Array of strings: `["class1", "class2 class3"]`</li><li>Function: `({ date, view }) => view === 'month' && date.getDay() === 3 ? 'saturday' : null`</li></ul> |
| tileContent     | 允许在给定的项中呈现自定义内容(月日视图、年月视图等等)。注意:对于带有自定义内容的tile，你可能需要设置react-calendar__tile的固定高度，以确保布局一致。 | n/a           | `({ date, view }) => view === 'month' && date.getDay() === 0 ? <p>It's Sunday!</p> : null`                                                                                                              |
| value           | 日历的价值。可以是一个值或两个值的数组。                                                                                                              | n/a           | <ul><li>Date: `new Date()`</li><li>An array of dates: `[new Date(2017, 0, 1), new Date(2017, 7, 1)]`</li><li>String: `2017-01-01`</li><li>An array of strings: `['2017-01-01', '2017-08-01']`</li></ul> |

## Useful links

* [React-Calendar Wiki](https://github.com/wojtekmaj/react-calendar/wiki)

## License

The MIT License.

## Author

<table>
  <tr>
    <td>
      <img src="https://github.com/wojtekmaj.png?s=100" width="100">
    </td>
    <td>
      Wojciech Maj<br />
      <a href="mailto:kontakt@wojtekmaj.pl">kontakt@wojtekmaj.pl</a><br />
      <a href="https://wojtekmaj.pl">https://wojtekmaj.pl</a>
    </td>
  </tr>
</table>

## Thank you

### Sponsors

Thank you to all our sponsors! [Become a sponsor](https://opencollective.com/react-calendar#sponsor) and get your image on our README on GitHub.

<a href="https://opencollective.com/react-calendar#sponsors" target="_blank"><img src="https://opencollective.com/react-calendar/sponsors.svg?width=890"></a>

### Backers

Thank you to all our backers! [Become a backer](https://opencollective.com/react-calendar#backer) and get your image on our README on GitHub.

<a href="https://opencollective.com/react-calendar#backers" target="_blank"><img src="https://opencollective.com/react-calendar/backers.svg?width=890"></a>

### Top Contributors

Thank you to all our contributors that helped on this project!

![Top Contributors](https://opencollective.com/react-calendar/contributors.svg?width=890&button=false)
