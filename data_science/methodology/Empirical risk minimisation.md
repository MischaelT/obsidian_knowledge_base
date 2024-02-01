**Empirical risk minimization** (ERM) is a principle in [statistical learning theory](https://en.wikipedia.org/wiki/Statistical_learning_theory "Statistical learning theory") which defines a family of [learning algorithms](https://en.wikipedia.org/wiki/Machine_learning "Machine learning") and is used to give theoretical bounds on their performance. The core idea is that we cannot know exactly how well an algorithm will work in practice (the true "risk") because we don't know the true distribution of data that the algorithm will work on, but we can instead measure its performance on a known set of training data (the "empirical" risk).

![[Pasted image 20230909120351.png]]
![[Pasted image 20230909120452.png]]
![[Pasted image 20230909120549.png]]
![[Pasted image 20230909120604.png]]

When the loss function is discontinuous, minimizing the empirical risk turns out to be a difficult combinatorial optimization problem. In many practically important cases, this comes down to finding [the maximum joint subsystem](http://www.machinelearning.ru/wiki/index.php?title=%D0%9C%D0%B0%D0%BA%D1%81%D0%B8%D0%BC%D0%B0%D0%BB%D1%8C%D0%BD%D0%B0%D1%8F_%D1%81%D0%BE%D0%B2%D0%BC%D0%B5%D1%81%D1%82%D0%BD%D0%B0%D1%8F_%D0%BF%D0%BE%D0%B4%D1%81%D0%B8%D1%81%D1%82%D0%B5%D0%BC%D0%B0 "Maximum Collaborative Subsystem") in the system of inequalities (the number of inequalities coincides with the number of learning objects  ![m](http://www.machinelearning.ru/mimetex/?m)) and is [_NP_ -complete](http://www.machinelearning.ru/wiki/index.php?title=NP-%D0%BF%D0%BE%D0%BB%D0%BD%D0%B0%D1%8F_%D0%B7%D0%B0%D0%B4%D0%B0%D1%87%D0%B0&action=edit "NP-complete problem") .

Along with the threshold loss functions, all kinds of their _continuous approximations_ are used , which makes it possible to apply quite effective classical methods of continuous optimization, including gradient methods. Moreover, it turns out that the use of certain approximations can improve [the generalization ability](http://www.machinelearning.ru/wiki/index.php?title=%D0%9E%D0%B1%D0%BE%D0%B1%D1%89%D0%B0%D1%8E%D1%89%D0%B0%D1%8F_%D1%81%D0%BF%D0%BE%D1%81%D0%BE%D0%B1%D0%BD%D0%BE%D1%81%D1%82%D1%8C "Generalization ability") of the classification algorithm.
## Что такое ядра

![[Pasted image 20230910161610.png]]
Вопрос: можно ли заменить скалярное произведение какой-то функцией  пары объектов и так это можно делать, если у нас будет какая-то функция фи, которая переводит векторы одного пространства в векторы другого пространства Н, и в новом пространстве Н существует скалярное произведение. И мы будет пользоваться скалярным произведением этого пространства. И строить SVM #svm мы будем именно а этом пространсве. ТО есть строить там плоскость и тд.
#linear_algebra 

Вопрос: нам нудно найти фкнцкию которая будет представуима в пространства H, как скалярное произведение. Строить ее напрямую очень сложно так как выполнить все условия, симметричности и не отрицательной определенности сложно
ПОэтому используют некоторый набор правил, которые позволяюь найти новые ядра из уже существующих
![[Pasted image 20230910163236.png]]
Пример:
#linear_spaces

![[Pasted image 20230910163040.png]]

![[Pasted image 20230910163735.png]]

#вопрос ПОчему они могут считаться нейронными сетями?

![[Pasted image 20230910164601.png]]

## Svm regression
Предполодим, что теперь вместо классификации чисел мы переходим к регрессии и теперемы предсказываем некие y_i.
Мы взяли линейную регрессионную модель и определили для нее фенкцию потерь. Функция может отклонят ся на какое-то определенное число внутри нахоядсь внутри заданного диапазона. После этого наказание для модели идет линейно
![[Pasted image 20230910164959.png]]

![[Pasted image 20230910165645.png]] 

![[Pasted image 20230910170050.png]]

![[Pasted image 20230910171246.png]]

#regularisation 

![[Pasted image 20230910171325.png]]

![[Pasted image 20230910171736.png]]

![[Pasted image 20230910171921.png]]