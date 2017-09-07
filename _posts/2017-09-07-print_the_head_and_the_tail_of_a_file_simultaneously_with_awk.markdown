---
title: "Print the head and the tail of a file simultaneously with awk"
layout: default
date: 2017-09-07
tags:
- awk
---

# Print the head and the tail of a file simultaneously with awk

	function headtail {
		# print the head and the tail
		awk '{i+=1; data[i]=$0} END{for (j=1; j<=10; j++){print data[j]}; print "---"; for (k=i-10;k<=i;k++){print data[k]}}' $1
	}
