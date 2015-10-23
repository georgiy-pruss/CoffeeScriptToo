# CoffeeScriptToo
My own fork of CoffeeScript - with some bells and whistles

<pre>
+ Literals with underscores: 0xFFFF_FFFF -- done;
- Pi, date/time literals etc - maybe;
- special cases for [m..n]:
  - [1..n] -- translate to i to n i.e. i=1;i&lt;N;++i,
  - [...n] -- 0 to n exclusive, i=0;i&lt;n;++i (same [..n], [0..n]),
  - [n...] -- n downto 1 (same [n...0],[n..1]),
  - [m..n by -1] -- i=m;i>=n;--i ('by' already in for: [m..n] by k),
  - [m..n by k] ??? arrays;
- foo'abc' should be parsed! it's good for J, must be good here too;
- unary // and %% as floor and frac (= x//1 and x%%1);
- |x as Math.abs(x), maybe something for x.length, etc etc :)
- "abc"*5 and [1,2,3]$10... others from J? we'll see;
- [5 6 7 8] or even 5 6 7 8... [[1 0 0][0 1 0][0 0 1]];
- Ambiguous call syntax: first id must be for all stmt, others - minimum
  Really weird. sum [1..5] is indexing array or calling fn with array argument?
  Or sum[1..5] is one thing and sum [1..5] the other? Must be redone actually.
  E.g. range must be without [], just 1..5 (and 1...5).
- Variable scope rules... (BTW eval('var '+'abc'+' = '+'123') works)
- Vertical arrays, e.g.
  cities =:
    "Киев"
    "Chișineu"
    "București"
- macros from C: #define rotl(x,k,n) (((x<<k)&((1<<n)-1))|(x>>>(n-k)))
  all arguments are in () i.e. = ((((x)<<(k))&((1<<(n))-1))|((x)>>>((n)-(k))))
- ...more to follow.
</pre>
