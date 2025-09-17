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
&\text{ } \exists_{\text{ sn, fn, ln, pos, sx, dob, sal, bn, st, ct, pc}} &\\
&(\text{Staff(sn, fn, ln, pos, sx, dob, sal, bn) } \land \text{ Branch(bn, st, ct, pc) } \land \text{ ct = 'London})
\end{flalign*}
$$

## Question 3

*domain*
$$
\begin{flalign*}
\{ \text{fn, ln } | \exists \text{ fn, pos, sx, dob, sal bn} &\\
& (\text{Staff(sn, fn, ln, pos, sx, dob, sal, bn) } \land &\\
& \exists \text{ sn1, pos1, sx1, dpob1, sal1, bn1 (Staff(sn1, 'Julie', 'Lee'} &\\
& \text{pos1, sx1, dob1, sal1, bn1 })


\end{flalign*}
$$

## Question 4

*tuple*

{ S.fName, S.lName | $\land$ $\forall$ A(~(staff(A) $\land$ A.position='Assistant) $\lor$ S.salary > A.salary)}