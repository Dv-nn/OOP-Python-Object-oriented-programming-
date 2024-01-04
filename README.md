# Python ОПП  (Object Oriented Programming)  
общие свойства объектов в языке программирования.  

ООП строится вокруг четырёх основных принципов: абстракция, инкапсуляция, наследование и полиморфизм.  
- **Инкапсуляция**  
Доступ к данным объекта должен контролироваться, чтобы пользователь не мог изменить их в произвольном порядке и что-то поломать. Поэтому для работы с данными программисты пишут методы, которые можно будет использовать вне класса и которые ничего не сломают внутри.  
- **Наследование**  
Классы могут передавать свои атрибуты и методы классам-потомкам.  
- **Полиморфизм**    
Этот принцип позволяет применять одни и те же команды к объектам разных классов, даже если они выполняются по-разному.    
- **Абстракция**    
При создании класса мы упрощаем его до тех атрибутов и методов, которые нужны именно в этом коде, не пытаясь описать его целиком и отбрасывая всё второстепенное.    
____  

**Class**   
-данные(свойства)   
> prop = ‘value’  
- методы(действия)   
> def get_prop(self, x, y):  
>   self.x = x  
>    self.y = y  
>  

**Добавить св-во**  
>  Сlass.prop = ‘value’  
>  setattr(Class, ‘prop’, ‘value’)  

**Читать св-во**  
>  c = Сlass.prop   - если нет св-ва, возвращает ошибку  
> getattr(Class, prop, False)  - если нет св-ва, возвращает третий аргумент  

**Наличие св-ва**  
>  hasattr(Class, prop)   - учитывает наследование  
 
**Удалить св-во  
>  del Сlass.prop   - если нет св-ва, возвращает ошибку  
>  delattr(Class, prop)  - если нет св-ва, возвращает ошибку  

**Пространство имен**  
>  Class.__dict__  

**Все свойства экз.класса**  
>  dir(obj)  

**Описание класса, комментарий**  
>  Class.__doc__  

**Метод класса**  
> @classmethod - работает с атрибутами класса  
> def method_a(cls, arg):  
>     return cls.x  
>   

**Статический метод**  
> @staticmethod  - независимая, сервисная функция; нет дополнительных параментров, кроме тех, которые указываем; не имеют доступа к атрибутам класса и к атрибутам экз.класса; можем вызыват внутри обычных методов  
> def method_b(x, y):
>     return x*x + y*y
>   

**Режим доступа (механизм инкапсуляции)** 
>  attr  - публичное свойство  
>  _attr  - режим доступа protected  
>  __attr  - режим доступа private  

> pip install accessify - защитить методы от внешнего доступа
____  

**Магические методы** - методы, которые вызываются интерпретатором для выполнения различных операций над объектами.  

| Метод |	Что делает |
|----------------:|----------------:|
|  __new__(cls)   return super().__new__(cls)  |  Создание объекта cls ссылается на текущий класс должен возвращать адрес нового созданного объекта   |
| __init__(self) | Инициализатор объекта |  
| __del__(self) | Финализатор объекта |  
| __setattr__(self, key, value) | Автоматически вызывается при изменении свойства key класса |  
| __getattribute__(self, item) | Автоматически вызывается при получении свойства класса с именем item |  
| __getattr__(self, item) | Автоматически вызывается при получении несуществующего свойства item класса |  
| __delattr__(self, item) | Автоматически вызывается при удалении свойства item (не важно существует оно или нет) |  
| __сall__(self, *args, **kwargs) | Позволяет экземплярам класса вести себя так, как будто они функции |  
| __str__(self) | Для отображения информации об объекте класса для пользователей |  
| __repr__(self) | Для отображения информации об объекте класса в режиме отладки |  
| __len__(self) | Позволяет применить функцию len() к экземпляру класса |  
| __abs__(self) | Позволяет применить функцию abs() к экземпляру класса |  
| __add__(self) | Для операции сложения |  
| __sub__(self) | Для операции вычитания |  
| __mul__(self) | Для операции умножения |  
| __truediv__(self) | Для операции деления |  
| __eq__(self) | Для равенства == |  
| __ne__(self) | Для неравенства != |  
| __lt__(self) | Для оператора < |  
| __le__(self) | Для оператора <= |  
| __gt__(self) | Для оператора > |  
| __ge__(self) | Для оператора >= |  
| __hash__(self) | Вычисляется хэш экземпляра класса |  
| __bool__(self) | Используется в программах, где требуется описать собственные проверки истинности или ложности объектов |  
| __getitem__(self, item) | Получение значения по ключу item | 
| __setitem__(self, key, value) | Запись значения value по ключу key |  
| __delitem__(self, key) | Удаление элемента по ключу key |  
| __iter__(self) | Получение итератора для перебора объекта | 
| __next__(self) | Переход к следующему значению и его считывание |  

____  

**Oбъект-свойство property**    
> объект-свойство property  
> 1. prop = property (getter, setter)  
>  
> 2. @property  
>    def name(self):  
>          return self.__name  
>
>    @name.setter  
>    def name(self, name):  
>          self.__name = name  
>
>    @name.deleter  
>     def name(self):  
>           del self.__name |  Для работы с приватными локальными свойствами экземпляров классов  
     
> коллекция  __slots__  
> __slots__ = (’x’, ‘y’) | Ограничивает допустимый набор имен атрибутов объекта только перечисленными именами  
> - ограничение создаваемых локальных свойств  
> - уменьшение занимаемой памяти, атрибут __dict__ удаляется  
> - ускорение работы с локальными свойствами     
____  

**Метакласс:**  
![](https://github.com/Dv-nn/Python--Object-Oriented-Programming/blob/main/img/img1.PNG)   
![](https://github.com/Dv-nn/Python--Object-Oriented-Programming/blob/main/img/img2.PNG)   

**Dataclass:**  
![](https://github.com/Dv-nn/Python--Object-Oriented-Programming/blob/main/img/img3.PNG)    
![](https://github.com/Dv-nn/Python--Object-Oriented-Programming/blob/main/img/img4.PNG)  

**Дескриптор:**  
![](https://github.com/Dv-nn/Python--Object-Oriented-Programming/blob/main/img/img5.PNG) 

____  
![](https://github.com/Dv-nn/Python--Object-Oriented-Programming/blob/main/img/img6.PNG) 

____  

 [ОOП Python  :point_left:](https://github.com/Dv-nn/Python--Object-Oriented-Programming/blob/main/ОOП_Python.pdf)   

