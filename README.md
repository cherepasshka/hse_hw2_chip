Для исследования была выбрана клеточная линия DND-41 и гистоновая метка H3K9me3.

[Colab notebook](https://colab.research.google.com/drive/1PZwWRe5S7dfo6pV16b0foB6wnfe5Pssh?usp=sharing)

- [Анализ выдачи FastQC](#analysis)
  - [Реплика 1: ENCFF000AQC](#rep1)
  - [Реплика 2: ENCFF000AQB](#rep2)
  - [Контроль: ENCFF000AOG](#control)
- [Выравнивание на хромосому](#chr)
- [Диаграммы Венна](#diagr)

<a name="analysis"></a> 
# Анализ выдачи FastQC

<a name="rep1"></a> 
## Реплика 1: ENCFF000AQC
![image](https://user-images.githubusercontent.com/50082204/220176275-ebc8fe64-2114-4ef1-912e-0832094e0cc8.png)
![image](https://user-images.githubusercontent.com/50082204/220176409-6b7891e0-ebc0-4627-bfaa-118afd80c329.png)
![image](https://user-images.githubusercontent.com/50082204/220176440-8534475b-bc63-4ffa-8e28-e1ee0c30c377.png)
![image](https://user-images.githubusercontent.com/50082204/220176489-7d6feda2-6428-4664-be6b-8eb533c5fc77.png)
![image](https://user-images.githubusercontent.com/50082204/220176576-904b26a4-a7d7-40fa-b7f0-cc2180afaf22.png)

В отчете два графика помечены как непрошедшие качество (Per Tile Sequence Quality и Per sequence GC content)

Per Tile Sequence Quality: основное полотно синего цвета, а красных полос очень мало, поэтому я думаю качество для tiles удовлетворительное.

Per sequence GC content: видим, что основной пик немного смещен, что говорит о небольшом загрязнении.

Я решила не делать фильтрацию и подрезания для чтений.

<a name="rep2"></a> 
## Реплика 2: ENCFF000AQB
![image](https://user-images.githubusercontent.com/50082204/220175147-9e4bb47a-ba53-4ae9-bc78-b0d4210b45c2.png)
![image](https://user-images.githubusercontent.com/50082204/220175218-8618d908-582f-43ff-9b4a-38f65d83b311.png)
![image](https://user-images.githubusercontent.com/50082204/220175338-cb451da4-6400-4eb5-8d7c-be04aa24ae71.png)
![image](https://user-images.githubusercontent.com/50082204/220175368-b85f5b28-a261-4c86-a94e-98d98e09e838.png)
![image](https://user-images.githubusercontent.com/50082204/220175563-8703a52e-5516-4d00-ac3b-6154a8de93f5.png)

В отчете только один график отмечен как непрошедший качество (Per Tile Sequence Quality).
Мне кажется, что крастных полосок довольно мало и основное полотно синего цвета, что свидетельствует о хорошем качестве для tiles. 
Поэтому я решила не делать фильтрацию и подрезания для чтений.

<a name="control"></a> 
## Контроль: ENCFF000AOG
![image](https://user-images.githubusercontent.com/50082204/220177696-e546ceb0-fbd3-4fbe-a199-8f8c6db5fe0d.png)
![image](https://user-images.githubusercontent.com/50082204/220177782-2f4cb84f-cd14-40aa-a1ec-152271cdba8d.png)
![image](https://user-images.githubusercontent.com/50082204/220177811-c988ce14-c543-4992-8189-fe89c04e1728.png)
![image](https://user-images.githubusercontent.com/50082204/220177841-4497f901-0819-47a5-bdd6-9a40562852b0.png)
![image](https://user-images.githubusercontent.com/50082204/220177876-e40cf59b-ada4-4750-a0b6-d49251632615.png)

В отчете вообще нет графиков, непрошедших качество.

Основной график, показывающий качество ридов, - Per base sequence quality показывает хорошие результаты качества. 
Я решила не использовать дополнительную обработку, хотя для 1й реплики можно было бы попытаться улучшить GC распределение, 
но мне не кажется, что это сильно что-то изменит.

<a name="chr"></a> 
## Выравнивание на хромосому 14

|                       |**всего ридов**|**выровненные 0 раз**|**выровненные ровно 1 раз**|**выровненные более 1 раза**|
|-----------------------|---------------|---------------------|---------------------------|----------------------------|
|ENCFF000AQC (реплика 1)|   34325063    |  27202966 (79.25%)  |      1563021 (4.55%)      |       5559076 (16.20%)     |
|ENCFF000AQB (реплика 2)|   36077917    |  27007620 (74.86%)  |      1781819 (4.94%)      |       7288478 (20.20%)     |
|ENCFF000AOG (контроль) |   41060673    |  33405977 (81.36%)  |      1902228 (4.63%)      |       5752468 (14.01%)     |

Процент уникальных выравниваний получился в диапазоне 4.5% - 5%, что, составляет приблизительный размер хромосомы, 
на которую происходило выравнивание. 

<a name="diagr"></a> 
## Диаграммы Венна

#### ENCFF000AQC (реплика 1)
![image](https://user-images.githubusercontent.com/50082204/220190379-425368f0-7c1c-43a7-91bb-577d74bed2fb.png)
![image](https://user-images.githubusercontent.com/50082204/220190406-30b9cf91-7515-40aa-af1d-4f4017dc6d62.png)

#### ENCFF000AQB (реплика 2)
![image](https://user-images.githubusercontent.com/50082204/220190286-2379f351-821e-4e40-9e12-6aeb8a85a828.png)
![image](https://user-images.githubusercontent.com/50082204/220190332-ed70a08b-cc23-4f8d-882f-4f51f37ae540.png)

Результат пересечения получился неплохой, учитывая то, что файл для сравнения в целом небольшой. 
