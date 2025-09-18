> I only got through question 4 - i finished through question 2 in class but only had the brainpower for 3&4.

## Question 1
*list the names of all female assistants*

*predicates*

*tuple*
$\{\text{ S.fName  S.lName  }| \text{ Staff(S)} \land \text{ S.sex = 'F' }  \land \text{ S.position = 'Assistant'}\}$

*domain*
$$
\begin{flalign*}
\{\text{FN LN   }|
&\exists_{\text{  SNO FN LN Posn sex DOB sal BNO}} & \\
& \text{(Staff( SNO FN LN posn sex DOB sal BNO )} &\\
& \land \text{sex = 'F'} \land \text{posn = 'Assistant'})\}
\end{flalign*}
$$
## Question 2

*tuple*
$$
\begin{flalign*}
\{ \text{ S.fName S.lName  } | &\\
&\text{Staff(S)  } \exists \text{ (Branch(B)} \\
&\text{S.branchNo = B.branchNO  } \land \text{  B.city = 'London'}) \}
&\end{flalign*}
$$
*domain*
$$
\begin{flalign*}
\{ \text{fn, ln} |
&\text{ } \exists\text{ sn, fn, ln, pos, sx, dob, sal, bn, st, ct, pc} &\\
&(\text{Staff(sn, fn, ln, pos, sx, dob, sal, bn) } \land \text{ Branch(bn, st, ct, pc) } \land \text{ ct = 'London})
\end{flalign*}
$$

## Question 3
*tuple*
$$
\begin{flalign*}
\{\, S.fName,\; S.lName \mid & \\
   &Staff(S)\ \land
   \exists J \big[ Staff(J) \land
   J.fName = 'Julie' \land
   J.lName = 'Lee' \land \\
   & S.salary > J.salary \big] \,\}
\end{flalign*}
$$


*domain*
$$
\begin{flalign*}
\{\,  F,L  \mid &
   \exists P,S,D,Sal,B \;
   \exists Fj,Lj,Pj,Sj,Dj,Salj,Bj \big[ \\
   & Staff(F,L,P,S,D,Sal,B) \land
     Staff('Julie','Lee',Pj,Sj,Dj,Salj,Bj) \\
     & \land Sal > Salj \big] \,\}
\end{flalign*}
$$

## Question 4

*tuple*
$$
\begin{flalign*}
\{ \text{ S.fName, S.lName } | &\\
& \land \forall A((Staff(A) \land \text{A.position = 'Assistant'} \lor S.salary > A.salary)\}
\end{flalign*}
$$
*domain*
$$
\begin{flalign*}
\{\,  F,L  \mid &
   \forall P',S',D',Sal',B' \big[ Staff(F,L,P,S,D,Sal,B)
   \land Staff(F,L,P,S,D,Sal,B) \big] \land Sal > S' \,\}
\end{flalign*}
$$
