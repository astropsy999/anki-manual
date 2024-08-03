# Anki не підбирає тему GTK у Gnome/Linux

Ви можете вирішити цю проблему, явно вказавши Anki, що таке тема GTK. Виконайте наступні команди в терміналі:

```shell
theme=$(gsettings get org.gnome.desktop.interface gtk-theme)
echo "gtk-theme-name=$theme" >> ~/.gtkrc-2.0
echo "export GTK2_RC_FILES=$HOME/.gtkrc-2.0" >> ~/.profile
```

Потім вийдіть із системи та знову увійдіть, і Anki має вибрати тему GTK.
