1. Переменной c будет присвоено значение "a+b" т.к. обращение к переменным не идет, это просто строковое значение
   Переменной d будет присвоено значение "1+2" т.к. из-за знака "+" переменные a и b интерпретируются как строки
   Переменной e будет присвоено значение "3" т.к.  $(( )) указывает что это арифметическая операция

2. 
	1. Нет закрывающей скобки в операторе while

while ((1==1))
  do
  curl https://localhost:4757
  if (($? != 0))
  then
    date >> curl.log
  fi
done

	2.  Заменить оператор добавления текста на замену текста

while ((1==1))
  do
  curl https://localhost:4757
  if (($? != 0))
  then
    date > curl.log
  fi
done

	3. Добавить выход по успешному выполнению curl

while ((1==1))
  do
  curl https://localhost:4757
  if (($? != 0))
  then
    date >> curl.log
  else
    break
  fi
done

3.
	 Првоерка доступности по 80 порту

#!/bin/bash

logfile="out.log"
port=80
hosts=("192.168.0.1" "173.194.222.113" "87.250.250.242")

for i in {0..4}
do
  for host in ${hosts[@]}
  do
    nc -z -w1 $host $port
    rc=$?
    if (($rc == 0))
    then
      echo `date` $host OK >> $logfile
    else
      echo `date` $host ERROR >> $logfile
    fi
  done
done


4.
	Если любой из узлов недоступен - IP этого узла пишется в файл error, скрипт прерывается

#!/bin/bash

logfile="out.log"
errfile="error"
port=80
hosts=("192.168.0.1" "173.194.222.113" "87.250.250.242")

for i in {0..4}
do
  for host in ${hosts[@]}
  do
    nc -z -w1 $host $port
    rc=$?
    if (($rc == 0))
    then
      echo `date` $host OK >> $logfile
    else
      echo `date` $host ERROR >> $logfile
      echo $host >> $errfile
      exit 1
    fi
  done
done



