Hadoop - Quick Guide

https://www.tutorialspoint.com/hadoop/hadoop_quick_guide.htm

Example Scenario

Given below is the data regarding the electrical consumption of an organization. 
It contains the monthly electrical consumption and the annual average for various years.

Jan 	Feb 	Mar 	Apr 	May 	Jun 	Jul 	Aug 	Sep 	Oct 	Nov 	Dec 	Avg
1979 	23 	23 	2 	43 	24 	25 	26 	26 	26 	26 	25 	26 	25
1980 	26 	27 	28 	28 	28 	30 	31 	31 	31 	30 	30 	30 	29
1981 	31 	32 	32 	32 	33 	34 	35 	36 	36 	34 	34 	34 	34
1984 	39 	38 	39 	39 	39 	41 	42 	43 	40 	39 	38 	38 	40
1985 	38 	39 	39 	39 	39 	41 	41 	41 	00 	40 	39 	39 	45


Input Data

The above data is saved as sample.txt and given as input. The input file looks as shown below.

1979   23   23   2   43   24   25   26   26   26   26   25   26  25 
1980   26   27   28  28   28   30   31   31   31   30   30   30  29 
1981   31   32   32  32   33   34   35   36   36   34   34   34  34 
1984   39   38   39  39   39   41   42   43   40   39   38   38  40 
1985   38   39   39  39   39   41   41   41   00   40   39   39  45 
<<< NO EMPTY LINE HERE

mkdir units
javac -classpath hadoop-core-1.2.1.jar -d units ProcessUnits.java 
jar -cvf units.jar -C units/ .
hadoop fs -mkdir input_dir
hadoop fs -put /home/hadoop/sample.txt input_dir
hadoop fs -ls input_dir/
hadoop jar units.jar hadoop.ProcessUnits input_dir output_dir

hadoop fs -ls output_dir/
hadoop fs -cat output_dir/part-00000 

Below is the output generated by the MapReduce program.

1981    34 
1984    40 
1985    45 
