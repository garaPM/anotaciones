# diag

```mermaid
graph TD
A(VNote)-->B[Qué es];
     A-->C[Para qué se usa];
     A-->D[Funcionalidades];
     A-->E[Como instalarlo];
     A-->F(Conclusión);
```
 - - -
 
```mermaid
graph TD;
A-->B;
A-->C;
B-->D;
C-->D;
```
- - -

```flowchart
st=>start: Start:>http://www.google.com[blank]
e=>end:>http://www.google.com
op1=>operation: My Operation
sub1=>subroutine: My Subroutine
cond=>condition: Yes
or No?:>http://www.google.com
io=>inputoutput: catch something...

st->op1->cond
cond(yes)->io->e
cond(no)->sub1(right)->op1
```