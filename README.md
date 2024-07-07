# Библиотека Орион
Эта документация относится к стабильной версии библиотеки Орион.

## Загружаем библиотеку
```lua
local OrionLib = loadstring(game:HttpGet(('https://raw.githubusercontent.com/shlexware/Orion/main/source')))()
```



## Создаем Окно
```lua
local Window = OrionLib:MakeWindow({Name = "Название Окна Интерфейса", HidePremium = false, SaveConfig = true, ConfigFolder = "Тест"})

--[[
Name = <string> - Название вашего интерфейса(обязательно в кавычках).
HidePremium = <bool> - Показывает, является ли юзер премиумом или нет. Может быть true или false.
SaveConfig = <bool> - вкл/выкл сохранение конфига. Желательно оставлять true.
ConfigFolder = <string> - Название папки с конфигом(обязательно в кавычках).
IntroEnabled = <bool> - Анимация при запуске. true или false
IntroText = <string> - Текст анимации(обязательно в кавычках).
IntroIcon = <string> - Здесь можно вставить ссылку на картинку для анимации(обязательно в кавычках).
Icon = <string> - Тоже самое, что и "IntroIcon", только для окна интерфейса.
CloseCallback = <function> - Функция, выполняющаяся при закрытии интерфейса.
]]
```



## Создаем вкладку
```lua
local Tab = Window:MakeTab({
	Name = "Вкладка 1",
	Icon = "rbxassetid://4483345998",
	PremiumOnly = false
})

--[[
Name = <string> - Имя вкладки.
Icon = <string> - Иконка вкладки.
PremiumOnly = <bool> - Делает вкладку доступной только премиум юзерам(оставлять false).
]]
```
## Создаем Раздел
```lua
local Section = Tab:AddSection({
	Name = "Раздел"
})

--[[
Name = <string> - Имя раздела.
]]
```
Ты можешь добавлять элементы в разделы так же, как добавляешь их во вкладку.

## Уведомляем пользователя
```lua
OrionLib:MakeNotification({
	Name = "Название",
	Content = "Уведомление... что же там написано??",
	Image = "rbxassetid://4483345998",
	Time = 5
})

--[[
Title = <string> - Название уведомления.
Content = <string> - Текст уведомления.
Image = <string> - Картинка уведомления.
Time = <number> - Длительность уведомления(сколько оно будет отображаться на экране).
]]
```



## Создаем кнопку
```lua
Tab:AddButton({
	Name = "Кнопка",
	Callback = function()
      		print("Кнопка нажата")
  	end    
})

--[[
Name = <string> - Название кнопки.
Callback = <function> - Функция кнопки.
]]
```


## Создаем переключатель(или тумблер, называйте как хотите)
```lua
Tab:AddToggle({
	Name = "Это переключатель... или тумблер... я не определился при переводе",
	Default = false,
	Callback = function(Value)
		print(Value)
	end    
})

--[[
Name = <string> - Имя переключателя... или тумблера... я не определился.
Default = <bool> - Значение переключателя или тумблера. Может быть true или false.
Callback = <function> - Функция переключателя(ура наконец то я определился).
]]
```

### Изменяем значение уже существующего переключателя
```lua
CoolToggle:Set(true)
```



## Создаем функцию выбора цвета
```lua
Tab:AddColorpicker({
	Name = "Выбрать Цвет",
	Default = Color3.fromRGB(255, 0, 0),
	Callback = function(Value)
		print(Value)
	end	  
})

--[[
Name = <string> - Имя.
Default = <color3> - Стандартное значение.
Callback = <function> - Функция.
]]
```

### Устанавливаем значение выбора цвета
```lua
ColorPicker:Set(Color3.fromRGB(255,255,255))
```


## Создаем слайдер
```lua
Tab:AddSlider({
	Name = "Слайдер",
	Min = 0,
	Max = 20,
	Default = 5,
	Color = Color3.fromRGB(255,255,255),
	Increment = 1,
	ValueName = "bananas",
	Callback = function(Value)
		print(Value)
	end    
})

--[[
Name = <string> - Имя.
Min = <number> - Мин. значение.
Max = <number> - Макс. значение.
Increment = <number> - Насколько будет меняться значение при изменении.
Default = <number> - Стандартное значение.
ValueName = <string> - Текст после значения.
Callback = <function> - Функция слайдера(то есть значение чего именно будет менять слайдер).
]]
```

### Изменяем значение уже существующего слайдера
```lua
Slider:Set(2)
```
Убедись что сделал слайдер со значением (local CoolSlider = Tab:AddSlider...) чтобы это работало.


## Создаем лейбл
```lua
Tab:AddLabel("Лейбл")
```

### Изменяем значение уже существующего лейбла
```lua
CoolLabel:Set("Новый лейбл!")
```


## Создаем параграф
```lua
Tab:AddParagraph("Параграф","Текст параграфа или значение")
```

### Изменяем уже существующий параграф
```lua
CoolParagraph:Set("Новый параграф!", "Новый текст или значение в параграфе!")
```


## Создаем текстовое окно
```lua
Tab:AddTextbox({
	Name = "Текстовое окно",
	Default = "Стандартное значение текстового окна(пиши сюда что хочешь)",
	TextDisappear = true,
	Callback = function(Value)
		print(Value)
	end	  
})

--[[
Name = <string> - Имя.
Default = <string> - Стандартное значение текстового окна.
TextDisappear = <bool> - Заставляет текст исчезнуть после потери фокуса.
Callback = <function> - Функция текстового окна.
]]
```


## Создаем Кейбинд
```lua
Tab:AddBind({
	Name = "Бинд",
	Default = Enum.KeyCode.E,
	Hold = false,
	Callback = function()
		print("press")
	end    
})

--[[
Name = <string> - Название бинда.
Default = <keycode> - Стандартное значение бинда (если хочешь поменять, выбери нужную кнопку тут: https://docs.tizen.org/application/dotnet/api/TizenFX/API4/api/Tizen.Uix.InputMethod.KeyCode.html, после чего поменяй "Enum.KeyCode.E" на "Enum.KeyCode.ТвояКнопка").
Hold = <bool> - Нужно ли удерживать кнопку для работы бинда. Может быть true или false.
Callback = <function> - Функция бинда.
]]
```

### Меняем значение существующего бинда
```lua
Bind:Set(Enum.KeyCode.N)
```


## Создаем открывающееся меню
```lua
Tab:AddDropdown({
	Name = "Мень",
	Default = "1",
	Options = {"1", "2"},
	Callback = function(Value)
		print(Value)
	end    
})

--[[
Name = <string> - Имя выпадающего меню.
Default = <string> - Стандартное значение.
Options = <table> - Опции в выпадающем меню.
Callback = <function> - Функция выпадающего меню.
]]
```

### Добавляем пару новых кнопок в выпадающее меню
```lua
Dropdown:Refresh(List<table>,true)
```

Вышеупомянутое значение «true» определяет, будут ли текущие кнопки удалены.
### Selecting a dropdown option
```lua
Dropdown:Set("dropdown option")
```

# Finishing your script (REQUIRED)
The below function needs to be added at the end of your code.
```lua
OrionLib:Init()
```

### How flags work.
The flags feature in the ui may be confusing for some people. It serves the purpose of being the ID of an element in the config file, and makes accessing the value of an element anywhere in the code possible.
Below in an example of using flags.
```lua
Tab1:AddToggle({
    Name = "Toggle",
    Default = true,
    Save = true,
    Flag = "toggle"
})

print(OrionLib.Flags["toggle"].Value) -- prints the value of the toggle.
```
Flags only work with the toggle, slider, dropdown, bind, and colorpicker.

### Making your interface work with configs.
In order to make your interface use the configs function you first need to add the `SaveConfig` and `ConfigFolder` arguments to your window function. The explanation of these arguments in above.
Then you need to add the `Flag` and `Save` values to every toggle, slider, dropdown, bind, and colorpicker you want to include in the config file.
The `Flag = <string>` argument is the ID of an element in the config file.
The `Save = <bool>` argument includes the element in the config file.
Config files are made for every game the library is launched in.

## Destroying the Interface
```lua
OrionLib:Destroy()
```
