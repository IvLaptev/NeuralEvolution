# NeuralEvolution

**Цель проекта:** создать симулятор жизни к 15.10 с помощью Deep Q-Learning.

**Основные этапы:**
1.	[Животное должно научиться не умирать (01.10)](#first)
2.	[Размножение, увеличение популяции (15.10)](#second)

**Технологии:** TensorFlow + Unity + gRPC

**Участники и роли:** 
* Иерусалимов – моделлер; 
* Мисаилиди – ML;
* Сергеев – ML;
* Снегирев – PM + backend + ML;
* Шошников – Unity.

**Основные требования:** 
* Серверная часть пишется на python3;
* Клиентская часть пишется на Unity;
* Общение между клиентом и сервером осуществляется протоколом gRPC.

<a name="first"></a>

## Первый этап

> Животное должно научиться не умирать (01.10)

### Логика взаимодействия

![Logic](./images/logic.jpg)

### Описание

**Окружение** – земля, рандомный спаун еды. Необходимо различать объекты окружения.

**Действия** – конечное кол-во действий, каждое из которых уникально и имеет свой id. Описывает, что должен сделать субъект мира. Обязательно должно быть действие недействия (null).

**Субъект мира** – животное, имеющее уровень жизни и уровень сытости. Оно изначально знает, за что получает награды и штрафы. Уровень сытости субъекта уменьшается каждые N секунд. Уровень жизни падает каждые N секунд, если уровень сытости на нуле.
 
**Возможные действия:**
1.	Ничего не делать
2.	Идти вперед
3.	Поворот влево на N градусов
4.	Поворот вправо на N градусов
5.	Кушац

**Данные, которые приходят на backend:**
1.	Жив ли субъект
2.	Координаты еды относительно субъекта (x и z). Если еды нет – приходят невалидные данные
3.	Уровень жизни субъекта
4.	Уровень сытости субъекта
5.	Награда / наказание за его предыдущее действие

```Нейронке скармливаются пункты 2-4.```

<a name="second"></a>

## Второй этап
