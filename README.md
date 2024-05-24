# conveyor-belt-and-computer-vision
A model for detecting conveyor belt defects using computer vision

<p align="center">
    <img src="https://github.com/PavelKrinitsin/conveyor-belt-and-computer-vision/blob/main/1.jpg" width="300">
</p>

## Description
Поточно транспортное оборудование составляет большую долю все промышленных объектов на металлургических предприятиях. От его работоспособности зависит непрерываность подачи сырья для дальнейшей обработки и перемещение готовой продукции на следующие этапы производства или на отгрузку. Конвейеры с транспортерной лентой - резиновой или полимерной, в свою очередь составляют большую часть всего конвейерного оборудования. Перемещаемые грузы могут быть различны как по фракционному/химическому составу так и по физическим характеристикам: высокая/низкая температура, влажность и другие. Существуют также и различия в условиях эксплуатации, связанных с характером выполняемых ими задач: непрерывная эксплуатация или работа по графику, постоянная загрузка или периодически меняющаяся в процессе работы конвейера. Таким образом возникают несколько проблем, связанных с обеспечением надежной работы данного оборудования: невозможность установить нормативный срок эксплуатации для транспортреных лент для всего оборудования - он может быть различным даже в пределах одного цеха для аналогичного оборудования, невозможность или недостаточное качество диагностики технического состояния ленты в процессе эксплуатации: лента находится под материалом в период осмотра ее состояния (особенно актуально когда оборудования много и возможности его одновременно остановить не представляется возможным). Различны и характеры повреждений ленты - какие то требуют незамедлительного устранения, другие являются индикатором для планирования ремонта в прогнозируемые сроки.
Все это и другие факторы (например человеческий фактор - влияющий на качество самой диагностики: просмотрел, не обратил внимания и т.д.) приводят к необходимости изучения применимости алгоритмов цифрового зрения для оценки состояния данного оборудования без привлечения ремонтного персонала.

Основные этапы данного исследования:
1. Создание собственного набор изображений с дефектами лент с помощью захвата изображений из видеопотока;
2. Разметка полученных изображений в программе CVAT различными способами (2 точки, 4 точки, полигональные линии);
3. Создание на основе данных о разметке датасетов изображений;
4. Разработка алгоритмов детекторов объектов на изображениях:
   4.1 Алгоритм простого классификатора изображений по типу есть дефект/нет дефекта и если есть то какой;
   4.2 Алгоритм детектора дефектов на изображениях с помощью предобученной нейросети REZNET50 с помощью отрисовки объектов прямоугольниками;
   4.3 Алгоритм обучения детектора на выделенных полигональными линиями объектах изображений.
5. Заключение о достигнутых результатах.


Flow transportation equipment accounts for a large share of all industrial facilities at metallurgical plants. The continuity of raw material supply for further processing and the movement of finished products to the next stages of production or for shipment depends on its performance. Belt conveyors, whether rubber or polymer, in turn, make up a significant part of all conveyor equipment. The transported loads can vary both in terms of fractional/chemical composition and physical characteristics: high/low temperature, humidity, and others. There are also differences in operating conditions related to the nature of the tasks performed by them: continuous operation or scheduled work, constant load or periodically changing during conveyor operation. Thus, several problems arise related to ensuring the reliable operation of this equipment: the inability to establish the standard service life for conveyor belts for all equipment - it may vary even within one workshop for similar equipment, the impossibility or insufficient quality of diagnosing the technical condition of the belt during operation: the belt is under material during the inspection of its condition (especially relevant when there is a lot of equipment and it is not possible to stop it simultaneously). The types of belt damage also vary - some require immediate elimination, while others serve as indicators for repair planning within predictable time frames. All these factors and others (for example, the human factor - affecting the quality of diagnosis: overlooked, not paid attention to, etc.) lead to the need to study the applicability of computer vision algorithms to assess the condition of this equipment without involving repair personnel.

The main stages of this research are as follows:
1. Creating a proprietary set of images with belt defects by capturing images from a video stream;
2. Labeling the obtained images in the CVAT program using various methods (2 points, 4 points, polygonal lines);
3. Creating image datasets based on labeling data;
4. Developing object detectors algorithms in images:
   4.1 Algorithm for a simple image classifier by type of defect/no defect and if there is a defect, what type it is;
   4.2 Algorithm for defect detection in images using the pretrained neural network REZNET50 by drawing objects with rectangles;
   4.3 Algorithm for training a detector on objects outlined with polygonal lines in images.
5. Conclusion on the achieved results.
___

## Results
Предварительные результаты исследования:
1.  Конвейерное оборудование обычно установлено и эксплуатируется в местах с недостаточным освещением (запыленность, невозможность установки мощных источников освещения и пр.) поэтому для создания изображений достаточного качества необходимо снимать видеопоток с частотой кдоров не менее 250к/сек. Что вызывает необходимость применения камер с высокой скоростью записи и достаточной степенью пылевлагозащиты;
2.  Размеченный датасет изображений участков транспортерных лент после обучения алгоритма классификации показывает хорошие результаты с точки зрения выявления дефектов на ленте. Что может быть достаточным для направления специалистов для более детального изучения состояния оборудования.
3.  Алгоритмы детекции дефектов на ленте, обученные с помощью прямоугольных областей, предоставляют гораздо больше информации о самом дефекте: его размер, место расположения, характер повреждения. Полученную таким образом информацию можно корвертировать в предсказания по сроку службы ленты, примерно оценив площади повреждения ленты, зафиксировать факт воздействия на нее высокой температуры или химических реагентов.
4.  Алгоритмы детекции дефектов, основанные на анализе полигональных линий, дают большее представление о площади повреждения, более точно фиксируют поврежденные области. Их применение целесообразно для особо ответсвенно оборудования, безаварийная работа которого влияет на работоспособность всей технологической цепочки производства.
Таким образом было изучены различные способы оценки технического состояния такого важного оборудования как ленточные конвейера. Предложены варианты выявления дефектов для оборудования различной группы важности.

1. Conveyor equipment is usually installed and operated in poorly lit areas (dusty environments, inability to install powerful lighting sources, etc.), so to create images of sufficient quality, it is necessary to capture a video stream with a frame rate of no less than 250 frames per second. This necessitates the use of cameras with high recording speeds and adequate dust and moisture protection.
2. A labeled dataset of images of conveyor belt sections after training the classification algorithm shows good results in terms of detecting defects on the belt. This may be sufficient to direct specialists for a more detailed study of the equipment's condition.
3. Defect detection algorithms on the belt, trained using rectangular areas, provide much more information about the defect itself: its size, location, and nature of damage. The information obtained in this way can be used to predict the service life of the belt, roughly estimate the damaged area of the belt, and record the effects of high temperatures or chemical agents on it.
4. Defect detection algorithms based on the analysis of polygonal lines provide a better understanding of the damaged area, more accurately identify the damaged areas. Their application is appropriate for particularly critical equipment, the uninterrupted operation of which affects the performance of the entire production technology chain.
In this way, various methods of assessing the technical condition of such important equipment as conveyor belts have been studied. Options for detecting defects for equipment of varying importance have been proposed.


___

## Tags
Python, Сomputer vision, Detection tasks
