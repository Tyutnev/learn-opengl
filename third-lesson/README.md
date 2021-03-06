# Третий урок
## Разбор первой программы
Итак, разберем первую программу. На данный момент, она просто запускает окно с черным фоном. Исходной код находится в этой же поддиректории с именем example.cpp

**Первый пункт:**
```cpp
glfwInit(); //1
```
Инициализация графического конвейера.
Мы можем мысленно, представить нашу программу, как пустую очередь из элементов. И на данный момент мы эту очередь инициализировали.

**Второй пункт:**
```cpp
glfwWindowHint(GLFW_CONTEXT_VERSION_MAJOR, 3); //2
glfwWindowHint(GLFW_CONTEXT_VERSION_MINOR, 3); //2
```
Настраеваем иницилазированную графическую программу. Устанавливаем мажорную и минорную версию OpenGL. Если данная версия у пользователя не поддерживается, то тогда программа не запустится.

**Третий пункт:**
```cpp
glfwWindowHint(GLFW_OPENGL_PROFILE, GLFW_OPENGL_CORE_PROFILE); //3
```
Указываем, что используем Core-profile режим. Мы не сможешь использовать устаревшие функции.

**Четвертый пункт:**
```cpp
glfwWindowHint(GLFW_RESIZABLE, GL_FALSE); //4
```
Указываем, что созданное окно не сможет изменять размер.

**Пятый пункт:**
```cpp
GLFWwindow* window = glfwCreateWindow(800, 600, "LearnOpenGL", nullptr, nullptr); //5
```
Создание объекта окна. В качестве первого аргумента передаем ширину окна, второй аргумент - высота окна, третий аргумент - заголовок окна.

**Шестой пункт:**
```cpp
glfwMakeContextCurrent(window); //6
```
Создание контекста окна

**Седьмой пункт:**
```cpp
glewExperimental = GL_TRUE; //7
```
Инициализация GLEW

**Восьмой пункт:**
```cpp
int width, height; //8
glfwGetFramebufferSize(window, &width, &height); //8
```
Создаем переменный, хранящие ширину и высоту кона, затем получаем и сохраняем ширину и высоту созданного ранее окна в эти переменные.

**Девятый пункт:**
```cpp
glViewport(0, 0, width, height); //9
```
Задаем координаты относительного окна и размер отображаемого окна.

**Десятый пункт:**
```cpp
	while (!glfwWindowShouldClose(window)) //10
	{
		glfwPollEvents(); //10
		glfwSwapBuffers(window); //10
	}
```
Цикл, в котором будет работать наше приложение, этот цикл будет работать, пока не закроется окно.
Функция glfwWindowShouldClose проверяет в начале каждой итерации цикла, получил ли GLFW инструкцию к закрытию.

Функция glfwPollEvents проверяет были ли вызваны какие либо события (вроде ввода с клавиатуры или перемещение мыши) и вызывает установленные функции (которые мы можем установить через функции обратного вызова (callback)). Обычно мы вызываем функции обработки событий в начале итерации цикла.

Функция glfwSwapBuffers заменяет цветовой буфер (большой буфер, содержащий значения цвета для каждого пикселя в GLFW окне), который использовался для отрисовки во время текущей итерации и показывает результат на экране.

**Одиннадцатый пункт:**
```cpp
glfwTerminate(); //11
```
Отчистка выделенных ресурсов.