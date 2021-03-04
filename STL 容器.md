# STL 容器

## 非关联式



## 关联式

### 无序

`unordered_map`

<table>
<caption>
unordered_map类模板成员方法</caption>
<tbody>
<tr>
<th>
成员方法</th>
<th>
功能</th>
</tr>
<tr>
<td>
begin()</td>
<td>
返回指向容器中第一个键值对的正向迭代器。</td>
</tr>
<tr>
<td>
end()&nbsp;</td>
<td>
返回指向容器中最后一个键值对之后位置的正向迭代器。</td>
</tr>
<tr>
<td>
cbegin()</td>
<td>
和 begin() 功能相同，只不过在其基础上增加了 const 属性，即该方法返回的迭代器不能用于修改容器内存储的键值对。</td>
</tr>
<tr>
<td>
cend()</td>
<td>
和 end() 功能相同，只不过在其基础上，增加了 const 属性，即该方法返回的迭代器不能用于修改容器内存储的键值对。</td>
</tr>
<tr>
<td>
empty()</td>
<td>
若容器为空，则返回 true；否则 false。</td>
</tr>
<tr>
<td>
size()</td>
<td>
返回当前容器中存有键值对的个数。</td>
</tr>
<tr>
<td>
max_size()</td>
<td>
返回容器所能容纳键值对的最大个数，不同的操作系统，其返回值亦不相同。</td>
</tr>
<tr>
<td>
operator[key]</td>
<td>
该模板类中重载了 [] 运算符，其功能是可以向访问数组中元素那样，只要给定某个键值对的键 key，就可以获取该键对应的值。注意，如果当前容器中没有以 key 为键的键值对，则其会使用该键向当前容器中插入一个新键值对。</td>
</tr>
<tr>
<td>
at(key)</td>
<td>
返回容器中存储的键 key 对应的值，如果 key 不存在，则会抛出 out_of_range 异常。&nbsp;</td>
</tr>
<tr>
<td>
find(key)</td>
<td>
查找以 key 为键的键值对，如果找到，则返回一个指向该键值对的正向迭代器；反之，则返回一个指向容器中最后一个键值对之后位置的迭代器（如果 end() 方法返回的迭代器）。</td>
</tr>
<tr>
<td>
count(key)</td>
<td>
在容器中查找以 key 键的键值对的个数。</td>
</tr>
<tr>
<td>
equal_range(key)</td>
<td>
返回一个 pair 对象，其包含 2 个迭代器，用于表明当前容器中键为 key 的键值对所在的范围。</td>
</tr>
<tr>
<td>
emplace()</td>
<td>
向容器中添加新键值对，效率比 insert() 方法高。</td>
</tr>
<tr>
<td>
emplace_hint()</td>
<td>
向容器中添加新键值对，效率比 insert() 方法高。</td>
</tr>
<tr>
<td>
insert()&nbsp;</td>
<td>
向容器中添加新键值对。</td>
</tr>
<tr>
<td>
erase()</td>
<td>
删除指定键值对。</td>
</tr>
<tr>
<td>
clear()&nbsp;</td>
<td>
清空容器，即删除容器中存储的所有键值对。</td>
</tr>
<tr>
<td>
swap()</td>
<td>
交换 2 个 unordered_map 容器存储的键值对，前提是必须保证这 2 个容器的类型完全相等。</td>
</tr>
<tr>
<td>
bucket_count()</td>
<td>
返回当前容器底层存储键值对时，使用桶（一个线性链表代表一个桶）的数量。</td>
</tr>
<tr>
<td>
max_bucket_count()</td>
<td>
返回当前系统中，unordered_map 容器底层最多可以使用多少桶。</td>
</tr>
<tr>
<td>
bucket_size(n)</td>
<td>
返回第 n 个桶中存储键值对的数量。</td>
</tr>
<tr>
<td>
bucket(key)</td>
<td>
返回以 key 为键的键值对所在桶的编号。</td>
</tr>
<tr>
<td>
load_factor()</td>
<td>
返回 unordered_map 容器中当前的负载因子。负载因子，指的是的当前容器中存储键值对的数量（size()）和使用桶数（bucket_count()）的比值，即 load_factor() = size() / bucket_count()。</td>
</tr>
<tr>
<td>
max_load_factor()</td>
<td>
返回或者设置当前 unordered_map 容器的负载因子。</td>
</tr>
<tr>
<td>
rehash(n)</td>
<td>
将当前容器底层使用桶的数量设置为 n。</td>
</tr>
<tr>
<td>
reserve()</td>
<td>
将存储桶的数量（也就是 bucket_count() 方法的返回值）设置为至少容纳count个元（不超过最大负载因子）所需的数量，并重新整理容器。</td>
</tr>
<tr>
<td>
hash_function()</td>
<td>
返回当前容器使用的哈希函数对象。</td>
</tr>
</tbody>
</table>

