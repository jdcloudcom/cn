#  索引操作   
## 创建非唯一索引
```
CREATE INDEX person_num ON person (number);
或者
ALTER TABLE person ADD INDEX person_num (number)；
```

## 创建唯一索引
```
CREATE UNIQUE INDEX person_num ON person (number);
或者
ALTER TABLE person ADD UNIQUE person_num  on (number);
```

## 查看表内所有索引
```
SHOW INDEX from person;
```
 
## 删除索引
```
DROP INDEX person_num ON person;
ALTER TABLE person DROP INDEX person_num;
```