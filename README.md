# super front-end team
# Styles
Мы используем [bem методологию](https://ru.bem.info/method/)
# Naming
##### Folders: hyphens.
    example: i-like-our-team
##### Files: camelCase with Upper 1st symbol
    example: ILikeOurTeam
Вообще есть желание везде придерживаться camelCase;    
#React tsx
Имя компонента начинается с большой буквы.
Интерфейсы, описывающие компонент(State, Props)
должны лежать в том же файле, что и сам компонент.
Если компонент имеет имя MyComponent, то имена интерфейсов должны быть следующие:
MyComponentProps, MyComponentState
В одном файле один компонент. Если компонент нуждается в выделении отдельных компонентов, но они используются только в этом компоненте - располагать в том же файле либо в папке компонента
Разметку должен возвращать только метод render, все отстальные методы компонента должны заниматься только логикой.
#Documentation
Используйте [jsDoc](http://usejsdoc.org/) для документации кода.
Обратите внимание, что типы указывать не нужно.
Документация крайне важна для функций, компонентов, сервисов, классов, которые будут переиспользованы.
Предпочтительный язык - unknown
Для автоматической генерации документации пользуемся http://typedoc.io/.

#Это может решить ваши проблемы:)
1) В tsx для приведения к типу пользуйтесь оператором as: 
```javascript
var test = (myProp as string);
```
2) Не вызывайте setState, forceUpdate из метода render;
3) setState на вход принимает объект, содержащий свойства, которые будет установлены в state. объект переданный в setState не обязательно должен содержать все поля.
```javascript 
getInitialState: function() {
  return { x: 0, y: 0 };
}
you can use setState to set individual keys on that object:

this.setState({ x: 1 }); // y still == 0
React does no intelligent merging of your state; for example, this does not work:

getInitialState: function() {
  return {
    point: { x: 0, y: 0 },
    radius: 10
  };
}

this.setState({point: {x: 1}});
// state is now == {point: {x: 1}, radius: 10} (point.y is gone)
```
в react.d.ts явно прописано, что setState на вход принимает State. по этому а нужно привести явно.    


Метод render в React.component возвращает тип JSX.Element, что означает что любой теговый элемент является экземпляром этого типа;
### Использование require, import.
Мы используем es-6 imports
```javascript 
    import {AnyType1, AnyType2} from './path/to/any'
```
в некоторых случаях для автоматической сборки зависимостей нам нужно пользоваться require (напрмер для загрузки стилей).
В таких случаях нужно явно вызвать require для ресурса.
``` javascript
declare require:(any)=> any;
require('../../path/to/need/styles');
```
