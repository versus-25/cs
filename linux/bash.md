	for var in list
	do
		#actions
	done

	if [[ predict ]]
	then
		#action
	elif  #optional
	then #optional
		#action
	else #optional
	fi  

	case var in
	value1)
		#action1 
		;;
	value2)
		#action2
		;; *)
		#action else
	esac 
	Условия для строк -z пустая
	-n негустая
	== равна
	!= неравна  Условия для чисел -eq равно
	-ne не равно
	-lt меньше
	-le меньше или равно
	-gt больше
	-ge больше или равно  Условия для путей
	-e путь существует
	-f это файл
	-d это директория
	-s размер файла
	-x файл исполняемый

	! Не
	&& и
	|| или  арифметические let «c = 2 + 1»
	a=`echo «test»`
	files=`ls ~`

	$? узнать код завершения программы
	rm test
	echo $? 

	Функция ()
	{
		Аргументы - 	$1 $2  и тд
		глобальный переменные 
		var1=4
		локальные
		local var21=9
	}

lsof -u cindy  
-u юзер  
-U сокет
-с - опция названия файла, который держит открытыми процессы lsof -cpython - все процессы, которые запущены от python  
lsof -cpython -c^python2.7 исключить python2.7  
lsof +d /usr/bin файлы открытые в директории, а не в поддиректории
lsof -p 1 - все файлы, открытые процессом 1  

