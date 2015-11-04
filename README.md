# CoffeeScriptToo
My own fork of CoffeeScript - with some bells and whistles

<pre>
+ Literals with underscores: 0xFFFF_FFFF -- done;
- Pi, date/time literals etc - maybe; 2p1 2015.2.28_15:30_+2
- special cases for [m..n]:
  - [1..n] -- translate to i to n i.e. i=1;i&lt;N;++i,
  - [...n] -- 0 to n exclusive, i=0;i&lt;n;++i (same [..n], [0..n]),
  - [n...] -- n downto 1 (same [n...0],[n..1]),
  - [m..n by -1] -- i=m;i>=n;--i ('by' already in for: [m..n] by k),
  - [m..n by k] ??? arrays;
- binary ops (e.g.)
  ~+  append     [1,2]~+3 = [1,2,3] or rather x.push(y)
  ~&  join       [1,2,3]~&'.' = '1.2.3'
  ~|  split      'a,bb,,c'~|',' = ['a','bb','','c']
  ~/  take       first y (last -y) ... like expand/shrink... TODO yet
  ~\  drop       without first y (without last -y)
  ~@  select     'abcde'~@[2,1,4] == 'bad' TODO -- see J
  ~:  filter     'abcde'~:[0,1,2,0,0] = 'bcc' or bool array, or function
  ~*  repeat     'abc'~*3 = 'abcabcabc'  [1,2]~*3 = [1,2,1,2,1,2]
  ~#  reshape    'abc'~#5 = 'abcab'  like x$y in J
  ~%  replace    'abc'~%'b','123' = 'a123c' -- x.replace(y,z[,y2,z2]...)
  ~>  expand     'abc'~>2 = 'abc'  'abc'~>4 = 'abc '  also negative = left
  ~<  shrink     'abc'~<2 = 'ab'   'abc'~<4 = 'abc'   also negative = left
  ~^  starts     'abc'~^'ab'
  ~$  ends       'abc'~$'bc'
  ~?  contains   'abc'~?'b'  [1,2,3]~?2  {1:2,3:4}~?3
  ~=  match      'abc'~=/^abc$/
  ~~  approx     1~~(1+1e-15) or compare strings ignoring case?...
  ~-  diff? encode/decode UTF8? ...
- unary ops
  &   length     &'abc' = 3     &[1,2,3,4] = 4
  |   abs        |-3 = 3
  //  floor      //x (= x//1)
  %%  frac       %%x (= x%%1)
  !   new        postfix:  Date! Date!('2015.1.1 0:00')
- [5 6 7 8] or even 5 6 7 8... [[1 0 0][0 1 0][0 0 1]];
- foo'abc' should be parsed! it's good for J, must be good here too;
  foo [1,2], foo[1,2] ? foo {1:2}, foo{1:2} ...
- Ambiguous call syntax: first id must be for all stmt, others - minimum
  Really weird. sum [1..5] is indexing array or calling fn with array argument?
  Or sum[1..5] is one thing and sum [1..5] the other? Must be redone actually.
  E.g. range must be without [], just 1..5 (and 1...5).
- Since "(nearly) everything is an expression", why not to use parentheses in
  one-liners instead of braces?
  if A then (if B then (C(); D()) else (for x in R then (K(); L()); M()); P()) else Q()
- Variable scope rules... (BTW eval('var '+'abc'+' = '+'123') works)
- BUT! It can be solved:
  a = d = 1
  f = ->
    `var a,b,c`
    a = 2; b = 3
    return b
  alert "#{a},#{f()}"
      ↓
  var a, d, f;
  a = d = 1;
  f = function() {
    var a,b,c; // <------ inserted
    var b;     // <------ double declaration is fine!
    a = 2;
    b = 3;
    return b;
  };
  alert(a + "," + (f()));
- Vertical arrays, e.g.
  cities = ::         # or maybe << >> ** || []
    "Киев"
    "Chișineu"
    "București"
- macros from C: #define rotl(x,k,n) (((x<<k)&((1<<n)-1))|(x>>>(n-k)))
  all arguments are in () i.e. = ((((x)<<(k))&((1<<(n))-1))|((x)>>>((n)-(k))))
- <span color='red'>REALLY????!!!!!</span> -->  
  if 3 in [1..1000]
    foo()
      ↓
  var i, results,
    indexOf = [].indexOf || function(item) { for (var i = 0,
        l = this.length; i < l; i++) { if (i in this && this[i] === item) return i; } return -1; };
  if (indexOf.call((function() {
    results = [];
    for (i = 1; i <= 1000; i++){ results.push(i); }
    return results;
  }).apply(this), 3) >= 0) {
    foo();
  }
- new X, new X(args) --> X!, X!(args) - just an idea, to get rid of going left
- OMG this bug (unmatched unindentations) is still there too!
  https://github.com/satyr/coco/wiki/wtfcs
  multiple for's in comprehension is right though
- ...more to follow.
</pre>
