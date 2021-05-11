Map: divide in degree of inputs, generate intermediates: {key, value}
Reduce: divide in degree of intermediates, deal with {key, value}s with same key
(pairs with same key reduce to one pair, that's reduce means)

map(struct input):
	generate({input.GetKey(), input.GetValue()})

reduce(string key, vector<T> value_vec):
	T value_sum;
	for (auto value : value_vec) value_sum.add(value);
	generate({key, value_sum})

common examples: word count, distribute grep, distribute sort, inverted index

usage of system: users submit jobs to scheduling system(one job consists of multiple tasks)

M mapper + R reducer + 1 master
master mantain table of M * R stats
usually input_size / M = 64M
