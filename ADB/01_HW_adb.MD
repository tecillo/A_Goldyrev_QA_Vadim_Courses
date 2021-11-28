 **1. Отобразить подключённый девайс в консоли.**
      C:\Users\Maryia Hancharyk\AppData\Local\Android\Sdk\platform-tools>adb devices

 **2. Вывести адрес приложения todolist в системе Android**
      adb shell pm list packages | findstr todolist
      
 **3. Установить .apk файл приложениия todolist на телефон с компьютера через ADB**
      adb install C:\Tecillo\app-debug.apk
      
 **4. Сделать скриншот запущенного приложения todolist и сразу скопировать на компьютер в одной команде.**
      platform-tools>adb shell screencap /sdcard/Download/todoscrenn.png && adb pull /sdcard/Download/todoscrenn.png C:\Tecillo\todotest1.png
 **5. Вывести в консоль логи приложения todolist**
      adb logcat com.android.todolist
      
 **6. Скопировать логи приложения todolist на компьютер.**
      adb logcat -d com.android.todolist >> C:\Tecillo\todo_log.txt

 **7. Удалить приложение todolist с телефона через ADB**
      adb uninstall com.android.todolist


