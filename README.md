[Healthcare_Analysis.xlsx](https://github.com/user-attachments/files/33071423/Healthcare_Analysis.xlsx)
# Module-end-assignment
*1.cleaning*
Count ? per column	=COUNTIF(B2:B2336,"~?") 
Month ? → Sep	=IF(C2="?","Sep",C2)
Year ? → average	=IF(B2="?",ROUND(AVERAGE($B$2:$B$2344),0),B2), which gives 1983
Smoker ? → mode	=IF(TRIM(H2)="?","No",PROPER(TRIM(H2)))
Hospital tier / City tier ? → mode	=IF(G2="?","tier - 2",G2) (same for City tier)
State ID ? → Unknown	=IF(I2="?","Unknown",I2)

*2. transformation*
Last name: =LEFT(B2,FIND(",",B2)-1)
Title:
First put =TRIM(MID(B2,FIND(",",B2)+1,60)) in a helper column F.
Then =LEFT(F2,FIND(" ",F2)-1).
First name:
Put =TRIM(MID(F2,FIND(" ",F2)+1,60)) in a helper column G.
Then =IFERROR(LEFT(G2,FIND(" ",G2)-1),G2).
Surgeries to numbers: =IF(G2="No major surgery",0,G2)
Heart Issues / smoker inconsistency: the data mixes "yes" and "No" in different cases. Fix with =PROPER(TRIM(D2)).
Weight Status: =IF(B2<18.5,"Underweight",IF(B2<25,"Normal Weight",IF(B2<30,"Overweight","Obesity")))
Diabetes Status: =IF(C2<5.7,"Normal",IF(C2<6.5,"Prediabetes","Diabetes"))
Date of Birth:
Use =DATE(year,MATCH(month,{"Jan","Feb","Mar","Apr","May","Jun","Jul","Aug","Sep","Oct","Nov","Dec"},0),date).
Format it as dd-mmm-yyyy.
Age: =DATEDIF(DOB,DATE(2023,6,8),"Y")
Charges: format the column as currency ($).

*Healthcare sheet*

(VLOOKUP). Put Customer ID in column A, then use =VLOOKUP($A2,'Medical Examinations'!$A:$O,col,FALSE)

<img width="698" height="526" alt="Screenshot 2026-10-01 234202" src="https://github.com/user-attachments/assets/c6cc3ebf-8957-41ff-801f-7a5248cc9f8c" />
<img width="752" height="646" alt="Screenshot 2026-10-01 234325" src="https://github.com/user-attachments/assets/b761d1ae-96dd-4cc6-b28a-9c83feac40fb" />
