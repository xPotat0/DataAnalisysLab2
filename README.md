# АНАЛИЗ ДАННЫХ И ИСКУССТВЕННЫЙ ИНТЕЛЛЕКТ [in GameDev]



Отчет по лабораторной работе #2 выполнил:
- Исмагилов Денис Рустамович
- РИ210945
Отметка о выполнении заданий (заполняется студентом):


| Задание | Выполнение | Баллы |
| ------ | ------ | ------ |
| Задание 1 | * | 60 |
| Задание 2 | # | 20 |
| Задание 3 | # | 20 |


знак "*" - задание выполнено; знак "#" - задание не выполнено;


Работу проверили:
- к.т.н., доцент Денисов Д.В.
- к.э.н., доцент Панов М.А.
- ст. преп., Фадеев В.О.




## Цель работы
Ознакомиться с технологией работы связки Python – Google Sheets - Unity


## Задание 1
### Реализовать совместную работу и передачу данных в связке Python - Google-Sheets – Unity. 
- В облачном сервисе google console подключить API для работы с google sheets и google drive.
- Реализовать запись данных из скрипта на python в google-таблицу. Данные описывают изменение темпа инфляции на протяжении 11 отсчётных периодов, с учётом стоимости игрового объекта в каждый период.
- Создать новый проект на Unity, который будет получать данные из google-таблицы, в которую были записаны данные в предыдущем пункте.
- Написать функционал на Unity, в котором будет воспризводиться аудио-файл в зависимости от значения данных из таблицы.
## Ход работы:
- Зайдём в Google console cloud и создадим новый проект. Для этого нажмём на кнопку справа от надписи Google Cloud – New Project
=====
![7](https://user-images.githubusercontent.com/106258306/195996980-c477e12d-0d81-4b88-9730-758b30508999.png)
=====
- Зайдём в созданный проект и перейдём в Marketplace. Для этого нажмём на меню, слева от названия Google Cloud.

![8](https://user-images.githubusercontent.com/106258306/195996996-e47d7002-e972-4f28-8409-7e6b5f3dccd4.png)

- В появившийся поисковой строке введём “Google Drive Api” и нажмём на предложенный вариант.

![9](https://user-images.githubusercontent.com/106258306/195997002-c9ebcdbf-99a3-4730-90e1-ff8d53c78ab6.png)

- Зайдём в Google Drive API и нажмём Enable.

![10](https://user-images.githubusercontent.com/106258306/195997008-e56c01a1-1a3e-4949-a0bc-7c6e3e996a57.png)

После этого также найдём “Google Sheets Api” и установим его. Далее зайдём в “APIs & Services” , перейдём во вкладку Credentials и создадим Service account(+ Create Credentials). Зададим имя новому аккаунту. После этого он появится ниже, в категории Service Account. Нажмём на него. Перейдём в категорию Keys и создадим новый JSON ключ(ADD KEY – Create Key – JSON). Будет предложено сохранить файл-ключ. Сохраните его в папке с новый файлом Python, с которым мы скоро начнём работу.
  
![11](https://user-images.githubusercontent.com/106258306/195997015-ec205a71-fd4e-42bb-8c57-b4162c2364cd.png)

Перейдём в категорию Details и скопируем Email. Далее зайдём на стартовую страницу и откроем Таблицы. Создадим новый файл.

![12](https://user-images.githubusercontent.com/106258306/195997016-82a140f3-d886-4a5c-8614-95134262b681.png)

- Нажмём кнопку Настройки доступа справа вверху и введём скопированный адрес Email(Для этого также придётся назвать свою таблицу, например UnitySheets). После этого выберем для него роль “Редактор”

![13](https://user-images.githubusercontent.com/106258306/195997021-26909a9f-07ef-4377-a4ee-3135d1cd8143.png)

- Теперь перейдём в файл Python. Установим для него библиотеки Numpy и gspread(File - Settings – Python Interpreter). Далее напишем код для случайной генерации чисел и сохранении этих чисел в файле таблицы, которую мы создали на предыдущих шагах.

![14](https://user-images.githubusercontent.com/106258306/195997027-b93258a9-7db0-4c69-9531-52ff4fd0151d.png)
![15](https://user-images.githubusercontent.com/106258306/195997043-f707bfb9-de4e-4164-a59f-8efead5a0cd7.png)


- Имя файла service_account равно названию файла-ключа, который мы предварительно скачали в ту же папку, что и файл Python.
- Название gc.open(“…”) равно вашему названию таблицы.
- После этого в файле таблицы появятся новые данные.

![16](https://user-images.githubusercontent.com/106258306/195997051-009c06c2-70cf-4cde-8225-18100d9d1687.png)


- После этого вернёмся на страницу Console Google cloud, вкладку APIs & Services, Credentials и создадим API key. После этого напротив ключа, справа, нажмём на три точки – Edit Api Key. На настройке API restrictions выберем Restrict key и в выпадающем меню выберем “Google Sheets API”

![17](https://user-images.githubusercontent.com/106258306/195997055-06a6bb2b-0ae2-407a-8ce9-dbeedd4f4106.png)


- Сохраним изменения. Далее перейдём в таблицу и настроем доступ. Зайдем в настройки доступа и позволим редактировать таблицу всем, у кого есть ссылка. Для этого во вкладке общий доступ выберем роль редактор.

![18](https://user-images.githubusercontent.com/106258306/195997064-7d5c2528-9ff2-49bf-abdb-d471373403e3.png)


- Далее перейдём в Unity и создадим новый проект с 3D сценой. После этого скачаем в папку Assets файлы с скриптами и звуковыми файлами, которые прилагаются вместе с отчётом.

- Создадим новый пустой объект и добавим в него компонент звуковой компонент(Add component – Audio Source). После этого создадим новый скрипт в импортированной папке Scripts и назовём его New Behaviour. Присоединим его к новому объекту перетягиванием скрипта на объект в меню, слева от сцены. Откроем скрипт и редактируем его

- ![1](https://user-images.githubusercontent.com/106258306/195997070-c2aa793d-105d-471f-a2ee-a21e739d1d16.png)

```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.Networking;
using SimpleJSON;

public class NewBehaviourScript : MonoBehaviour
{
    public AudioClip goodSpeak;
    public AudioClip normalSpeak;
    public AudioClip badSpeak;
    private AudioSource selectAudio;
    private Dictionary<string,float> dataSet = new Dictionary<string, float>();
    private bool statusStart = false;
    private int i = 1;

    void Start()
    {
        StartCoroutine(GoogleSheets());
    }

    void Update()
    {

    }

    IEnumerator GoogleSheets()
    {
        UnityWebRequest currentResp = UnityWebRequest.Get("https://sheets.googleapis.com/v4/spreadsheets/1fFvxyTIB-vN5k29u4QPb3kRnW0ApnT392QfKIxw5WNo/values/Лист1?key=AIzaSyBTVNBSLOmqUTxwlewqFuk2hqwX-dgBo4A");
        yield return currentResp.SendWebRequest();
        string rawResp = currentResp.downloadHandler.text;
        var rawJson = JSON.Parse(rawResp);
        foreach (var itemRawJson in rawJson["values"])
        {
            var parseJson = JSON.Parse(itemRawJson.ToString());
            var selectRow = parseJson[0].AsStringList;
            dataSet.Add(("Mon_" + selectRow[0]), float.Parse(selectRow[2]));
        }
	Debug.Log(dataSet["Mon_1"]);
    }
}
```
 
- Подключим необходимые библиотеки , такие как:
	-UnityEngine
	-UnityEngine.Networking
	-SimpleJSON
(ВНИМЕНИЕ!
 Для работы этих библиотек необходимо установить .NET Framework 4.7.1)
Наследуем наш скрипт от MonoBehavior. Создадим заготовки для звуковых файлов с названиями:
	-goodSpeak
	-normalSpeak
	-badSpeak
	-selectAudio
Реализуем скачивание данных с GoogleSheets и запись их в словарь. Сделаем вывод данных в Debug.log
После перейдём в Unity и запустим нашу сцену. В консоли появится надпись. Это будет означать, что наш скрипт успешно выполнен.

![3](https://user-images.githubusercontent.com/106258306/195997085-3dfda920-2f04-47a0-8b2f-a7d92152ffae.png)


- Уберём вывод первого элемента в консоль. Реализуем вывод элементов GoogleSheets в функции Update.

```c#
void Update()
    {
        if(dataSet["Mon_" + i.ToString()] <= 10 & statusStart == false & i != dataSet.Count)
        {
            StartCoroutine(PlayerSelectAudioGood());
            Debug.Log(dataSet["Mon_" + i.ToString()]);
        }

        if(dataSet["Mon_" + i.ToString()] > 10 & dataSet["Mon_" + i.ToString()] < 100 & statusStart == false & i != dataSet.Count)
        {
            StartCoroutine(PlayerSelectAudioNormal());
            Debug.Log(dataSet["Mon_" + i.ToString()]);
        }

        if(dataSet["Mon_" + i.ToString()] >= 100 & statusStart == false & i != dataSet.Count)
        {
            StartCoroutine(PlayerSelectAudioBad());
            Debug.Log(dataSet["Mon_" + i.ToString()]);
        }
    }
 ```

- Создадим воспроизведение звуковых эффектов. Для этого создадим методы, которые будут вызываться во время вывода элементов в консоль. В Unity уберём авто воспроизведение(Play on awake) и подключим звуковые файлы, которые мы установили ранее.

![5](https://user-images.githubusercontent.com/106258306/195997089-36f22778-74a1-416b-9699-47b27b593924.png)
![6](https://user-images.githubusercontent.com/106258306/195997098-fe6239b6-a12a-4116-ac3c-27cd153ba53b.png)


- Запустим программу в Unity. Теперь будет выводиться звук в зависимости от того, какое число мы передали в словарь из GoogleSheets

Вывод: Я научился использовать API из google console для работы с GoogleSheets и работать в связке Python - Google Sheets - Unity.
Весь код, использованный в отчёте можно найти в репозитории, вместе с отчётом.
