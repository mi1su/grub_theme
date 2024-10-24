## Описание темы GRUB

Данная тема GRUB предназначена для экранов с разрешением **`2560x1600`**. 

### Центрирование элементов

При использовании параметра `left = 50%-X`, вы указываете, что элемент должен быть смещен влево от центра экрана на `X` пикселей. Чтобы правильно центрировать элемент `+boot_menu`, необходимо учесть ширину самого меню.

### Расчет ширины меню

Если ширина вашего меню составляет 60% от ширины экрана, то:

- **Ширина экрана**: 2560 пикселей
- **60% от 2560**: \( 2560 \times 0.6 = 1536 \) пикселей
- **Половина ширины меню**: \( 1536 / 2 = 768 \) пикселей

Таким образом, чтобы центрировать меню, вам нужно установить `left` на:

```plaintext
left = 50%-768
```

### Шрифты

В данной теме используются шрифты [Poppins](https://fonts.google.com/specimen/Poppins). 
Для создания шрифта с нужным размером выполните следующую команду:

```bash
sudo grub-mkfont -v -s 28 -o /usr/share/grub/themes/min_theme/Poppins-28.pf2 Poppins-Regular.ttf 
```

### Установка темы GRUB

Для установки данной темы выполните следующие шаги:

1. **Переместите тему** в нужную директорию:
   ```sh
   sudo mv /путь/к/теме/min_theme /usr/share/grub/themes/
   ```
   Установите правильные права доступа и владельца:
   ```sh
   sudo chmod -R 644 /usr/share/grub/themes/min_theme/*
   sudo chown -R root:root /usr/share/grub/themes/min_theme/*
   ```

2. **Откройте файл конфигурации GRUB** в редакторе:
   ```sh
   sudo vim /etc/default/grub
   ```

3. **Убедитесь, что в файле указана тема**:
   Найдите строку, начинающуюся с `GRUB_THEME`, и измените её на:
   ```sh
   GRUB_THEME="/usr/share/grub/themes/min_theme/theme.txt"
   ```

4. **Сгенерируйте новый конфигурационный файл GRUB**:
   ```sh
   sudo grub-mkconfig -o /boot/grub/grub.cfg
   ```

После выполнения этих шагов ваша тема GRUB будет установлена и активирована.