
|Bit offset	7 .. 4 (byte 0)|	3 .. 0 (byte 0) |	15 .. 8 (byte 1) |	23..16 (byte 2)	| ....|
|--|--|--|--|--|
Single	0	size (0..7)	Data A	Data B	Data C
First	1	size (8..4095)	Data A	Data B
Consecutive	2	index (0..15)	Data A	Data B	Data C
Flow	3	FC flag (0,1,2)	Block size	ST	
