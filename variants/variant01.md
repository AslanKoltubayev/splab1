### Variant 01
Output the following information:

* Top 10 referers as per the total number of bytes downloaded by them
* Total number of bytes downloaded for each of the them
* Percentage of bytes downloaded by each of them

Sample output:

```
1. http://www.example.org/example/When/200x/2006/09/25/ - 3100 - 74%                                                    
2. http://www.example.org/example/ - 1000 - 24%                
3. http://www.example.org/example/genx/docs/Guide.html -  91 - 2%                                                        
```
#! /bin/bash  
lines=$(cut -f10,11 -d" " log.txt | grep -v '"-"' 	| sort -t" " -k1   | sort --reverse -k1 -n |wc -l);
echo $lines;

liness=$(cut -f10,11 -d" " log.txt | grep -v '"-"' 	| sort -t" " -k1   | sort --reverse -k1 -n | head);

for i in  $liness;
do 

	if [[ $i =~ ^[0-9]+$ ]]; then
	printf "$i -  0$(echo "scale=1; $i / $lines" | bc)%%" ;
  	else printf " - $i \n"; fi 
done
