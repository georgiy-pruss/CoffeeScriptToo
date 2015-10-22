# CoffeeScriptToo
My own fork of CoffeeScript - with some bells and whistles

<pre>
+ Literals with underscores: 0xFFFF_FFFF -- done;
- Pi, date/time literals etc - maybe;
- special cases for [m..n]:
  - [1..n] -- translate to i to n i.e. i=1;i&lt;N;++i,
  - [...n] -- 0 to n exclusive, i=0;i&lt;n;++i (same [..n], [0..n]),
  - [n...] -- n downto 1 (same [n...0],[n..1]),
  - [m..n by -1] -- i=m;i>=n;--i,
  - [m..n by k] -- general case, like now, but with step k;
- foo'abc' should be parsed! it's good for J, must be good here too;
- unary // and %% as floor and frac (= x//1 and x%%1);
- |x as Math.abs(x), maybe something for x.length, etc etc :)
- "abc"*5 and [1,2,3]$10... others from J? we'll see;
- [5 6 7 8] or even 5 6 7 8... [[1 0 0][0 1 0][0 0 1]];
- Ambiguous call syntax: first id must be for all stmt, others - minimum
- Variable scope rules...
- ...more to follow.
</pre>
