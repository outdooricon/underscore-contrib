Documentation should use [Journo](https://github.com/jashkenas/journo) formats and standards.

### Array concatenation via `_.cat`

Signature: `_.cat(... arrays:Array ...)`

The `_.cat` function provides a way to concatenate zero or more heterogeneous arrays into one.

    _.cat();                    // 0-args
    //=> []
    
    _.cat([]);                  // 1-arg, empty array
    //=> []
    
    _.cat([1,2,3]);             // 1-arg
    //=> []
    
    _.cat([1,2,3],[4,5,6]);     // 2-args
    //=> [1,2,3,4,5,6]
    
    _.cat([1,2,3],[4,5,6],[7]); // 3+ args
    //=> [1,2,3,4,5,6,7]

Not every argument to `_.cat` needs to be an array; other types are accepted.

Signature: `_.cat(... elems:Any ...)`

    _.cat(1,[2],3,4);           // mixed args
    //=> [1,2,3,4]

The `_.cat` function will also work with the `arguments` object as if it were an array.

Signature: `_.cat(... elems:Arguments ...)`

    function f(){ return _.cat(arguments, 4,5,6); }
    
    f(1,2,3);
    //=> [1,2,3,4,5,6]

### Array construction via `_.cons`

Signature: `_.cons(head:Any, tail:Array)`

The `_.cons` function provides a way to "construct" a new array by taking some element and putting it at the front of another array.

    _.cons(0, []);
    //=> [0]
    
    _.cons(1, [2]);
    //=> [1,2]
    
    _.cons([0], [1,2,3]);
    //=> [0,1,2,3]

The `_.cons` function also can be used to create pairs if the second argument is not an array.

Signature: `_.cons(head:Any, tail:Any)`

    _.cons(1, 2);
    //=> [1,2]
    
    _.cons([1], 2);
    //=> [[1],2]

Finally, `_.cons` will operate with the `arguments` object.

Signature: `_.cons(head:Any, tail:Arguments)`

    function f() { return _.cons(0, arguments) }
    
    f(1,2,3);
    //=> [0,1,2,3]

### Array partitioning via `_.partition` and `_.partitionAll`

The `_.partition` function, by default, accepts an array and a number and splits and returns a new array representing the original array split into some number of arrays of the given size:

    _.partition([0,1,2,3], 2);
    //=> , [[0,1],[2,3]]

If the original array cannot completely fulfill the partition scheme then the array returned will drop the undersized final partition:

    _.partition([0,1,2,3,4], 2);
    //=> , [[0,1],[2,3]]

You can pass an optional third argument to `_.partition` to pad out the final array partition should it fall short.  If the value given as the third argument is *not* an array then it is repeated the needed number of times:

    _.partition([0,1,2,3,4], 3, '_');
    //=> , [[0,1,2],[3,'_','_']]

If you given an array as the optional third argument then that array is used to pad in-place as needed:

    _.partition([0,1,2,3,4], 3, ['a', 'b']);
    //=> , [[0,1,2],[3,'a','b']]

The `_.partitionAll` function is similar to `_.partition` except for the following.  First, `_.partionAll` will never drop short partitions from the end:

    _.partitionAll([0,1,2,3,4], 3);
    //=> , [[0,1,2],[3]]

Also, `_.paritionAll` takes an optional third argument signifying that paritions should be built from skipped regions:

    _.partitionAll(_.range(1), 2, 4);
    //=> [[0,1],[4,5],[8,9]]

	
### Array flattening via `_.mapcat`
	
    mapcat: function(array, fun) {
	
### Inserting elements into an array via `_.interpose`
	
    interpose: function(array, inter) {
	
### Weaving arrays together via `_.weave` and `_.interleave`
	
    weave: function(/* args */) {
    interleave: _.weave,
	
### Building arrays from repeated value with `_.repeat` and `_.cycle`

Signature: `_.repeat(t:Integer, value:Any)`

The `_.repeat` function takes an integer value used to build an array of that size containing the value given:

    _.repeat(5, 'a');
    //=> ['a','a','a','a','a']

The `_.cycle` function takes an integer value used to build an array of that size containing the number of iterations through the given array, strung end-to-end as many times as needed.  An example is probably more instructive:

    _.cycle(5, [1,2,3]);
    //=> [1,2,3,1,2]
	
### Splitting an array with `_.splitAt`
	
    splitAt: function(array, index) {
	
### Building an array until a condition fails via `_.iterateUntil`
	
    iterateUntil: function(doit, checkit, seed) {
	
### Taking skipped elements from an array with `_.takeSkipping`
	
    takeSkipping: function(array, n) {
	
### Storing every stage of a reduce with `_.reductions`
	
    reductions: function(array, fun, init) {
	
### Taking elements from an array based on properties of their keys
	
    keepIndexed: function(array, pred) {

