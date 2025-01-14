6.1
Задача "Съедобное, несъедобное":

Разнообразие животного мира давно будоражит умы человечества. Царства, классы, виды... Почему бы и нам не попробовать выстроить что-то подобное используя наследования классов?



Необходимо описать пример иерархии животного мира, используя классы и принцип наследования.



Создайте:

2 класса родителя: Animal, Plant

Для класса Animal атрибуты alive = True(живой) и fed = False(накормленный), name - индивидуальное название каждого животного.

Для класса Plant атрибут edible = False(съедобность), name - индивидуальное название каждого растения



4 класса наследника:

Mammal, Predator для Animal.

Flower, Fruit для Plant.



У каждого из объектов класса Mammal и Predator должны быть атрибуты и методы:

eat(self, food) - метод, где food - это параметр, принимающий объекты классов растений.

В данном случае можно использовать принцип наследования, чтобы не дублировать код.



Метод eat должен работать следующим образом:

Если переданное растение (food) съедобное - выводит на экран "<self.name> съел <food.name>", меняется атрибут fed на True.

Если переданное растение (food) не съедобное - выводит на экран "<self.name> не стал есть <food.name>", меняется атрибут alive на False.

Т.е если животному дать съедобное растение, то животное насытится, если не съедобное - погибнет.



У каждого объекта Fruit должен быть атрибут edible = True (переопределить при наследовании)



Создайте объекты классов и проделайте действия затронутые в примере результата работы программы.



Пункты задачи:

Создайте классы Animal и Plant с соответствующими атрибутами и методами
Создайте(+унаследуйте) классы Mammal, Predator, Flower, Fruit с соответствующими атрибутами и методами. При необходимости переопределите значения атрибутов.
Создайте объекты этих классов.


Пример результата выполнения программы:

Выполняемый код(для проверки):

a1 = Predator('Волк с Уолл-Стрит')

a2 = Mammal('Хатико')

p1 = Flower('Цветик семицветик')

p2 = Fruit('Заводной апельсин')



print(a1.name)

print(p1.name)



print(a1.alive)

print(a2.fed)

a1.eat(p1)

a2.eat(p2)

print(a1.alive)

print(a2.fed)



# Что произошло: Хищник попытался съесть цветок и погиб, млекопитающее съело фрукт и насытилось.



Вывод на консоль:

Волк с Уолл-Стрит

Цветик семицветик

True

False

Волк с Уолл-Стрит не стал есть Цветик семицветик

Хатико съел Заводной апельсин

False

True



Примечания:

Помните, обращаясь к атрибутам объекта текущего класса используйте параметр self.
Передавая объекты классов Fruit и Flower в метод eat, так же можно обращаться к их атрибутам внутри.
Обращайте внимание на то, где атрибут класса, а где атрибут объекта.


6.2
Задача "Изменять нельзя получать":

В этой задаче мы реализуем классы транспорта, в которых нельзя будет просто так поменять цвет, мощность двигателя и прочие свойства, т.к. в реальной жизни это чаще всего делается не владельцем, а в специальных сервисах. Да, узнать значения этих свойств мы сможем, но вот изменить - нет.



Вам необходимо создать 2 класса: Vehicle и Sedan, где Vehicle - это любой транспорт, а Sedan(седан) - наследник класса Vehicle.



I. Каждый объект Vehicle должен содержать следующие атрибуты объекта:

Атрибут owner(str) - владелец транспорта. (владелец может меняться)
Атрибут __model(str) - модель (марка) транспорта. (мы не можем менять название модели)
Атрибут __engine_power(int) - мощность двигателя. (мы не можем менять мощность двигателя самостоятельно)
Атрибут __color(str) - название цвета. (мы не можем менять цвет автомобиля своими руками)
А так же атрибут класса:

Атрибут класса __COLOR_VARIANTS, в который записан список допустимых цветов для окрашивания. (Цвета написать свои)
Каждый объект Vehicle должен содержать следующий методы:

Метод get_model - возвращает строку: "Модель: <название модели транспорта>"
Метод get_horsepower - возвращает строку: "Мощность двигателя: <мощность>"
Метод get_color - возвращает строку: "Цвет: <цвет транспорта>"
Метод print_info - распечатывает результаты методов (в том же порядке): get_model, get_horsepower, get_color; а так же владельца в конце в формате "Владелец: <имя>"
Метод set_color - принимает аргумент new_color(str), меняет цвет __color на new_color, если он есть в списке __COLOR_VARIANTS, в противном случае выводит на экран надпись: "Нельзя сменить цвет на <новый цвет>".
Взаимосвязь методов и скрытых атрибутов:

Методы get_model, get_horsepower, get_color находятся в одном классе с соответствующими им атрибутами: __model, __engine_power, __color. Поэтому атрибуты будут доступны для методов.
Атрибут класса __COLOR_VARIANTS можно получить обращаясь к нему через объект(self).
Проверка в __COLOR_VARIANTS происходит не учитывая регистр ('BLACK' ~ 'black').
II. Класс Sedan наследуется от класса Vehicle, а так же содержит следующие атрибуты:

Атрибут __PASSENGERS_LIMIT = 5 (в седан может поместиться только 5 пассажиров)


Пункты задачи:

Создайте классы Vehicle и Sedan.
Напишите соответствующие свойства в обоих классах.
Не забудьте сделать Sedan наследником класса Vehicle.
Создайте объект класса Sedan и проверьте, как работают все его методы, взяты из класса Vehicle.


Пример результата выполнения программы:

Исходный код:

# Текущие цвета __COLOR_VARIANTS = ['blue', 'red', 'green', 'black', 'white']

vehicle1 = Sedan('Fedos', 'Toyota Mark II', 'blue', 500)



# Изначальные свойства

vehicle1.print_info()



# Меняем свойства (в т.ч. вызывая методы)

vehicle1.set_color('Pink')

vehicle1.set_color('BLACK')

vehicle1.owner = 'Vasyok'



# Проверяем что поменялось

vehicle1.print_info()



Вывод на консоль:

Модель: Toyota Mark II

Мощность двигателя: 500

Цвет: blue

Владелец: Fedos

Нельзя сменить цвет на Pink

Модель: Toyota Mark II

Мощность двигателя: 500

Цвет: BLACK

Владелец: Vasyok



Примечания:

Обращайте особое внимание на условия задачи: что является атрибутом класса, а что атрибутом объекта.
Методы, где описано получение/перезапись каких-либо атрибутов рекомендуется начинать со слов get и set соответственно. Такие методы часто используются для доступа к скрытым атрибутам и позволяют написать дополнительную логику(код) при их получении/изменении.
Не забывайте использовать self при обращении к атрибутам объекта.
Константные(постоянные) значения в Python принято писать полностью в верхнем регистре (капсом), как в случае списка цветов или количеством пассажиров.

6.3
Задача "Ошибка эволюции":

Замечали, что некоторые животные в нашем мире обладают странными и, порой, несовместимыми друг с другом свойствами? Например, утконос... Вроде есть клюв, но не птица. Вроде милый, а есть шипы на задних лапах. А ещё он откладывает яйца... Опустим факт о том, что они потеют молоком и попробуем не эволюционным способом создать нашего утконоса.

Необходимо написать 5 классов:

Animal - класс описывающий животных.

Класс обладает следующими атрибутами:

live = True
sound = None - звук (изначально отсутствует)
_DEGREE_OF_DANGER = 0 - степень опасности существа
Объект этого класса обладает следующими атрибутами:

_cords = [0, 0, 0] - координаты в пространстве.
speed = ... - скорость передвижения существа (определяется при создании объекта)
И методами:

move(self, dx, dy, dz), который должен менять соответствующие кооординаты в _cords на dx, dy и dz в том же порядке, где множетелем будет являтся speed. Если при попытке изменения координаты z в _cords значение будет меньше 0, то выводить сообщение "It's too deep, i can't dive :(" , при этом изменения не вносяться.
get_cords(self), который выводит координаты в формате: "X: <координаты по x>, Y: <координаты по y>, Z: <координаты по z>"
attack(self), который выводит "Sorry, i'm peaceful :)", если степень опасности меньше 5 и "Be careful, i'm attacking you 0_0" , если равно или больше.
speak(self), который выводит строку со звуком sound.


Bird - класс описывающий птиц. Наследуется от Animal.

Должен обладать атрибутом:

beak = True - наличие клюва
И методом:

lay_eggs(self), который выводит строку "Here are(is) <случайное число от 1 до 4> eggs for you"


AquaticAnimal - класс описывающий плавающего животного. Наследуется от Animal.

В этом классе атрибут _DEGREE_OF_DANGER = 3.

Должен обладать методом:

dive_in(self, dz) - где dz изменение координаты z в _cords. Этот метод должен всегда уменьшать координату z в _coords. Чтобы сделать dz положительным, берите его значение по модулю (функция abs). Скорость движения при нырянии должна уменьшаться в 2 раза, в отличии от обычного движения. (speed / 2)
PoisonousAnimal - класс описывающий ядовитых животных. Наследуется от Animal.

В этом классе атрибут _DEGREE_OF_DANGER = 8.



Duckbill - класс описывающий утконоса. Наследуется от классов Bird, AquaticAnimal, PoisonousAnimal. Порядок наследования определите сами, опираясь на ниже приведённые примеры выполнения кода.

Объект этого класса должен обладать одним дополнительным атрибутом:

sound = "Click-click-click" - звук, который издаёт утконос


Пример результата выполнения программы:

Пример работы программы:

db = Duckbill(10)



print(db.live)

print(db.beak)



db.speak()

db.attack()



db.move(1, 2, 3)

db.get_cords()

db.dive_in(6)

db.get_cords()



db.lay_eggs()



Вывод на консоль:

True

True

Click-click-click

Be careful, i'm attacking you 0_0

X: 10 Y: 20 Z: 30

X: 10 Y: 20 Z: 0

Here are(is) 3 eggs for you # Число может быть другим (1-4)



По итогу мы должны получить живого утконоса с клювом, атакующего и издающего странные звуки.

После чего утконос совершает манёвры и ныряет.

Теперь утконос в безопасности, он откладывает яйца для будущего потомства.



Примечания:

Будьте внимательней, когда вызываете методы классов родителей в классе наследнике при множественном наследовании: при обращении через super() методы будут искаться сначала в первом, потом во втором и т.д. классах по mro().
При определении порядка наследования обратите внимание на то, что утконос атакует "Be careful, i'm attacking you 0_0"

доп задание

Дополнительное практическое задание по модулю: "Наследование классов."



Цель: Применить знания полученные в модуле, решив задачу повышенного уровня сложности



Задание "Они все так похожи":

2D? 3D? Даже 4D?.... Настолько глубоко мы заходить конечно же не будем, 4D подождёт, но вот с двумерными и трёхмерными фигурами можем поэкспериментировать.

Вы когда-нибудь задумывались как устроены графические библиотеки для языков программирования?

Безусловно, там выполняются огромные расчёты при помощи вашей видеокарты, но... Что лежит в основе удобного использования таких объектов?



По названию задачи можно понять, что все геометрические фигуры обладают схожими свойствами, такими как: длины сторон, цвет и др.



Давайте попробуем реализовать простейшие классы для некоторых таких фигур и при этом применить наследование (в будущем, изучая сторонние библиотеки, вы будете замечать схожие классы, уже написанные кем-то ранее):



Общее ТЗ:

Реализовать классы Figure(родительский), Circle, Triangle и Cube, объекты которых будут обладать методами изменения размеров, цвета и т.д.

Многие атрибуты и методы должны быть инкапсулированны и для них должны быть написаны интерфейсы взаимодействия (методы) - геттеры и сеттеры.



Подробное ТЗ:



Атрибуты класса Figure: sides_count = 0

Каждый объект класса Figure должен обладать следующими атрибутами:

Атрибуты(инкапсулированные): __sides(список сторон (целые числа)), __color(список цветов в формате RGB)
Атрибуты(публичные): filled(закрашенный, bool)
И методами:

Метод get_color, возвращает список RGB цветов.
Метод __is_valid_color - служебный, принимает параметры r, g, b, который проверяет корректность переданных значений перед установкой нового цвета. Корректным цвет: все значения r, g и b - целые числа в диапазоне от 0 до 255 (включительно).
Метод set_color принимает параметры r, g, b - числа и изменяет атрибут __color на соответствующие значения, предварительно проверив их на корректность. Если введены некорректные данные, то цвет остаётся прежним.
Метод __is_valid_sides - служебный, принимает неограниченное кол-во сторон, возвращает True если все стороны целые положительные числа и кол-во новых сторон совпадает с текущим, False - во всех остальных случаях.
Метод get_sides должен возвращать значение я атрибута __sides.
Метод __len__ должен возвращать периметр фигуры.
Метод set_sides(self, *new_sides) должен принимать новые стороны, если их количество не равно sides_count, то не изменять, в противном случае - менять.


Атрибуты класса Circle: sides_count = 1

Каждый объект класса Circle должен обладать следующими атрибутами и методами:

Все атрибуты и методы класса Figure
Атрибут __radius, рассчитать исходя из длины окружности (одной единственной стороны).
Метод get_square возвращает площадь круга (можно рассчитать как через длину, так и через радиус).


Атрибуты класса Triangle: sides_count = 3

Каждый объект класса Triangle должен обладать следующими атрибутами и методами:

Все атрибуты и методы класса Figure
Метод get_square возвращает площадь треугольника. (можно рассчитать по формуле Герона)
Атрибуты класса Cube: sides_count = 12

Каждый объект класса Cube должен обладать следующими атрибутами и методами:

Все атрибуты и методы класса Figure.
Переопределить __sides сделав список из 12 одинаковы сторон (передаётся 1 сторона)
Метод get_volume, возвращает объём куба.


ВАЖНО!

При создании объектов делайте проверку на количество переданных сторон, если сторон не ровно sides_count, то создать массив с единичными сторонами и в том кол-ве, которое требует фигура.

Пример 1: Circle((200, 200, 100), 10, 15, 6), т.к. сторона у круга всего 1, то его стороны будут - [1]

Пример 2: Triangle((200, 200, 100), 10, 6), т.к. сторон у треугольника 3, то его стороны будут - [1, 1, 1]

Пример 3: Cube((200, 200, 100), 9), т.к. сторон(рёбер) у куба - 12, то его стороны будут - [9, 9, 9, ....., 9] (12)

Пример 4: Cube((200, 200, 100), 9, 12), т.к. сторон(рёбер) у куба - 12, то его стороны будут - [1, 1, 1, ....., 1]



Код для проверки:

circle1 = Circle((200, 200, 100), 10) # (Цвет, стороны)

cube1 = Cube((222, 35, 130), 6)



# Проверка на изменение цветов:

circle1.set_color(55, 66, 77) # Изменится

print(circle1.get_color())

cube1.set_color(300, 70, 15) # Не изменится

print(cube1.get_color())



# Проверка на изменение сторон:

cube1.set_sides(5, 3, 12, 4, 5) # Не изменится

print(cube1.get_sides())

circle1.set_sides(15) # Изменится

print(circle1.get_sides())



# Проверка периметра (круга), это и есть длина:

print(len(circle1))



# Проверка объёма (куба):

print(cube1.get_volume())





Выходные данные (консоль):

[55, 66, 77]

[222, 35, 130]

[6, 6, 6, 6, 6, 6, 6, 6, 6, 6, 6, 6]

[15]

15

216



Примечания (рекомендации):

Рекомендуется сделать дополнительные (свои проверки) работы методов объектов каждого класса.
Делайте каждый класс и метод последовательно и проверяйте работу каждой части отдельно.
Для проверки принадлежности к типу рекомендуется использовать функцию isinstance.
Помните, служебные инкапсулированные методы можно и нужно использовать только внутри текущего класса.
Вам не запрещается вводить дополнительные атрибуты и методы, творите, но не переборщите!




Успехов!

Дополнительное практическое задание по модулю: "Наследование классов."



Цель: Применить знания полученные в модуле, решив задачу повышенного уровня сложности



Задание "Они все так похожи":

2D? 3D? Даже 4D?.... Настолько глубоко мы заходить конечно же не будем, 4D подождёт, но вот с двумерными и трёхмерными фигурами можем поэкспериментировать.

Вы когда-нибудь задумывались как устроены графические библиотеки для языков программирования?

Безусловно, там выполняются огромные расчёты при помощи вашей видеокарты, но... Что лежит в основе удобного использования таких объектов?



По названию задачи можно понять, что все геометрические фигуры обладают схожими свойствами, такими как: длины сторон, цвет и др.



Давайте попробуем реализовать простейшие классы для некоторых таких фигур и при этом применить наследование (в будущем, изучая сторонние библиотеки, вы будете замечать схожие классы, уже написанные кем-то ранее):



Общее ТЗ:

Реализовать классы Figure(родительский), Circle, Triangle и Cube, объекты которых будут обладать методами изменения размеров, цвета и т.д.

Многие атрибуты и методы должны быть инкапсулированны и для них должны быть написаны интерфейсы взаимодействия (методы) - геттеры и сеттеры.



Подробное ТЗ:



Атрибуты класса Figure: sides_count = 0

Каждый объект класса Figure должен обладать следующими атрибутами:

Атрибуты(инкапсулированные): __sides(список сторон (целые числа)), __color(список цветов в формате RGB)
Атрибуты(публичные): filled(закрашенный, bool)
И методами:

Метод get_color, возвращает список RGB цветов.
Метод __is_valid_color - служебный, принимает параметры r, g, b, который проверяет корректность переданных значений перед установкой нового цвета. Корректным цвет: все значения r, g и b - целые числа в диапазоне от 0 до 255 (включительно).
Метод set_color принимает параметры r, g, b - числа и изменяет атрибут __color на соответствующие значения, предварительно проверив их на корректность. Если введены некорректные данные, то цвет остаётся прежним.
Метод __is_valid_sides - служебный, принимает неограниченное кол-во сторон, возвращает True если все стороны целые положительные числа и кол-во новых сторон совпадает с текущим, False - во всех остальных случаях.
Метод get_sides должен возвращать значение я атрибута __sides.
Метод __len__ должен возвращать периметр фигуры.
Метод set_sides(self, *new_sides) должен принимать новые стороны, если их количество не равно sides_count, то не изменять, в противном случае - менять.


Атрибуты класса Circle: sides_count = 1

Каждый объект класса Circle должен обладать следующими атрибутами и методами:

Все атрибуты и методы класса Figure
Атрибут __radius, рассчитать исходя из длины окружности (одной единственной стороны).
Метод get_square возвращает площадь круга (можно рассчитать как через длину, так и через радиус).


Атрибуты класса Triangle: sides_count = 3

Каждый объект класса Triangle должен обладать следующими атрибутами и методами:

Все атрибуты и методы класса Figure
Метод get_square возвращает площадь треугольника. (можно рассчитать по формуле Герона)
Атрибуты класса Cube: sides_count = 12

Каждый объект класса Cube должен обладать следующими атрибутами и методами:

Все атрибуты и методы класса Figure.
Переопределить __sides сделав список из 12 одинаковы сторон (передаётся 1 сторона)
Метод get_volume, возвращает объём куба.


ВАЖНО!

При создании объектов делайте проверку на количество переданных сторон, если сторон не ровно sides_count, то создать массив с единичными сторонами и в том кол-ве, которое требует фигура.

Пример 1: Circle((200, 200, 100), 10, 15, 6), т.к. сторона у круга всего 1, то его стороны будут - [1]

Пример 2: Triangle((200, 200, 100), 10, 6), т.к. сторон у треугольника 3, то его стороны будут - [1, 1, 1]

Пример 3: Cube((200, 200, 100), 9), т.к. сторон(рёбер) у куба - 12, то его стороны будут - [9, 9, 9, ....., 9] (12)

Пример 4: Cube((200, 200, 100), 9, 12), т.к. сторон(рёбер) у куба - 12, то его стороны будут - [1, 1, 1, ....., 1]



Код для проверки:

circle1 = Circle((200, 200, 100), 10) # (Цвет, стороны)

cube1 = Cube((222, 35, 130), 6)



# Проверка на изменение цветов:

circle1.set_color(55, 66, 77) # Изменится

print(circle1.get_color())

cube1.set_color(300, 70, 15) # Не изменится

print(cube1.get_color())



# Проверка на изменение сторон:

cube1.set_sides(5, 3, 12, 4, 5) # Не изменится

print(cube1.get_sides())

circle1.set_sides(15) # Изменится

print(circle1.get_sides())



# Проверка периметра (круга), это и есть длина:

print(len(circle1))



# Проверка объёма (куба):

print(cube1.get_volume())





Выходные данные (консоль):

[55, 66, 77]

[222, 35, 130]

[6, 6, 6, 6, 6, 6, 6, 6, 6, 6, 6, 6]

[15]

15

216



Примечания (рекомендации):

Рекомендуется сделать дополнительные (свои проверки) работы методов объектов каждого класса.
Делайте каждый класс и метод последовательно и проверяйте работу каждой части отдельно.
Для проверки принадлежности к типу рекомендуется использовать функцию isinstance.
Помните, служебные инкапсулированные методы можно и нужно использовать только внутри текущего класса.
Вам не запрещается вводить дополнительные атрибуты и методы, творите, но не переборщите!




Успехов!

Дополнительное практическое задание по модулю: "Наследование классов."



Цель: Применить знания полученные в модуле, решив задачу повышенного уровня сложности



Задание "Они все так похожи":

2D? 3D? Даже 4D?.... Настолько глубоко мы заходить конечно же не будем, 4D подождёт, но вот с двумерными и трёхмерными фигурами можем поэкспериментировать.

Вы когда-нибудь задумывались как устроены графические библиотеки для языков программирования?

Безусловно, там выполняются огромные расчёты при помощи вашей видеокарты, но... Что лежит в основе удобного использования таких объектов?



По названию задачи можно понять, что все геометрические фигуры обладают схожими свойствами, такими как: длины сторон, цвет и др.



Давайте попробуем реализовать простейшие классы для некоторых таких фигур и при этом применить наследование (в будущем, изучая сторонние библиотеки, вы будете замечать схожие классы, уже написанные кем-то ранее):



Общее ТЗ:

Реализовать классы Figure(родительский), Circle, Triangle и Cube, объекты которых будут обладать методами изменения размеров, цвета и т.д.

Многие атрибуты и методы должны быть инкапсулированны и для них должны быть написаны интерфейсы взаимодействия (методы) - геттеры и сеттеры.



Подробное ТЗ:



Атрибуты класса Figure: sides_count = 0

Каждый объект класса Figure должен обладать следующими атрибутами:

Атрибуты(инкапсулированные): __sides(список сторон (целые числа)), __color(список цветов в формате RGB)
Атрибуты(публичные): filled(закрашенный, bool)
И методами:

Метод get_color, возвращает список RGB цветов.
Метод __is_valid_color - служебный, принимает параметры r, g, b, который проверяет корректность переданных значений перед установкой нового цвета. Корректным цвет: все значения r, g и b - целые числа в диапазоне от 0 до 255 (включительно).
Метод set_color принимает параметры r, g, b - числа и изменяет атрибут __color на соответствующие значения, предварительно проверив их на корректность. Если введены некорректные данные, то цвет остаётся прежним.
Метод __is_valid_sides - служебный, принимает неограниченное кол-во сторон, возвращает True если все стороны целые положительные числа и кол-во новых сторон совпадает с текущим, False - во всех остальных случаях.
Метод get_sides должен возвращать значение я атрибута __sides.
Метод __len__ должен возвращать периметр фигуры.
Метод set_sides(self, *new_sides) должен принимать новые стороны, если их количество не равно sides_count, то не изменять, в противном случае - менять.


Атрибуты класса Circle: sides_count = 1

Каждый объект класса Circle должен обладать следующими атрибутами и методами:

Все атрибуты и методы класса Figure
Атрибут __radius, рассчитать исходя из длины окружности (одной единственной стороны).
Метод get_square возвращает площадь круга (можно рассчитать как через длину, так и через радиус).


Атрибуты класса Triangle: sides_count = 3

Каждый объект класса Triangle должен обладать следующими атрибутами и методами:

Все атрибуты и методы класса Figure
Метод get_square возвращает площадь треугольника. (можно рассчитать по формуле Герона)
Атрибуты класса Cube: sides_count = 12

Каждый объект класса Cube должен обладать следующими атрибутами и методами:

Все атрибуты и методы класса Figure.
Переопределить __sides сделав список из 12 одинаковы сторон (передаётся 1 сторона)
Метод get_volume, возвращает объём куба.


ВАЖНО!

При создании объектов делайте проверку на количество переданных сторон, если сторон не ровно sides_count, то создать массив с единичными сторонами и в том кол-ве, которое требует фигура.

Пример 1: Circle((200, 200, 100), 10, 15, 6), т.к. сторона у круга всего 1, то его стороны будут - [1]

Пример 2: Triangle((200, 200, 100), 10, 6), т.к. сторон у треугольника 3, то его стороны будут - [1, 1, 1]

Пример 3: Cube((200, 200, 100), 9), т.к. сторон(рёбер) у куба - 12, то его стороны будут - [9, 9, 9, ....., 9] (12)

Пример 4: Cube((200, 200, 100), 9, 12), т.к. сторон(рёбер) у куба - 12, то его стороны будут - [1, 1, 1, ....., 1]



Код для проверки:

circle1 = Circle((200, 200, 100), 10) # (Цвет, стороны)

cube1 = Cube((222, 35, 130), 6)



# Проверка на изменение цветов:

circle1.set_color(55, 66, 77) # Изменится

print(circle1.get_color())

cube1.set_color(300, 70, 15) # Не изменится

print(cube1.get_color())



# Проверка на изменение сторон:

cube1.set_sides(5, 3, 12, 4, 5) # Не изменится

print(cube1.get_sides())

circle1.set_sides(15) # Изменится

print(circle1.get_sides())



# Проверка периметра (круга), это и есть длина:

print(len(circle1))



# Проверка объёма (куба):

print(cube1.get_volume())



Выходные данные (консоль):

[55, 66, 77]

[222, 35, 130]

[6, 6, 6, 6, 6, 6, 6, 6, 6, 6, 6, 6]

[15]

15

216

Примечания (рекомендации):

Рекомендуется сделать дополнительные (свои проверки) работы методов объектов каждого класса.
Делайте каждый класс и метод последовательно и проверяйте работу каждой части отдельно.
Для проверки принадлежности к типу рекомендуется использовать функцию isinstance.
Помните, служебные инкапсулированные методы можно и нужно использовать только внутри текущего класса.
Вам не запрещается вводить дополнительные атрибуты и методы, творите, но не переборщите!

Успехов!

